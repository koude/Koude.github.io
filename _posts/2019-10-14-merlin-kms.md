---
title: 梅林路由器安装KMS激活Windows Office
description: 在梅林koolshare版路由器固件上安装KMS激活工具，并激活Windows与Office
categories:
 - 教程
tags: Windows Office KMS
comments: true
---

> 在梅林koolshare版路由器固件上安装KMS激活工具，并激活Windows与Office

# 安装KMS工具
进入路由器管理页面，最下方最后选项 软件中心-未安装-系统工具-安装，安装完毕后开启系统工具

# 激活Windows
```
slmgr /ipk MHF9N-XY6XB-WVXMC-BTDCT-MKKG7
slmgr /skms 192.168.50.1
slmgr /ato
```

# 激活Office
```
cd "C:\Program Files\Microsoft Office\Office16"
cscript ospp.vbs /inpkey:XQNVK-8JYDB-WJ9W3-YJ8YR-WFG99   ;（安装Office Professional 2016 vl版密钥）
cscript ospp.vbs /sethst:192.168.50.1
cscript ospp.vbs /act
```