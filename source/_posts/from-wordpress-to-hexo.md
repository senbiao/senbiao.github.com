---
title: from wordpress to hexo
date: 2016-04-15 16:16:02
tags: 
  - hexo
categories:
  - summary
---
	
	   自己搭建独立博客，最简单的总结就是两个字，折腾。
       我从2012年开始了博客折腾之路，貌似漫长，其实中间因为两个字，懒惰，导致写博客的状态是断断续续，并且质量不高。博客折腾的历程，从所使用的程序来看，是由wordpress开始，转typecho，再转回wordpress，转hexo。wordpress自然不必说，强大，之所以转typecho是主要是因为好奇、而且typecho非常轻量，整个程序才几兆，后来typecho官方不更新了，久而久之自己也懒了，又开始感觉wordpress才是王道，转回wordpress一直用到去年底，某天突然发现博客访问不了了，但wp-admin.php后台能进，猜想是模板什么地方出问题了吧，还是因为懒，没去细究，就这样一直放着，放了好几个月了，最近突然想起来不能再这样荒废下去了，我要重新勤奋起来！
       之前就接触过基于node.js的静态博客hexo，这次我决定不再用那几百块一年的虚拟主机了，尽管还有大半年才到期。周末花时间一阵折腾，于是我正式把博客转到了hexo！！！这里简单记录一下hexo的折腾过程。
       1.安装篇
安装Git
下载 msysgit 并执行即可完成安装。
安装Node.js
在 Windows 环境下安装 Node.js 非常简单，仅须下载安装文件并执行即可完成安装。
安装hexo
利用 npm 命令即可安装。（在任意位置点击鼠标右键，选择Git bash）

