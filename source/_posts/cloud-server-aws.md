---
title: aws ec2服务器
date: 2019-06-11 23:16:25
tags: 
    - cloudserver
    - aws
categories:
    - aws
---

# 切换root用户登录

```
# 密钥证书放到了~/.ssh目录
cd ~/.ssh

# 把证书权限修改为400
chmod 400 aws-tokyo.pem

# ssh远程连接
ssh -i aws-tokyo.pem ec2-user@ec2-3-113-37-231.ap-northeast-1.compute.amazonaws.com

# root用户设置密码
sudo passwd root

# 切换到root用户
su root

# 修改 PasswordAuthentication 为 yes 
vim /etc/ssh/sshd_config

# 重启服务器
```
