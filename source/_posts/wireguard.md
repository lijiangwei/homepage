---
title: wireguard安装及配置
date: 2019-06-17 21:55:02
tags:
    - wireguard
    - centos7
    - aws linux2
categories:
    - vpn
---

# centos7一键安装脚本

```
wget https://raw.githubusercontent.com/atrandys/wireguard/master/wireguard_install.sh && chmod +x wireguard_install.sh && ./wireguard_install.sh
```

# aws linux 2 安装wireguard

## 安装

```
sudo curl -Lo /etc/yum.repos.d/wireguard.repo https://copr.fedorainfracloud.org/coprs/jdoss/wireguard/repo/epel-7/jdoss-wireguard-epel-7.repo

sudo amazon-linux-extras install epel

sudo yum install wireguard-dkms wireguard-tools

# 开启ipv4流量转发
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
sysctl -p

# 或者
sysctl -w net.ipv4.ip_forward=1


# 创建并进入WireGuard文件夹
mkdir -p /etc/wireguard && chmod 0777 /etc/wireguard
cd /etc/wireguard

# 生成服务器密钥对
umask 077
wg genkey | tee privatekey | wg pubkey > publickey
```

## 使用命令创建配置文件

```
ip link add dev wg0 type wireguard  # ip link delete dev wg0 type wireguard
ip address add dev wg0 192.168.2.1/24
wg set wg0 private-key ./privatekey
wg setconf wg0 wg0.conf
ip link set wg0 up

# 添加客户端配置
wg set wg0 peer <client-publickey> allowed-ips 192.168.2.2/24

# 查看运行状态
wg

# 查看配置文件
wg showconf
```

## 手动创建配置文件

```
[Interface]
Address = 192.168.2.1/24   #wg0 内网ip地址段 任意的内网地址
SaveConfig = true   # 设为true之后，每次重启服务（stop service时）都会自动保存config

# 以下是重点: 当服务启动时，通过iptables配置wg0来的流量forward到eth0
# 如果你的device不是eth0而是别的名字，把下面的eth0改成别的。
# 当服务停止的时候，删除相关的iptables规则
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE; ip6tables -A FORWARD -i wg0 -j ACCEPT; ip6tables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE; ip6tables -D FORWARD -i wg0 -j ACCEPT; ip6tables -t nat -D POSTROUTING -o eth0 -j MASQUERADE
 
ListenPort = 51820   # 随便选一个空闲的端口
PrivateKey = <server-privateKey>   #在上一步里生成的privatekey的内容

# 客户端1
[Peer]
PublicKey = <client-publicKey>
AllowedIPs = 192.168.2.2/24

# 客户端2
[Peer]
PublicKey = <client-publicKey>
AllowedIPs = 192.168.2.3/24
```

## 客户端配置文件
```
[Interface]
Name = aws
PrivateKey = <client-privateKey>
PublicKey = S4bzrVS8PBvuXxowqOzB5uNGrd4WQY74UJ388Z1XshQ=
Address = 192.168.2.2/24

[Peer]
PublicKey = <server-publicKey>
Endpoint = ip:port  #服务器ip:端口
AllowedIPs = 0.0.0.0/0
```

## 启动/停止

```
cd /etc/wireguard
wg-quick up wg0
wg-quick down wg0

# 设置开机启动
systemctl enable wg-quick@wg0
```

# 客户端配置

## Android客户端配置

* Name: 自己起个名字
* 点击GENERATE，它会自动生成Private/Public Key
* 点击Public key，它会把public key复制到剪贴版，之后要用到。
* Addresses: 填跟服务器端的配置里同样网段的IP，比如说192.168.2.2/24 （虚拟内网ip地址，/24是子网掩码，等于24位1，ip地址不能重复）
* DNS: 8.8.8.8，这个应该是可选的
* 添加一个Peer，在Peer里：
    Public key: 填服务器端生成的public key
    Allowed IPs: 填0.0.0.0/0，允许所有IP（这个很重要，否则即使连上了VPN，也无法访问别的网站）
    Endpoint: 填服务器的IP:端口（端口是服务器监听的端口）

