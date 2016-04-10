---
title: ExecuteNonQuery()的返回值
tags:
  - 软件
id: 48
categories:
  - 软件开发
date: 2013-07-29 09:26:18
---

&nbsp; &nbsp; &nbsp; ADO.NET中使用ExecuteNonQuery()方法时，我们常通过看其返回值是否大于0来判断操作是否成功 。ExecuteNonQuery()方法主要用于更新数据，对于Update,Insert,Delete语句执行成功时返回值为该命令所影响的行数，如果影响的行数为0则返回值为0，如果数据操作回滚得话返回值为-1，对于上述操作，用判断返回值是否大于0的方式是可以的。&nbsp;

&nbsp; &nbsp; &nbsp;但这只是在处理一般的修改、插入、删除操作时的做法，对于其他的操作如对数据库结构的操作，在操作成功时的返回值却是-1。例如对数据库添加一个数据表的Create操作，当创建数据表成功时返回-1,如果操作失败的话（如数据表已经存在）往往会发生异常，因此一般需要用try-catch语句来容错。

<pre class="prettyprint linenums bush:csharp" lang="csharp">SqlConnection conn = new SqlConnection("Data Source=.;Initial Catalog=DB;Integrated Security=SSPI");
       &nbsp;</pre>
<pre class="prettyprint linenums bush:csharp" lang="csharp">
   string str = "CREATE TABLE test ( " +
  "[ID] [int] IDENTITY (1, 1) NOT NULL , " +
  "[userName] [varchar] (50) COLLATE Chinese_PRC_CI_AS NULL ," +
  "[userSex] [char] (2) COLLATE Chinese_PRC_CI_AS NULL ," +
  "[userBirthday] [smalldatetime] NULL ," +
") ON [PRIMARY]   ";     

  SqlCommand comm = new SqlCommand(str, conn);
        int i = 10;
        try
        {
            conn.Open();
            i = comm.ExecuteNonQuery();
            conn.Close();
        }
        catch (Exception ex)
        {
            Response.Write(ex.Message);
        }

        Response.Write(i.ToString());</pre>

&nbsp; &nbsp; &nbsp; 执行成功则返回的值为-1,若数据表已经存在则返回异常：数据库中已存在名为 'test' 的对象。