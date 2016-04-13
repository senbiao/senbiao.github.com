---
title: 初识phalcon——高性能的php框架
id: 8
categories:
  - Phalcon
date: 2013-01-31 23:04:12
tags: PHP
---

<span style="font-size: small;"><span style="font-size: small;"><span style="font-family: 宋体;"><span lang="EN-US">&nbsp;&nbsp;&nbsp;Phalcon是一个开源的，全堆栈的，用C语言写成的php5框架，高性能的php扩展。同时Phalcon是松耦合的，也可以根据需要使用其他组件。</span></span></span></span>

<span style="font-size: small;"><span style="font-size: small;"><span style="font-family: 宋体;"><span lang="EN-US">&nbsp;&nbsp;&nbsp; 说明：由于Phalcon编译在PHP5.3.1上，所有之前的版本无法支持Phalcon，笔者使用的是PHP5.4.3。&nbsp;</span></span></span></span>

<span style="font-size: small;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 18.0pt; mso-bidi-font-family: Arial; mso-border-alt: none windowtext 0cm; border: windowtext 1pt; padding: 0cm;">搭建环境，安装<span lang="EN-US">Phalcon</span></span></span>

<span style="font-size: small;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial; mso-border-alt: none windowtext 0cm; border: windowtext 1pt; padding: 0cm;" lang="EN-US"><span style="mso-tab-count: 1;">&nbsp;&nbsp;&nbsp; </span></span><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial; mso-border-alt: none windowtext 0cm; border: windowtext 1pt; padding: 0cm;">由于笔者现在使用的开发环境是<span lang="EN-US">windows xp</span>，因此暂时只探讨<span lang="EN-US">windows</span>下的安装方式。使用<span lang="EN-US">Phalcon</span>只需要下载一个<span lang="EN-US">Windows</span>的扩展即可，下载地址：<span lang="EN-US">[<span style="color: #800080;">http://phalconphp.com/download</span>](http://phalconphp.com/download)</span>。下载完毕解压后放至<span lang="EN-US">php</span>安装目录下的<span lang="EN-US">\ext</span>文件夹中。</span></span>

<span style="font-size: small;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial; mso-border-alt: none windowtext 0cm; border: windowtext 1pt; padding: 0cm;" lang="EN-US"><span style="mso-tab-count: 1;">&nbsp;&nbsp;&nbsp; </span></span><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial; mso-border-alt: none windowtext 0cm; border: windowtext 1pt; padding: 0cm;">然后编辑<span lang="EN-US">php.ini</span>文件，增加下面一段：</span><a name="OLE_LINK3"></a><a name="OLE_LINK2"></a></span>

<span style="font-size: small;"><span style="mso-bookmark: OLE_LINK2;"><span style="mso-bookmark: OLE_LINK3;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: 宋体;" lang="EN-US"><span style="mso-tab-count: 1;">&nbsp;&nbsp;&nbsp; </span>extension</span></span></span><span style="mso-bookmark: OLE_LINK2;"><span style="mso-bookmark: OLE_LINK3;"><span style="font-family: 宋体; color: #666600; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: 宋体;" lang="EN-US">=</span></span></span><span style="mso-bookmark: OLE_LINK2;"><span style="mso-bookmark: OLE_LINK3;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: 宋体;" lang="EN-US">php_phalcon</span></span></span><span style="mso-bookmark: OLE_LINK2;"><span style="mso-bookmark: OLE_LINK3;"><span style="font-family: 宋体; color: #666600; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: 宋体;" lang="EN-US">.</span></span></span><span style="mso-bookmark: OLE_LINK2;"><span style="mso-bookmark: OLE_LINK3;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: 宋体;" lang="EN-US">dll</span></span></span></span>

<span style="font-size: small;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial;" lang="EN-US"><span style="mso-tab-count: 1;">&nbsp;&nbsp;&nbsp; </span></span><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial;">保存后，重启<span lang="EN-US">Web</span>服务器。</span></span>

<span style="font-size: small;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial;" lang="EN-US"><span style="mso-tab-count: 1;">&nbsp;&nbsp;&nbsp; </span></span><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial;">使用如下代码，检查安装是否正确：</span></span>

<span style="font-size: small;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial;" lang="EN-US"><span style="mso-tab-count: 1;">&nbsp;&nbsp;&nbsp; </span>&lt;?php<span style="mso-spacerun: yes;">&nbsp;&nbsp; </span>print_r(get_loaded_extensions());<span style="mso-spacerun: yes;">&nbsp;&nbsp; </span>?&gt;</span></span>

<span style="font-size: small;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial;" lang="EN-US"><span style="mso-tab-count: 1;">&nbsp;&nbsp;&nbsp; </span></span><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial;">在浏览器的输出内容中查找<span lang="EN-US">phalcon</span>，如果发现该项，则说明<span lang="EN-US">phalcon</span>安装成功：</span></span>

&nbsp;

<span style="font-size: small;"><span style="font-family: 宋体; color: black; mso-bidi-font-size: 10.5pt; mso-font-kerning: 0pt; mso-bidi-font-family: Arial;">建立项目，目录结构如下：</span></span>

&nbsp;

<span style="font-family: 宋体; color: #333333; font-size: small; mso-bidi-font-size: 10.5pt;" lang="EN-US"><span style="mso-tab-count: 1;">&nbsp;&nbsp;&nbsp; </span></span>

<span style="font-size: small;"><span style="font-family: 宋体; color: #333333; mso-bidi-font-size: 10.5pt;" lang="EN-US"><span style="mso-tab-count: 1;">&nbsp;&nbsp;&nbsp; 小结：由于Phalcon已经在上述的安装步骤中被当做一个php模块加载进来了，所以不需再include任何类库到项目中了。这也是Phalcon不同于ZF等其他框架的地方。以增添PHP扩展的方式来安装一个PHP的开发框架，是完全不同于传统的PHP框架的。可对Phalcon源文件进行编译，或选择所使用的操作系统对应的编译好的文件。</span></span></span>

&nbsp;
