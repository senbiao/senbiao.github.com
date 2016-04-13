---
title: CentOS6下yum方式安装svn客户端subversion(亲测可用)
tags:
  - CentOS
id: 243
categories:
  - 操作系统
date: 2015-09-19 09:13:14
---

目前找到一个当下能用的yum源，进行快速安装subversion

在 /etc/yum.repos.d/ 创建源文件 wandisco-svn1.8.repo
[WANdisco]
name=WANdisco SVN Repo 1.8
enabled=1
baseurl=http://opensource.wandisco.com/rhel/6/svn-1.8/RPMS/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-WANdisco

然后导入GPG-KEY
wget http://opensource.wandisco.com/RPM-GPG-KEY-WANdisco
rpm --import RPM-GPG-KEY-WANdisco

再进行安装：
yum update
yum -y install subversion

&nbsp;
