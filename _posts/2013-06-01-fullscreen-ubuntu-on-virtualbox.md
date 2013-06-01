---
layout: post
title: "Fullscreen Ubuntu on VirtualBox"
description: ""
category: Ubuntu
tags: [Ubuntu, 经验, 设置]
---
{% include JB/setup %}
我的VirtualBox版本是4.1.12。
###Step1：
在VirtualBox的菜单下找到<b>Devices</b>标签，选<b>Install Guest Additions</b>或者使用快捷键：Host+D。会有一个光盘的icon跳出来(VBOXADDITIONS_版本号)。  

###Step2：
打开找到<b>autorun.sh</b>,双击后选“run in terminal”。一般来说这之后Guest Addition就会被安装上了。重启Ubuntu，Host+F，就可以全屏了。  

但通常我总是没有这么顺利的，在autorun运行中出现了：  
```
“build the main guest additions module failed！  
(Look at /var/log/vboxadd-install.log to find out what went wrong) ”
```  
在log文件里面我找到了E: Couldn't find package kernel-header-3.2.0-40  

###Step3：
按照搜到的解决方案，打开Terminal，输入：  
sudo apt-get install build-essential kernel-headers-`uname -r` dkms  
按网上说的，本应该这样就解决问题了，但是没有。。。我得到了类似这样的：  
```
unable to locate package kernel-headers-3.2.0-40-generic
```
###Step4:
输入：  
```
sudo apt-get install linux-headers-$(uname -r)
```  
再重做一遍Step1，应该就可以了，呼～
