---
title: 删除盘符根目录下的msdia80.dll文件
description: 在Windows系统，D/E等盘符下出现msdia80.dll文件，如何处理？
categories:
 - 教程
tags: windows
---

> 在Windows系统，D/E等盘符下出现msdia80.dll文件，如何处理？

<!-- more -->



## 出现原因
计算机上安装 Microsoft Visual C++ 2005 可再发行组件时，msdia80.dll文件被错误安装在其他驱动器的根目录下，正确路径应为`"C:\Program Files\Common Files\Microsoft Shared\VC\msdia80.dll" `

## 如何处理
把msdia80.dll复制到`C:\Program Files\Common Files\Microsoft Shared\VC\` 内；
管理员运行命令提示符，执行`regsvr32 "C:\Program Files\Common Files\Microsoft Shared\VC\msdia80.dll"`

出现以下提示表示OK
![](/images/msdia80.dll.png)



