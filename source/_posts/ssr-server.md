---
title: ssr服务器安装脚本
date: 2019-05-08 08:51:44
tags:
    - ssr
    - ss
    - bbr
    - kcptun
categories:
    - ssr
---

> 使用ssr一键安装脚本搭建ssr服务器

# doubi一键安装脚本

## 安装

1. 下载安装脚本

``` shell
wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh
```

2. 执行安装

```
chmod +x ssr.sh
./ssr.sh
```

## 配置

## 常用命令

## 卸载

```
./ssr.sh uninstall
```

# 秋水一键安装脚本

## 安装

1. 下载安装脚本

``` shell
wget –no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
```

2. 执行安装

```
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh
```

## 配置

## 常用命令

```
# Shadowsocks-libev 版：
/etc/init.d/shadowsocks-libev start
/etc/init.d/shadowsocks-libev stop
/etc/init.d/shadowsocks-libev restart
/etc/init.d/shadowsocks-libev status

# Shadowsocks-Python 版：
/etc/init.d/shadowsocks-python start
/etc/init.d/shadowsocks-python stop
/etc/init.d/shadowsocks-python restart
/etc/init.d/shadowsocks-python status

# ShadowsocksR 版：
/etc/init.d/shadowsocks-r start
/etc/init.d/shadowsocks-r stop
/etc/init.d/shadowsocks-r restart
/etc/init.d/shadowsocks-r status

# Shadowsocks-Go 版：
/etc/init.d/shadowsocks-go start
/etc/init.d/shadowsocks-go stop
/etc/init.d/shadowsocks-go restart
/etc/init.d/shadowsocks-go status
```

## 卸载

```
./shadowsocks-all.sh uninstall
```

# 安装bbr加速

```
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh && chmod +x bbr.sh && bash bbr.sh
```

# 安装kcptun加速器

> 参考[https://ssr.tools/588](https://ssr.tools/588)

```
wget --no-check-certificate https://github.com/kuoruan/shell-scripts/raw/master/kcptun/kcptun.sh
chmod +x ./kcptun.sh
./kcptun.sh
```

# centos关闭防火墙

```
# 查看防火墙状态
firewall-cmd --state

# 关闭防火墙
systemctl stop firewalld.service

# 禁止开机启动
systemctl disable firewalld.service
```

> 参考
    [https://ssr.tools/373](https://ssr.tools/373)
