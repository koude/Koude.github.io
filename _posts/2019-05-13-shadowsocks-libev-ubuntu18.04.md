---
title: Ubuntu 18.04 搭建 shadowsocks-libev
description: 在系统为Ubuntu 18.04的VPS上搭建 shadowsocks-libev
categories:
 - 教程
tags: shadowsocks 科学上网
---

> Shadowsocks不多介绍

<!-- more -->



## 安装shadowsocks-libev
```sh
sudo apt update
sudo apt install shadowsocks-libev
```

## 配置shadowsocks-libev

编辑shadowsocks-libev配置文件, 须注意.json文件不可添加注释
```sh
vim /etc/shadowsocks-libev/config.json
```
```json
{
"server":"0.0.0.0", 
"server_port":443, 
"local_port":1080,
"password":"YourPassword",
"timeout":300,
"method":"aes-256-gcm",
"plugin":"obfs-server",
"plugin_opts":"obfs=http"
}
```

## 安装obfs
```sh
sudo apt-get install --no-install-recommends build-essential autoconf libtool libssl-dev libpcre3-dev libev-dev asciidoc xmlto automake
git clone https://github.com/shadowsocks/simple-obfs.git
cd simple-obfs
git submodule update --init --recursive
./autogen.sh
./configure && make
sudo make install
```

## shadowsocks-libev的启动、停止与重启.
```sh
sudo ss-server -c /etc/shadowsocks-libev/config.json -f .ss.pid
sudo service shadowsocks-libev start
sudo service shadowsocks-libev status
sudo service shadowsocks-libev stop
sudo service shadowsocks-libev restart
```

## 安装bbr

 开机后 `uname -r` 看看是不是内核4.9以上
 切换管理员登陆 `sudo -i`
 执行 `lsmod | grep bbr `，如果结果中没有 `tcp_bbr` 的话就先执行
```sh
modprobe tcp_bbr
echo "tcp_bbr" >> /etc/modules-load.d/modules.conf
```
 执行
```sh
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
```
 保存生效
```sh
sysctl -p
```
 执行
```sh
sysctl net.ipv4.tcp_available_congestion_control
sysctl net.ipv4.tcp_congestion_control
```
 如果结果都有bbr, 则证明你的内核已开启 bbr。
执行`lsmod | grep bbr`, 看到有 `tcp_bbr` 模块即说明 bbr 已启动



