---
title: 华硕/梅林路由器修改本地Hosts设置DNS
description: 华硕/梅林路由器修改本地Hosts设置DNS，达到接入路由器的设备自动将某域名解析到自定义IP之目的。
categories:
 - 教程
tags: 路由器 hosts DNS
comments: true
---


# 路由器设置
进入系统管理 - 系统设置 - SSH 连接，启用SSH连接。

# 设置hosts
SSH连接路由器 ```ssh admin@192.168.50.1```
进入目录 `cd /jffs`
新建文件 `dnsmasq.conf.add` 并写入内容
```
addn-hosts=/jffs/configs/hosts
```
编辑文件`vi /jffs/configs/hosts`
写入内容
```192.168.0.1 www.example.com
```

# 重启 DNS 服务
```service restart_dnsmasq```