npm install -g hexo
额外参考：：：
1.安装brewhome，一句话搞定
ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)”
2.0 安装nodejs 
2.1 第一种方式，brewhome安装，一句话搞定
brew install node
2.2 第二种方式，前提是已经安装好Xcode和git，安装git方法在下面介绍
git clone git://github.com/joyent/node.gitcd node
./configure
make
sudo make install
2.3 第三种方式，下载源码( http://nodejs.org/download/ )，编译执行同上 

2.本地运行
创建hexo文件夹
安装完成后，在你喜爱的文件夹下（如H:\hexo），执行以下指令(在H:\hexo内点击鼠标右键，选择Git bash)，Hexo 即会自动在目标文件夹建立网站所需要的所有文件。

hexo init

安装依赖包

npm install

本地查看

现在我们已经搭建起本地的hexo博客了，执行以下命令(在H:\hexo)，然后到浏览器输入localhost:4000看看。

hexo generate
hexo server

3.部署

编辑_config.yml(在H:\hexo下)。你在部署时，要把下面的zippera都换成你的账号名。

deploy:
  type: github
  repository: https://github.com/senbiao/senbiao.github.io.git
  branch: master

据说最新版本的hexo 中，这里的 type 要写成 git，而不是 github。
执行下列指令即可完成部署。

hexo generate
hexo deploy

注意：有些新用户需要设置 ssh，否则上述命令会失败。ssh 的介绍和设置方法请看官方教程，不用担心，很简单。
记住：每次修改本地文件后，需要hexo generate才能保存。每次使用命令时，都要在H:\hexo目录下。

4.技巧

遇到什么其他的问题，不妨删除.deploy 和db.json 再重新生成试一试。
tips
hexo现在支持更加简单的命令格式了，比如：
hexo g == hexo generate
hexo d == hexo deploy
hexo s == hexo server
hexo n == hexo new
其他Tips

有的时候当你修改页面或更改配置后发现并没有立即生效，可以执行hexo clean然后再启动hexo server。
默认的评论组件可能并不太适合中国大陆用户（你懂的。。），你可以选择性的换成别的组件，或主题，比如我用的多说评论以及Pacman主题。
参与开源项目很简单，你只需要学会使用Git以及Github，遇到bug或任何程序问题可以递交issue，当然如果你有能力自己解决问题或可以为Hexo开发新的功能，那么请pull request。

hexo可能更新过了,所以老的hexo可能会报错:
{ [Error: Cannot find module './build/Release/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }
{ [Error: Cannot find module './build/default/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }
{ [Error: Cannot find module './build/Debug/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }
解决办法：
先执行： npm uninstall hexo 
再执行： npm install hexo --no-optional

从Wordpress转移过来的，写了一段时间之后，文章全部在那里面，如果一篇篇的复制粘贴那工作量就太大了。好在Hexo提供了Wordpress插件，可以一次性把wordpress数据导入到Hexo博客，html文件都转换成了Markdown文件，非常的方便，有图片的更改一下图片的路径就好了。


首先导出wordpress数据，得到的回事一个xml格式的文件，先把这个复制到Hexo文件夹下，假设文件是wordpress.xml。
安装好wordpress插件，再使用迁移命令就可以实现从Wordpress到Hexo的转移。

npm install hexo-migrator-wordpress --save
hexo migrate wordpress wordpress.xml



额，不知道是不是有人跟我一样有一个库没有README.md文件就浑身不舒服的强迫症= =
正如大家所知道的，在source文件夹下的所有md文件都会被hexo渲染成html文件，导致README.md文件不能好好的放在里面了，即使是添加了layout: false依然没有用。
不过现在有一个另外的好办法，那就是利用主题的source目录，也就是themes/themes-name/source。因为这个文件夹里面的所有文件都会被复制到网站的根目录中去，也就是说，如果在里面放上README，就可以正常的存在于网站的主目录了。
同样的，对于一些需要在网站下添加html文件的需求也可以这样来达成。比如百度或者谷歌在验证站长权限的时候，通常都会要求在主目录下添加一个html文件。同样的，只要把这个文件放在themes/themes-name/source就可以搞定了。



5.问题解决

（1）
git push -u origin master
(gnome-ssh-askpass:20853): Gtk-WARNING **: cannot open display:

unset SSH_ASKPASS



（2）git rm 误删文件找回方法
git rm a.txt ，误将a.txt删除后找回方法：
1. git log 找到离没删文件前最近的commit id
2. 将操作过的其它文件转移
3. git reset --hard "commit id"

（3）git操作
#添加当前修改的文件到暂存区  
git add .  
  
#如果你自动追踪文件，包括你已经手动删除的，状态为Deleted的文件  
git add -u  
  
#提交你的修改  
git commit –m "你的注释"  
  
#推送你的更新到远程服务器,语法为 git push [远程名] [本地分支]:[远程分支]  
git push origin master  
  
#查看文件状态  
git status  

（4）
[git@AYZ github01]$ git push -u origin master
error: The requested URL returned error: 403 Forbidden while accessing https://github.com/iopqrst/learn20140823.git/info/refs
在要推送项目的文件目录下：
vi .git/config

# 将
[remote "origin"]  
    url = https://github.com/iopqrst/learn20140823.git
修改为：
[remote "origin"]
url = https://iopqrst@github.com/iopqrst/learn20140823.git

（5）
git remote rm origin
git remote add origin git@github.com:Liutos/foobar.git
方法二：直接修改.git/config
注意事项



所有键的冒号后面留一个空格，如language: zh-CN  

url不能为空,否则报错  

type: github报错hexo ERROR Deployer not found: github的解决方法：
先运行 npm install hexo-deployer-git --save
再改为 type: git

1.导入『Wordpress数据』


　　开篇我说过我写博客的基本经历，是从Wordpress转移过来的，写了一段时间之后，文章全部在那里面，如果一篇篇的复制粘贴那工作量就太大了。好在Hexo提供了Wordpress插件，可以一次性把wordpress数据导入到Hexo博客，html文件都转换成了Markdown文件，非常的方便，有图片的更改一下图片的路径就好了。


首先导出wordpress数据，得到的回事一个xml格式的文件，先把这个复制到Hexo文件夹下，假设文件是wordpress.xml。

安装好wordpress插件，再使用迁移命令就可以实现从Wordpress到Hexo的转移。


npm install hexo-migrator-wordpress --savehexo migrate wordpress wordpress.xml


文／起今知行（简书作者）
原文链接：http://www.jianshu.com/p/739bf1305e66
著作权归作者所有，转载请联系作者获得授权，并标注“简书作者”。


hexo d，执行该命令，报错：

1
ERROR Deployer not found: git

执行命令：
npm install hexo-deployer-git --save，再次执行hexo d

升级至Hexo 3.0版本后，deploy报错