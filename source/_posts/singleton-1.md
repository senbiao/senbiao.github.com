---
title: 单例模式学习笔记
tags:
  - C++
  - 设计模式
id: 51
categories:
  - 设计模式
  - 软件开发
date: 2013-07-31 11:37:05
---

<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">单例模式的一个官方定义：确保一个类只有一个实例</span><span lang="EN-US">,</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">并提供一个全局访问点。</span>

<span style="font-size: 10.5pt; mso-bidi-font-size: 12.0pt; font-family: 'Times New Roman'; mso-fareast-font-family: 宋体; mso-font-kerning: 1.0pt; mso-ansi-language: EN-US; mso-fareast-language: ZH-CN; mso-bidi-language: AR-SA;" lang="EN-US">[](http://zhousenbiao.com/index.php/attachment/50/ "singleton.JPG")</span>

![](http://i2.tietuku.com/8b7a31cbcf59c55d.jpg) 

<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">根据单例模式的概念和上面的类图，总结了单例模式的以下三个要点：</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">1.<span style="font-size: 7pt;">       </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">定义私有的构造函数。一旦定义了私有的构造函数，在外界就不能通过</span><span lang="EN-US">new</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">来创建它的实例了。因此能确保一个类只有一个实例。</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">2.<span style="font-size: 7pt;">       </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">要创建实例，就要有一个变量来保存该实例。因此需要定义静态私有变量来记录该类的唯一实例。</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">3.<span style="font-size: 7pt;">       </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">定义一个公有方法或者属性来把该类的实例公开出去。也就是需要提供类的全局访问点。</span>

<span style="font-size: 10.5pt; mso-bidi-font-size: 12.0pt; font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman'; mso-bidi-font-family: 'Times New Roman'; mso-font-kerning: 1.0pt; mso-ansi-language: EN-US; mso-fareast-language: ZH-CN; mso-bidi-language: AR-SA;">    若考虑线程并发问题，当出现两个或更多的线程同时获取</span><span style="font-size: 10.5pt;" lang="EN-US">instance</span><span style="font-size: 10.5pt; mso-bidi-font-size: 12.0pt; font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman'; mso-bidi-font-family: 'Times New Roman'; mso-font-kerning: 1.0pt; mso-ansi-language: EN-US; mso-fareast-language: ZH-CN; mso-bidi-language: AR-SA;">实例，而且是</span><span style="font-size: 10.5pt;" lang="EN-US">null</span><span style="font-size: 10.5pt; mso-bidi-font-size: 12.0pt; font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman'; mso-bidi-font-family: 'Times New Roman'; mso-font-kerning: 1.0pt; mso-ansi-language: EN-US; mso-fareast-language: ZH-CN; mso-bidi-language: AR-SA;">的时候，那样就是多个线程分别创建了</span><span style="font-size: 10.5pt;" lang="EN-US">instance</span><span style="font-size: 10.5pt; mso-bidi-font-size: 12.0pt; font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman'; mso-bidi-font-family: 'Times New Roman'; mso-font-kerning: 1.0pt; mso-ansi-language: EN-US; mso-fareast-language: ZH-CN; mso-bidi-language: AR-SA;">，这是违反单例模式的规则的。因此，考虑了多线程后，代码如下：</span>

<pre class="prettyprint linenums bush:csharp" lang="csharp">public class Singleton
{
       private static Singleton instance;
       private static object _lock=new object();

       private Singleton()
       {

       }

       public static Singleton GetInstance()
       {
               if(instance==null)
               {
                      lock(_lock)
                      {
                             if(instance==null)
                             {
                                     instance=new Singleton();
                             }
                      }
               }
               return instance;
       }
}</pre>

<span style="font-size: 10.5pt; mso-bidi-font-size: 12.0pt; font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman'; mso-bidi-font-family: 'Times New Roman'; mso-font-kerning: 1.0pt; mso-ansi-language: EN-US; mso-fareast-language: ZH-CN; mso-bidi-language: AR-SA;">
</span>

<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">程序中采用了“双重锁”方式，有效地解决了单例模式在多线程下的问题。程序用了内外两层</span><span lang="EN-US">if</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">语句：内层</span><span lang="EN-US">if</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">语句块的加锁操作保证了只有一个线程可以访问该语句块，即只创建一个实例。外层</span><span lang="EN-US">if</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">语句块先判断</span><span lang="EN-US">instance</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">实例是否为空，这样每个线程不用每次都加锁，只有实例为空才加锁并创建实例。如果已经存在</span><span lang="EN-US">instance</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">实例，就直接返回该实例，提高了程序的性能。</span>

<span style="font-size: 10.5pt; mso-bidi-font-size: 12.0pt; font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman'; mso-bidi-font-family: 'Times New Roman'; mso-font-kerning: 1.0pt; mso-ansi-language: EN-US; mso-fareast-language: ZH-CN; mso-bidi-language: AR-SA;">
</span>

<span style="font-size: 10.5pt; mso-bidi-font-size: 12.0pt; font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman'; mso-bidi-font-family: 'Times New Roman'; mso-font-kerning: 1.0pt; mso-ansi-language: EN-US; mso-fareast-language: ZH-CN; mso-bidi-language: AR-SA;">
</span>

 