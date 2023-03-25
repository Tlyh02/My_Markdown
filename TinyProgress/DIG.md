##dns信息收集-DIG
---
- dig：dig （选项） 需要查询的域名
- @< DNS服务器地址 > #指定进行域名解析的服务器
    > 8.8.8.8 #
    114.114.114.114
    >
- any #显示所有类型的域名记录，默认显示A记录，加在查询句尾
    > hi.china 万网
- -x #反查 IP -> 域名
![001](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023321_173126_1679391086424.png)

- 利用BIND查询DNS服务器版本信息，通过版本信息查找相关版本漏洞利用方式

    > dig txt chaos VERSION.BIND @你想查询的DNS
    >
    有可能找不到或者被拒绝，可以换别的或国外IP试一下
    >此测试用ns2.dnsv4.com
    >
    ![002](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023321_174756_1679392076178.png)
- 使用whois查询域名信息
    1. terminal内用 ``who is @domin ``查询

    ![003](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023321_180541_1679393140363.png)
    2. 使用web在线查询
    > whois.aliyun.com
    > whois.chinaz.com
    >
    3. 备案信息查询


    - `` https://icp.chinaz.com ``#站长工具
    - `` https://www.tianyancha.com/ ``#天眼查
    - `` https://www.beian.gov.cn ``#公安机关

   