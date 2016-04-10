---
title: 'NFS umount 提示 device is busy '
id: 255
categories:
  - ClousStack
date: 2015-10-13 02:34:36
tags:
---

[root@node11 SecStorage]# umount /mnt/SecStorage/

umount.nfs: /mnt/SecStorage: device is busy

umount.nfs: /mnt/SecStorage: device is busy

解决方法：

增加一个-l参数：umount  -l  /mnt/SecStorage

或者：

fuser -m -v /mnt/SecStorage

进程占用了，将其kill掉，再重新umount
kill -xxxx
umount  /mnt/SecStorage