---
title: Ubuntu 18.04 搭建Shadowsocks-libev
description: Ubuntu 18.04 搭建Shadowsocks-libev
categories:
 - 教程
tags: BreakWall
---

> Ubuntu 18.04 搭建Shadowsocks-libev

<!-- more -->

# Ubuntu 18.04 搭建Shadowsocks-libev
1. 搭建vps 操作系统ubuntu 18.04

``` shell
sudo apt update
sudo apt install shadowsocks-libev
```

2. 编辑shadowsocks-libev配置文件 sudo vim /etc/shadowsocks-libev/config.json

``` shell
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

3. 安装obfs

```shell
sudo apt-get install --no-install-recommends build-essential autoconf libtool libssl-dev libpcre3-dev libev-dev asciidoc xmlto automake
git clone https://github.com/shadowsocks/simple-obfs.git
cd simple-obfs
git submodule update --init --recursive
./autogen.sh
./configure && make
sudo make install
```

4. Shadowsocks-libev的启动、停止与重启

``` shell
sudo ss-server -c /etc/shadowsocks-libev/config.json -f .ss.pid
sudo service shadowsocks-libev start
sudo service shadowsocks-libev stop
sudo service shadowsocks-libev restart
```

5. 安装bbr

   5.1 开机后  ` uname -r`  看看是不是内核4.9以上

   5.2 切换管理员登陆  ` sudo -i` 

   5.3 执行 ` lsmod | grep bbr` ，如果结果中没有 ` tcp_bbr`  的话就先执行

   ```shell
   modprobe tcp_bbr
   echo "tcp_bbr" >> /etc/modules-load.d/modules.conf
   ```

   5.4 执行

   ``` shell
   echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
   echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
   ```

   5.5 保存生效

   `sysctl -p` 

    5.6 执行

   ``` shell
   sysctl net.ipv4.tcp_available_congestion_control
   sysctl net.ipv4.tcp_congestion_control
   ```

   5.7 如果结果都有bbr, 则证明你的内核已开启 bbr。

   执行` lsmod | grep bbr`, 看到有 `tcp_bbr`  模块即说明 bbr 已启动