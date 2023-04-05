# CentOS 7  
---
`/etc/sysconfig/network-script/ifcfg-<interface>#网络接口配置信息`
![001](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_135920_1680415160092.png)

局域网内更改

> BOOTPROTO=static
> ONBOOT=yes
> DNS1=<gatway>
> IPADDR=<网段+你选的1-255，不要和别人重复>
> NETMASK=<根据你的网关，一般255.255.255.0>
> GATEWAY=<gatway>

`systemctl restart network #重启网络服务`

py:根据宿主机配置确定网络网关