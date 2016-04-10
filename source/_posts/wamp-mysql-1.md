---
title: WAMP中mysql的密码修改方法
tags:
  - MySql
id: 69
categories:
  - 数据库
date: 2013-10-25 12:20:23
---

&nbsp; &nbsp; &nbsp; 每次重装系统或者重装wamp之后，都要重新搭建php开发环境，这不又来了。

&nbsp; &nbsp; &nbsp; 有些东西久了没使用它，就容易生疏。像这里所说的wamp中的mysql密码、phpmyadmin密码等问题，我们在搭建环境的时候或许很快可以搞定，但时间久了要重新搞的时候又感觉有点麻烦了。因此这次我决定把这个过程给记录下来，以便以后翻阅。

前提是wamp已经安装好了，那么第一步首先通过WAMP打开mysql控制台。

[![QQ图片20131025120437.jpg](http://zhousenbiao.com/wp-content/uploads/2013/10/3611043254.jpg)](http://zhousenbiao.com/attachment/62/ "QQ图片20131025120437.jpg")

提示输入密码，因为现在是空，所以直接按回车。

[![QQ图片20131025120721.jpg](http://zhousenbiao.com/wp-content/uploads/2013/10/3266336872.jpg)](http://zhousenbiao.com/attachment/63/ "QQ图片20131025120721.jpg")

然后输入&ldquo;use mysql&rdquo;，意思是使用mysql这个数据库，提示&ldquo;Database changed&rdquo;就行。

[![QQ图片20131025120959.jpg](http://zhousenbiao.com/wp-content/uploads/2013/10/3269423899.jpg)](http://zhousenbiao.com/attachment/64/ "QQ图片20131025120959.jpg")

然后输入要修改的密码的sql语句&ldquo;update user set password=PASSWORD('admin') where user='root';&rdquo;，注意，sql语句结尾的分号不能少，提示Query OK&hellip;&hellip;即可。

[![QQ图片20131025121320.jpg](http://zhousenbiao.com/wp-content/uploads/2013/10/3352295584.jpg)](http://zhousenbiao.com/attachment/65/ "QQ图片20131025121320.jpg")

最后输入&ldquo;flush privileges;&rdquo;，不输入这个的话，修改密码的操作不会生效的。

[![QQ图片20131025121445.jpg](http://zhousenbiao.com/wp-content/uploads/2013/10/4294617675.jpg)](http://zhousenbiao.com/attachment/66/ "QQ图片20131025121445.jpg")

然后输入&ldquo;quit&rdquo;退出。

&nbsp; &nbsp; &nbsp; 如果在浏览器中访问phpmyadmin出现如下错误：#1045 - Access denied for user 'root'@'localhost'&nbsp;(using password: YES)&nbsp;

[![QQ图片20131025121743.jpg](http://zhousenbiao.com/wp-content/uploads/2013/10/4140904756.jpg)](http://zhousenbiao.com/attachment/68/ "QQ图片20131025121743.jpg")

那么说明mysql的密码已修改了，但是phpmyadmin相对于的配置文件还未修改。请在wamp的phpmyadmin目录下找config.inc.php进行修改。比如我的电脑中，目录是E:\wamp\apps\phpmyadmin3.5.1，那么在这个目录下找到config.inc.php文件并打开，ctrl+F查找$cfg['Servers'][$i]['password']，将其改为$cfg['Servers'][$i]['password']='admin'，admin即是修改后的密码。

[![QQ图片20131025121450.jpg](http://zhousenbiao.com/wp-content/uploads/2013/10/2766738.jpg)](http://zhousenbiao.com/attachment/67/ "QQ图片20131025121450.jpg")