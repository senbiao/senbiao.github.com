---
title: cannot open file /etc/cloudstack/management/tomcat6.conf
id: 258
categories:
  - CloudStack
date: 2015-10-15 08:24:32
tags: JAVA
---

修改tomcat，由于tomcat为了区分ssl和没有ssl,所以配置分为tomcat6-nonssl.conf和tomcat6-ssl.conf，需要把tomcat6
-nonssl.conf更改tomcat6.conf，否则启动会报没有tomcat6.conf文件错误

[root@manage5156 run]#cp /usr/share/cloudstack-management/conf/server-nonssl.xml /usr/share/cloudstack-management/conf/server.xml

[root@manage5156 run]#cp /etc/cloudstack/management/tomcat6-nonssl.conf
/etc/cloudstack/management/tomcat6.conf
