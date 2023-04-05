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

---

## scapy-数据包定制程序

- 定制ARP包扫描
  - 显示基础ARP包配置`ARP().display()`
![002](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_144959_1680418199190.png)
  - 定义一个向网关发送的ARP数据包  
  - 函数`sr1`包含了发送数据包和接受数据包的功能`sr1(ARP(pdst="<gateway>"),timeout=100) #向网关发送一个ARP数据包`
![003](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_151520_1680419720125.png)

- 定制PING包
  -  IP/ICMP包
  -  `IP().display() #看IP默认数据包格式`
![004](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_152605_1680420364985.png)
  - `ICMP().display() #看ICMP默认数据包格式`![005](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_153415_1680420855013.png)
  - 使用上面两个函数生成ping包![006](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_154013_1680421212969.png)
  - `sr1(IP(dst="<gateway>")/ICMP(),timeout=100)`![007](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_154407_1680421447286.png)

- 定制TCP/SYN包
  - TCP三次握手![008](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_160143_1680422503809.png)
  - `TCP().display() #查看默认TCP包配置`![009](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_161025_1680423025303.png)
	> 标志位* :
  	> - 紧急标志URG，
	> - 有意义的应答标志 ACK，
	>- 推PSH，
	>- 重置链接标志RST，
	>- 同步序列号标志SYN，
	>- 完成发送标志FIN
  - `sr1(IP(dst="<target>")/TCP(flags="S",dport=80),timeout=1) #发送SYN包给目标`![010](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_163750_1680424669910.png)*flags=SA才成功建立半链接*
  - 僵尸扫描目标80端口![011](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202342_170111_1680426071231.png)