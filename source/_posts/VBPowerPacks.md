---
title: 未定义类型Microsoft.VisualBasic.PowerPacks
tags:
  - vb.net
id: 59
categories:
  - 软件开发
date: 2013-10-17 14:16:30
---

本文背景：

一个vb6改造成vb.net的winform项目，打开项目时部分窗体无法显示，主要提示以下两个错误：命名空间"Microsoft.VisualBasic.PowerPacks"中不存在类型或命名空间名称"LineShape"(是缺少程序集引用吗？)

命名空间"Microsoft.VisualBasic.PowerPacks"中不存在类型或命名空间名称"ShapeContainer"(是缺少程序集引用吗？)

小结一下问题： **未定义类型 Microsoft.VisualBasic.PowerPacks.ShapeContainer&nbsp;**

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; **未定义类型 Microsoft.VisualBasic.PowerPacks.LineShape**

尝试解决：

在程序中添加了Microsof.VisualBasic，提示该引用已默认添加了。

添加Microsoft.VisualBasic.PowerPacks.vs后发现问题依旧。

最终解决：

到官网http://msdn.microsoft.com/en-us/vbasic/bb735936.aspx下载了Microsoft.VisualBasic.PowerPacks最新版安装，然后在项目中添加Microsoft.VisualBasic.PowerPacks的引用。然后发现窗体显示正常了，问题圆满解决了。