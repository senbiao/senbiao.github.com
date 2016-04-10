---
title: 大话ADO.NET操作流程
tags:
  - .NET
id: 44
categories:
  - 软件开发
date: 2013-07-24 19:29:29
---

<span lang="EN-US">ADO.NET</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">的数据库操作流程如下：</span>

<span lang="EN-US">1</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">、建立数据库连接，包含连接对象（</span><span lang="EN-US">sqlconnection</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">）、连接字符串、打开连接三个步骤。</span>

<span lang="EN-US">2</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">、执行命令，包含命令对象（</span><span lang="EN-US">sqlcommand</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">）、</span><span lang="EN-US">sql</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">语句、打开的连接对象</span>

<span lang="EN-US">3</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">、返回结果，包含两种情况，一是返回</span><span lang="EN-US">SqlDataReader</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">对象，一是返回</span><span lang="EN-US">DataSet</span><span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">对象</span>

<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">抽水的流程大致如下：</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">1、<span style="font-size: 7pt; font-family: 'Times New Roman';">  </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">确定水龙头的连接方向</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">2、<span style="font-size: 7pt; font-family: 'Times New Roman';">  </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">接水龙头</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">3、<span style="font-size: 7pt; font-family: 'Times New Roman';">  </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">发动抽水机</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">4、<span style="font-size: 7pt; font-family: 'Times New Roman';">  </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">接水管</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">5、<span style="font-size: 7pt; font-family: 'Times New Roman';">  </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">准备水池来存放水</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">6、<span style="font-size: 7pt; font-family: 'Times New Roman';">  </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">把水管中的水输到水池中</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">7、<span style="font-size: 7pt; font-family: 'Times New Roman';">  </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">抽完水，关水龙头</span>

&lt;!--[if !supportLists]--&gt;<span lang="EN-US">8、<span style="font-size: 7pt; font-family: 'Times New Roman';">  </span></span>&lt;!--[endif]--&gt;<span style="font-family: 宋体; mso-ascii-font-family: 'Times New Roman'; mso-hansi-font-family: 'Times New Roman';">停止抽水机</span>

<span style="text-indent: -18pt;" lang="EN-US">9、<span style="font-size: 7pt; font-family: 'Times New Roman';">  </span></span><span style="text-indent: -18pt; font-family: 宋体;">拆水管</span>

<span style="font-size: 10.5pt; line-height: 125%;">下面用对比的方法来形象地理解每个对象的作用</span>

<span style="font-size: 10.5pt; line-height: 125%;">
</span>

<span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">1</span><span style="font-size: 10.5pt; line-height: 125%;">、数据库好比水源，存储了大量的数据。</span>

<span style="font-size: 10.5pt; line-height: 125%;">
</span>

<span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">2</span><span style="font-size: 10.5pt; line-height: 125%;">、</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">Connection</span><span style="font-size: 10.5pt; line-height: 125%;">好比伸入水中的进水笼头，保持与水的接触，只有它与水进行了</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">“</span><span style="font-size: 10.5pt; line-height: 125%;">连接</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">”</span><span style="font-size: 10.5pt; line-height: 125%;">，其他对象才可以抽到水。</span>

<span style="font-size: 10.5pt; line-height: 125%;">
</span>

<span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">3</span><span style="font-size: 10.5pt; line-height: 125%;">、</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">Command</span><span style="font-size: 10.5pt; line-height: 125%;">则像抽水机，为抽水提供动力和执行方法，通过</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">“</span><span style="font-size: 10.5pt; line-height: 125%;">水龙头</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">”</span><span style="font-size: 10.5pt; line-height: 125%;">，然后把水返给上面的</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">“</span><span style="font-size: 10.5pt; line-height: 125%;">水管</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">”</span><span style="font-size: 10.5pt; line-height: 125%;">。</span>

<span style="font-size: 10.5pt; line-height: 125%;">
</span>

<span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">4</span><span style="font-size: 10.5pt; line-height: 125%;">、</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">DataAdapter</span><span style="font-size: 10.5pt; line-height: 125%;">、</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">DataReader</span><span style="font-size: 10.5pt; line-height: 125%;">就像输水管，担任着水的传输任务，并起着桥梁的作用。二者是有不同的，后面章节中将详细介绍。</span>

<span style="font-size: 10.5pt; line-height: 125%;">
</span>

<span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">5</span><span style="font-size: 10.5pt; line-height: 125%;">、</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">DataSet</span><span style="font-size: 10.5pt; line-height: 125%;">则是一个大水库，把抽上来的水按一定关系的池子进行存放。即使撤掉</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">“</span><span style="font-size: 10.5pt; line-height: 125%;">抽水装置</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">”</span><span style="font-size: 10.5pt; line-height: 125%;">（断开连接，离线状态），也可以保持</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">“</span><span style="font-size: 10.5pt; line-height: 125%;">水</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">”</span><span style="font-size: 10.5pt; line-height: 125%;">的存在。这也正是</span><span style="font-size: 10.5pt; line-height: 125%; font-family: Simsun;" lang="EN-US">ADO.NET</span><span style="font-size: 10.5pt; line-height: 125%;">的核心。</span>

<span style="font-size: 10.5pt; line-height: 125%;">
</span>

<span style="line-height: 125%; text-indent: -18pt; font-family: Simsun;" lang="EN-US">6</span><span style="line-height: 125%; text-indent: -18pt; font-family: 宋体;">、</span><span style="line-height: 125%; text-indent: -18pt; font-family: Simsun;" lang="EN-US">DataTable</span><span style="line-height: 125%; text-indent: -18pt; font-family: 宋体;">则像水库中的每个独立的水池子，分别存放不同种类的水。一个大水库由一个或多个这样的水池子组成。</span>

 ![](http://i2.tietuku.com/e5e476fe56d1cb0e.jpg)

<span style="line-height: 125%; text-indent: -18pt; font-family: 宋体;">[](http://zhousenbiao.com/index.php/attachment/46/ "2012179090.jpg")</span>

<span style="line-height: 125%; text-indent: -18pt; font-family: 宋体;">
</span>

![](file:///C:/Documents%20and%20Settings/eec/桌面/clip_image001.jpg)

<span style="font-family: 宋体; font-size: 10.5pt; line-height: 125%; text-indent: -18pt;">编码实现如下：</span>

<pre class="prettyprint linenums bush:csharp" lang="csharp">//数据库连接字符串  --确定水龙头连接的方向
string strCon = "Data source=.;Initial Catalog=db;User ID=abc;Password= ";
string strSql = "select UserCode,UserName,DivisionCode from UserMas";
//定义连接对象      --接水龙头
SqlConnection conn = new SqlConnection(strCon );
//打开连接对象      --开水龙头
conn.Open();
//实例化SqlCommand对象来执行sql语句           --发动抽水机
SqlCommand comm = new SqlCommand(strSql,conn);
//实例化SqlDataAdapter对象来把数据源引到myDa  --接水管
SqlDataAdapter myDa = new SqlDataAdapter(comm);
//实例化DataSet来存放数据源                   --准备水池来储水
DataSet Ds = new DataSet();
//用myDa填充Ds     --把水管的水存到水池
myDa.Fill(Ds);
//关闭连接对象     --抽完水，关水龙头
conn.Close();
//关闭comm对象     --停止抽水机
comm.Dispose();
//关闭Da对象       --拆水管
myDa.Dispose();</pre>

<span style="font-family: 宋体; font-size: 10.5pt; line-height: 125%; text-indent: -18pt;">
</span>