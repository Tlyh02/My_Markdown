## CentOS 7  

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


## kali(debian)

![002](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/202345_130354_1680671033433.png)

> /etc/network/interfaces

局域网内更改

> auto eth0
> iface eth0 inet static
> address <网段+你选的1-255，不要和别人重复>
> netmask <根据你的网关，一般255.255.255.0>
> gateway  *gateway

改国内镜像源
>vi /etc/apt/sources.list

- 删除原先内容，添加下列内容：

>deb https://mirrors.ustc.edu.cn/debian/ bullseye main contrib non-free
deb-src https://mirrors.ustc.edu.cn/debian/ bullseye main contrib non-free
deb https://mirrors.ustc.edu.cn/debian/ bullseye-updates main contrib non-free
deb-src https://mirrors.ustc.edu.cn/debian/ bullseye-updates main contrib non-free
deb https://mirrors.ustc.edu.cn/debian/ bullseye-backports main contrib non-free
deb-src https://mirrors.ustc.edu.cn/debian/ bullseye-backports main contrib non-free
deb https://mirrors.ustc.edu.cn/debian-security/ bullseye-security main contrib non-free
deb-src https://mirrors.ustc.edu.cn/debian-security/ bullseye-security main contrib non-free

- 完成后运行：
>apt-get update
apt-get upgrade

SSH配置

>vi /etc/ssh/sshd_config
取消PermitRootLogin行注释，并将值改为yes
取消PasswordAuthentication yes行注释
开启ssh服务并设置开机自启
/etc/init.d/ssh start
update-rc.d ssh enable