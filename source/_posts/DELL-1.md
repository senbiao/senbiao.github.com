---
title: 戴尔品牌电脑系统问题
tags:
  - 电脑问题
id: 42
categories:
  - 操作系统
date: 2013-06-28 15:05:58
---

<div style="font-family: 'lucida Grande', Verdana; line-height: 23px;">&nbsp; &nbsp; &nbsp; 公司一个同事的电脑开不了机，我过去看了，发现<span style="line-height: 1.5;">一开始提示：ntldr is missing的错误，于是我用PE给它</span><span style="line-height: 1.5;">修复了ntldr和boot.ini，此时开机，新的问题又来了</span><span style="line-height: 1.5;">：hal.dll丢失或损坏。</span></div>
<div style="font-family: 'lucida Grande', Verdana; line-height: 23px;">这时候，我郁闷了，于是通过PE进入C盘系统盘把boot.ini文件再检查一遍，发现其内容为：</div>
<div style="font-family: 'lucida Grande', Verdana; line-height: 23px;">
<div>[boot loader]</div>
<div>timeout=5</div>
<div>default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS</div>
<div>[operating systems]</div>
<div>multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect</div>
<div>C:\GHLDR="一键GHOST v8.3 Build 060428"</div>
</div>
<div style="font-family: 'lucida Grande', Verdana; line-height: 23px;">&nbsp; &nbsp; &nbsp; 原来关键问题就出在这里：<span style="line-height: 1.5;"><span style="line-height: 23px; color: #ff0000;">multi(0)disk(0)rdisk(0)partition(1)\WINDOWS</span></span></div>
<div style="font-family: 'lucida Grande', Verdana; line-height: 23px;">应该改为：<span style="line-height: 1.5; color: #ff0000;">**multi(0)disk(0)rdisk(0)partition(2)\WINDOWS**</span></div>
<div style="font-family: 'lucida Grande', Verdana; line-height: 23px;"><span style="line-height: 1.5;">主要原因是我们公司用的办公电脑统一都是戴尔品牌机，DELL品牌机的硬盘分区比较特殊，它的第一分区是个隐藏分区，而不是C盘，因此，C盘算是第二分区了，所以无法读取到hal.dll文件。</span></div>
<div style="font-family: 'lucida Grande', Verdana; line-height: 23px;"><span style="line-height: 1.5;">也有另外一个方法，就是</span><span style="background-color: #ffffff;"><span style="font-family: Arial, Helvetica, simsun, u5b8bu4f53; line-height: 25px;">重建MBR表，</span><span style="font-family: Arial, Helvetica, simsun, u5b8bu4f53; line-height: 25px;">直接删除第一个没用的隐藏分区</span></span></div>
<div style="font-family: 'lucida Grande', Verdana; line-height: 23px;"><span style="font-family: Arial, Helvetica, simsun, u5b8bu4f53; line-height: 25px;">&nbsp; &nbsp; &nbsp; 至此，问题圆满解决。</span></div>