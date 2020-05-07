---
title: NUC8i5BEH 黑苹果
description: NUC8i5BEH 安装黑苹果过程全记录
categories:
 - 教程
tags: 黑苹果 hackintosh
---

> NUC8i5BEH 安装黑苹果

<!-- more -->

## NUC8i5BEH 黑苹果过程全记录（未完待续）
# 硬件准备

#### 采购硬件如下：

NUC8i5BEH一台[英特尔（Intel）NUC8i5BEH NUC迷你电脑主机 豆子峡谷 准系统不含内存和硬盘](https://item.jd.com/56753694658.html) ，实际成交价格为2408.84元，评价晒单后返50京东e卡

SATA接口固态硬盘 [英睿达(Crucial) 500G SSD固态硬盘 SATA3.0接口 MX500系列](https://item.jd.com/6164595.html)，498.98元

笔记本内存条[金士顿(Kingston) DDR4 2666 16GB(8G×2)套装 笔记本内存条 骇客神条 Impact系列](https://item.jd.com/8179330.html)，568.73元

> NUC8i5BEH 支持内存频率最高2400，购买2666的原因是它的价格与2400一样，可自动降频到2400。



白苹果拆机无线网卡，BCM943602CS，闲鱼淘来，180元。

NVME转白苹果网卡转接卡，淘宝购买，46.56元。

> NUC8不直接支持白苹果网卡接口，需使用上述转接卡，会占用NUC唯一的nvme接口，因此无法使用nvme固态硬盘。网上已有读卡器接口硬改网卡服务，鉴于会失去保修，不予考虑。

#### 已有硬件如下：

16GB U盘一个，速度越快越好；

MacOS系统电脑一台，黑白都行。

#### 硬件安装：

1. 后背螺丝拧开，取下后盖，注意后盖与主机之间有SATA线、电源线连接；
2. 断开自带网卡天线接头，拧下主板上两颗螺丝，从后背USB接口处开始取下主板，调整黑色天线走向，以免长度不够，然后装回主板；
3. 白苹果网卡固定到转接卡上，转接卡固定到nvme接口上，USB供电线接在主板供电口合适位置。黑白色两条天线接到网卡中间和一侧的两处接口上。（后续采购过第三条天线，但贴片位置不好安装，作罢）；
4. 插内存条；
5. 插硬盘，接好线；
6. 后盖螺丝拧好。



# 软件准备

1. intel官网下载最新版本BIOS，按照说明更新NUC的BIOS，并进入BIOS按照以下说明进行相关设置。

   > 1、为了避免之前有其他不合适的改动，建议先按 F9 重置 BIOS 默认设置。
   > 2、Boot->Boot Priority->Legacy Boot Priority-> « Legacy Boot » ：禁用
   > 3、Boot->Boot Configuration->
   >   UEFI Boot->« Fast Boot »： 禁用
   >   UEFI Boot->« Boot USB Devices First » ： 启用
   >   UEFI Boot->« Boot Network Devices Last » ：启用
   >   Boot Devices->«Network Boot» ：设置为 « Disable »
   > 4、Boot->Secure Boot-> « Secure Boot » ：禁用
   > 5、Security->Security Features-> « Inter VT for directed I/VO (VT-d) » ： 禁用
   > 6、Power->Secondary Power Settings-> « Wake on LAN from S4/S5 » ： 设置为 « Stay Off »
   > 以下为使用白果拆机卡的用户设置：
   > 7、Devices->Onboard Devices-> « WLAN » 和  « Bluetooth » ：禁用
   >
   > 
   >
   > 作者：weachy
   > 链接：https://www.jianshu.com/p/78510cfa4a64
   > 来源：简书
   > 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

2. 采用OpenCore引导，EFI文件采用 [weachy维护的的EFI-OC-200416.zip](https://github.com/Koude/NUC8BEH-Hackintosh)(链接非官方)。
3. MacOS系统App Store下载 Install macOS Catalina.app
4. 格式化U盘



# 开始安装

重启

# 调试完善

修改三码