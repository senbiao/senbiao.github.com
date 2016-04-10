---
title: cloudstack二次开发——编译单个模块来升级系统
id: 264
categories:
  - ClousStack
  - 云计算
date: 2015-10-15 08:53:42
tags:
---

cloudstack二次开发中，当修改了代码时，需要重新编译，此时编译整个cloudstack尤为不便:
<div>`$ mvn clean`</div>
<div>`$ mvn install -Dnoredist`</div>
因此，考虑针对单个模块进行编译并替换到已安装的相关节点中，以cloudstack中的kvm模块为例：

首先，编译cloudstack中的kvm工程：
<div>`$ mvn clean`</div>
<div>`$ mvn -pl:cloud-plugin-hypervisor-kvm`</div>
然后，把plugins/hypervisors/kvm/target/下的cloud-plugin-hypervisor-kvm-4.2.1.jar 替换到安装KVM的agent节点中:/usr/share/cloudstack-agent/lib/cloud-plugin-hypervisor-kvm-4.2.1.jar，最后，重启一下agent节点。

至此，便已成功把kvm模块中修改过的部分更新到已部署好的cloudstack中了。