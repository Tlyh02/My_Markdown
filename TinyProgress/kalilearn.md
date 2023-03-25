>sudo passwd root #修改root密码
----
>cd .ssh
>vim authorized_keys #公钥
---
>su - root 
>sudo -i #进入root
---
>apt update #获取软件更新列表
---
>ifconfig #获得主机网络信息
---
>ps -ef #查看进程信息
>kill -9 PID#根据PID停止进程
---
>https://senjianlu.com/2021/10/centos7-shadowsocks-server/ #配置shadowsocks教程
> #启动 Shadowsocks 服务
>systemctl start shadowsocks-libev
>#检查服务状态
>systemctl status shadowsocks-libev
>#服务开机自启
>systemctl enable shadowsocks-libev
>#查看 Shadowsocks 服务的全部日志
>journalctl -u shadowsocks-libev

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU2MTIzNTAzNSwxMTI4OTQ4NTkwLC0xNz
M3NTcyMjQ4LC0xMDE4NDYwMDUyLC01MjEwNTI3ODYsLTE0Mjg3
MzE0OTldfQ==
-->