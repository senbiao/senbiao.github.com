---
title: 温故而知新之java代码片段
tags:
  - java
id: 174
categories:
  - software
date: 2015-02-05 05:11:08
---

1.检测Java代码的执行时间
long startTime=System.currentTimeMillis();

//获取开始时间，单位是毫秒ms。若需取纳秒ns，则System.nanoTime();  doSomeThing();

//需要检测的代码段

long endTime=System.currentTimeMillis();

//获取结束时间

System.out.println("运行时间： "+(endTime-startTime)+"ms");

2.数组打印出来
// List&lt;String&gt;类型的列表

List&lt;String&gt; list = new ArrayList&lt;String&gt;();

list.add("First");  list.add("Second");

System.out.println(list);
//Array类输出数组

String[] array = new String[] { "First", "Second" };  System.out.println(Arrays.toString(array));
//使用Arrays.deepToString()输出数组的数组

String[] arr1 = new String[] { "One", "Two" };

String[] arr2 = new String[] { "Three", "Four" };

String[][] arrayOfArray = new String[][] { arr1, arr2 };

//输出

System.out.println(arrayOfArray);

System.out.println(Arrays.toString(arrayOfArray));

System.out.println(Arrays.deepToString(arrayOfArray));
