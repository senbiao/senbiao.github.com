---
title: The requested URL /…/… was not found on this server的解决方法
id: 12
categories:
  - Phalcon
date: 2013-02-02 16:04:52
tags:
---

&nbsp; &nbsp; &nbsp; 笔者在研究Phalcon官网教程提供的[Demo](http://docs.phalconphp.com/en/latest/reference/tutorial.html)时，按部就班一步步来做了，结果就卡在这个问题上了。将教程再从头细看，并且google+baidu伺候，广泛寻求解答，依然不得其解。后来一个同事提醒我去看下.htaccess文件是否有问题，是否缺少mod_rewrite.c这个文件？

&nbsp; &nbsp; &nbsp; 最后发现，其实就是Apache下伪静态html(URL Rewrite)模块未开启。仅需两步这个问题即迎刃而解了：
1.打开 Apache 的配置文件 httpd.conf 。
2.将#LoadModule rewrite_module modules/mod_rewrite.so前面的#去掉
&nbsp; &nbsp; &nbsp; 补充：关于rewrite模块的调用；
Apache 2.x 中URL重写，是通过mod_rewrite.so 来实现的，因此需要查看Apache 是否已经被编译
进去这个模块了，并且在Apache的配置文件httpd.conf 中已经调用了这个模块。笔者所用的Apache 
2.2.22 ，rewrite模块已经编译进去了，剩下的工作只需修改apache2.2.22\conf目录下的配置文件 
httpd.conf即可。