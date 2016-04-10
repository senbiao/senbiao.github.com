---
title: cloudstack二次开发——配置Debug端口
id: 261
categories:
  - ClousStack
  - 云计算
date: 2015-10-15 08:33:03
tags:
---

## <span style="font-size: 16px;">1.manage:</span>

vi /usr/sbin/tomcat6

-classpath "$CLASSPATH"  -Xrunjdwp:transport=dt_socket,address=8787,server=y,suspend=n\

2.agent:

vi /etc/init.d/cloudstack-agent

$JSVC -Xrunjdwp:transport=dt_socket,address=18787,server=y,suspend=n  -cp "$CLASSPATH" -pidfile "$PIDFILE" \

&nbsp;

&nbsp;