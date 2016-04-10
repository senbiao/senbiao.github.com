---
title: java笔记——IO操作小结
id: 166
categories:
  - JAVA开发
  - 软件开发
date: 2015-09-20 07:52:42
tags:
---

1.FileWriter与BufferedWriter的区别

1.  FileWriter fw = new FileWriter(file);
2.  BufferedWriter bw = new BufferedWriter (fw);
3.  fw.write("你好");
4.  fw.close();
5.  fw.close();
这里有一个 "修饰类 "的概念
FileWriter   是被修饰者
BufferedWriter   是修饰者
一般用法为
BufferedWriter   bw   =   new   BufferedWriter(new   FileWriter( "filename "));
上面这个加了一个缓冲,缓冲写满后在将数据写入硬盘
这样做极大的提高了性能

如果单独使用   FileWriter  也可以,你每写一个数据,硬盘就有一个写动作,性能极差

相同点：都是使用字符流写文件。
不同点：前者采用缓冲区，可以预读一些准备写入的数据，增加写入文件时的效率，
而后者则没有这个功能。具体的在BufferedWriter的API DOC中有说明。

2.写入txt文件出现乱码

windows自身采用的编码格式是gbk(而gbk和gb2312基本上是一样的编码方式),而IDE中Encode不修改的话，默认是utf-8的编码，这就是为什么会出现乱码的原因。当在OS下手工创建并写入的txt文件（gbk），用程序直接去读（utf-8），就会乱码。为了避免可能的中文乱码问题，最好在文件写入和读出的时候显式指定编码格式。

private static void readTxt() {
try {
File f1 = new File("e:/qqgroup.txt");// 打开文件
FileInputStream in = new FileInputStream(f1);
// 指定读取文件时以UTF-8的格式读取
BufferedReader br = new BufferedReader(new InputStreamReader(in,
"UTF-8")); // 读取文件
String name = "";
String numb = "";
String str;

System.out.println("群名*************群号");
while ((str = br.readLine()) != null) {
if (str.indexOf("class=\"addrtitle\"&gt;")&gt;-1) {
name = str.substring(str.indexOf("&gt;"), str.indexOf("&lt;/"));
System.out.println("群名：" + name);
}
if (str.indexOf("gid=")&gt;-1) {
numb = str.substring(str.indexOf("gid="), str.indexOf("@groupmail"));
System.out.println("群号：" + numb);
}
}
in.close();// 关闭读取
} catch (Exception e1) {// 如果有错误，这里进行处理
e1.printStackTrace();// 打印错误信息
}
}

（1）写入乱码

File f = new File(filePathAndName);

OutputStreamWriter   w = new OutputStreamWriter(new FileOutputStream(f),"UTF-8"); 		   BufferedWriter   writer=new BufferedWriter(w);

writer.write("file content");

writer.flush();

writer.close();

（2）读取txt文件

File f = new File("PathAndName");

if(f.isFile()&amp;&amp;f.exists()){

InputStreamReader read = new InputStreamReader(new FileInputStream(f),"UTF-8"); 		    BufferedReader reader=new BufferedReader(read);

String line;

while ((line = reader.readLine()) != null) {

"file content" += line;

}

read.close();

}

`File file = ``new` `File(``"d:/1.txt"``);`

`BufferedWriter bw = ``new` `BufferedWriter(``new` `FileWriter(file));`
<div>` `</div>
<div>` ``bw.write(``"abc"``);`</div>
<div>` ``bw.newLine();`</div>
<div>` ``bw.write(``"efg"``);`</div>
<div>` `</div>
<div>` ``bw.flush();`</div>
<div>` ``bw.close();`</div>
3.字符流的写入写出

` ``File file=``new` `File(``"F:\\io\\abc.txt"``);`
<div>` ``FileOutputStream fos=``new` `FileOutputStream(file);`</div>
<div>` ``OutputStreamWriter osw=``new` `OutputStreamWriter(fos);`</div>
<div>` ``osw.write(``'大'``);`</div>
<div>` ``osw.close();`</div>
<div>` ``FileInputStream fis=``new` `FileInputStream(file);`</div>
<div>` ``InputStreamReader isr=``new` `InputStreamReader(fis);`</div>
<div>` ``System.out.println((``char``)isr.read());`</div>
<div>` ``isr.close();`</div>
&nbsp;

&nbsp;