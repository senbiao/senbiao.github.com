---
title: 装饰模式，我的肤浅理解
tags:
  - 设计模式
id: 53
categories:
  - 设计模式
date: 2013-08-06 18:52:54
---

<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">&nbsp; &nbsp; &nbsp; 所谓装饰，就是一些对象给主体对象做陪衬。这是我的理解。好比说我的办公桌，需要电脑、电话、文件夹、盆栽等作为装饰。那么，办公桌就是一个主体对象，电脑、电话等装饰品就是那些做陪衬的对象。这些办公用品准备好了，该怎么摆放到办公桌上呢？可以有多种方案。而且，我可以随时往办公桌上增加一支签字笔，增加一枚公章等等。</span>

<span lang="EN-US">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">目前，可归纳如下：</span>

<span lang="EN-US">&nbsp; &nbsp; &nbsp; A</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">主体对象：办公桌</span>

<span lang="EN-US">&nbsp; &nbsp; &nbsp; B</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">装饰者：电脑、电话、文件夹、盆栽、签字笔、公章</span>

<span lang="EN-US">&nbsp; &nbsp; &nbsp; C</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">装饰者可以装饰主体对象，即</span><span lang="EN-US">B</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">可以装饰</span><span lang="EN-US">A</span>

<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">什么是装饰模式？一个标准的定义是：动态地将责任附加到对象上。若要扩展功能，装饰者提供了比基础更有弹性的替代方案。</span>

&nbsp;

<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">根据我的理解，装饰模式可以这样定义：能够动态地为对象添加功能，同时不会对类进行修改。</span>

<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">[![201308062.jpg](http://zhousenbiao.com/wp-content/uploads/2013/08/4181935157.jpg)](http://zhousenbiao.com/attachment/54/ "201308062.jpg")
</span>

<span style="font-size: 10.5pt;">&nbsp; &nbsp; &nbsp; 对于上面的</span><span style="font-size: 10.5pt; font-family: 'Times New Roman', serif;" lang="EN-US">UML</span><span style="font-size: 10.5pt;">类图，我们可以发现装饰模式的两个要点：</span>

<span style="font-size: 10.5pt; font-family: Verdana, sans-serif;" lang="EN-US">&nbsp; &nbsp; &nbsp; 1.</span><span style="font-size: 10.5pt;">装饰者（办公用品）需要知道装饰对象（桌子）。（</span><span style="font-size: 10.5pt; font-family: 'Times New Roman', serif;" lang="EN-US">UML</span><span style="font-size: 10.5pt;">类图的聚合关系）</span>

<span style="font-size: 10.5pt; font-family: Verdana, sans-serif;" lang="EN-US">&nbsp; &nbsp; &nbsp; 2.</span><span style="font-size: 10.5pt;">装饰对象（办公桌）需要把一系列装饰行为交给装饰者（办公用品），让装饰者帮忙装饰，因此用到了继承。</span><span style="text-indent: 21pt;">&nbsp;</span>

<span style="font-size: 10.5pt; font-family: Verdana, sans-serif;" lang="EN-US">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="font-size: 10.5pt;">在办公桌的装饰过程中，办公桌的装饰交给另一个对象来处理，办公桌不需要去管装饰这个过程。也就是把自身的一些行为交给别人来完成，而且这样有个明显的好处就是，这些处理顺序可以改变。可以先摆好电脑，再装上电话，也可以先装个电话在摆好电脑，它们的顺序可以变换。下面是装饰模式的简单的编码实现：</span>

using System;

using System.Collections.Generic;

<div>
<div>using System.Linq;</div>
<div>using System.Text;</div>
<div>namespace DecorateTest</div>
<div>{</div>
<div>//桌子</div>
<div>public abstract class Desk</div>
<div>{</div>
<div>public abstract void Decorate();</div>
<div>}</div>
<div>//办公桌</div>
<div>public class officeDesk : Desk</div>
<div>{</div>
<div>public override void Decorate()</div>
<div>{</div>
<div>Console.WriteLine("办公桌已经交给Decoretor来装饰了");</div>
<div>}</div>
<div>}</div>
<div>//装饰者</div>
<div>public class Decorator : Desk</div>
<div>{</div>
<div>private Desk desk;</div>
<div>//需要知道装饰对象，对应UML中的聚合</div>
<div>public void setDecorate(Desk desk)</div>
<div>{</div>
<div>this.desk = desk;</div>
<div>}</div>
<div>//装饰对象把装饰这个行为交给我来处理了</div>
<div>public override void Decorate()</div>
<div>{</div>
<div>if (desk != null)</div>
<div>{</div>
<div>desk.Decorate();</div>
<div>}</div>
<div>}</div>
<div>}</div>
<div>//电脑</div>
<div>public class Computer : Decorator</div>
<div>{</div>
<div>public override void Decorate()</div>
<div>{</div>
<div>base.Decorate();</div>
<div>Console.WriteLine("电脑已经装饰摆放好了");</div>
<div>}</div>
<div>}</div>
<div>//电话</div>
<div>public class Telephone : Decorator</div>
<div>{</div>
<div>public override void Decorate()</div>
<div>{</div>
<div>base.Decorate();</div>
<div>Console.WriteLine("电话已经摆放好了");</div>
<div>}</div>
<div>}</div>
<div>//公章</div>
<div>public class Seal : Decorator</div>
<div>{</div>
<div>public override void Decorate()</div>
<div>{</div>
<div>base.Decorate();</div>
<div>Console.WriteLine("公章已经放好了");</div>
<div>}</div>
<div>}</div>
<div>class Program</div>
<div>{</div>
<div>static void Main(string[] args)</div>
<div>{</div>
<div>//对办公桌进行装饰</div>
<div>officeDesk office = new officeDesk();</div>
<div>Computer computer = new Computer();</div>
<div>Telephone telephone = new Telephone();</div>
<div>Seal seal = new Seal();</div>
<div>//装饰顺序：电脑、电话、公章</div>
<div>computer.setDecorate(office);</div>
<div>telephone.setDecorate(computer);</div>
<div>seal.setDecorate(telephone );</div>
<div>seal.Decorate();</div>
<div>Console.ReadLine();</div>
<div>}</div>
<div>}</div>
<div>}</div>
</div>