# Shodan_Data_collect
---
- Shodan信息收集介绍

    Shodan使用IP搜索查找和互联网关联的服务器，摄像头，打印机，路由器等等，可以大概显示出目标具体地理位置
   
    官网 www.shodan.io ；

    ### Shodan有每日最大搜索量（大概15次？），想好了再搜索，而且非付费用户只能看两页

---

- 进行网络摄像头实验，

    ![001](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023325_123720_1679719039947.png)

    用之前先注册一个账号，在搜索框中搜索`webcam`，

    ![002](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023325_124055_1679719254853.png)

    搜索国内webcam，

    ![003](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023325_124534_1679719534481.png)

    或者在搜索框中加入`country:"CN"`,

    ![004](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023325_124655_1679719615514.png)

    打开搜索到的链接，

    ![005](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023325_124843_1679719723218.png)

    （国内没有什么能看的结果，使用别的）

    ![006](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023325_125611_1679720170968.png)

    打开后，

    ![007](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023325_125711_1679720231688.png)

    可以控制摄像头上下左右转，挺有意思的，

---

- 对域名与IP进行搜索
    - IP搜索：

        使用  百度 进行实验
        在搜索栏中键入`net:39.156.66.10`（`218.28.242.216`）
        **今天次数用完了，之后再补图**

    - port搜索：

        键入`port:$Port`
        `port:9200` 查看ELK日志分析，
        `port:3000` 查看服务器监控登录平台上登录账号，可暴力破解，
        `port:22`SSH

---

- 有趣的搜索（在Google上进行查询）

    https://github.com/jakejarvis/awesome-shodan-queries