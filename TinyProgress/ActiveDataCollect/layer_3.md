# 三层扫描
----
## ping  
 - 使用ICMP报文判断主机存活
 - 

----  
## traceroute

- 和Windows上的 ``tracert`` 一样
- 

----  

## arping

>arping 192.168.1.1 -c 1  

- 通过arp协议将IP转换成MAC地址
- 查看网段中是否有IP冲突  
- 通过shell脚本自动化列举当前网段内所有物理机与对应Mac地址

小脚本：

>#!/bin/bash
if [ "\$#" -ne 1 ];then
	echo 'arpingAUTO.sh [network interface like(eth0)]'
	exit
fi
inf=\$1
pre=\$(ifconfig \$inf | grep "inet " | cut -d "t" -f 2 | cut -d "." -f 1-3 )
for i in \$(seq 1 254);do
	ip=\$(arping -c 1 \$pre.\$i | grep "from"| cut -d "(" -f 2 |cut -d ")" -f 1)
	mac=\$(arping -c 1 \$pre.\$i | grep "from" | cut -d "m" -f 2 | cut -d "(" -f 1 )
	if [ -n "\$ip" ];then
	echo "\$ip--\$mac"
	fi
done
>

如果出现了两个相同的IP地址即受到了ARP攻击

---

## Netdiscover进行主/被动网络发现

Netdiscover搜索局域网中的IP地址，检查在线主机或发送的ARP请求

主动：
`netdiscover -i  *(eth0) -r *(IPadress s)`
被动：
`netdiscover -p`

![001](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202341_140127_1680328886418.png)

---
## Hping3

使用组装TCP/IP包组装分析工具，可做压力测试或ddos，每次一个目标

压力测试：
`hping3 -c 1000 -d 120 -w 64 -p 80 -S --flood --rand-source *(target)`
>发送1000个数据包120字节，窗口大小为64字节的SYN包
目标端口为80，洪泛发送，随机源IP（内网未经过nat转换）
>

---

## Fping

增强版ping

`fping -g 192.168.*.*/16`