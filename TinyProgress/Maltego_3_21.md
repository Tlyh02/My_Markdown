#用 Maltego 收集子域名信息

--- 

## 子域名
- 子域名（Subdomain）是顶级域名+前缀的都是该顶级域名的子域名
- 子域名是某个主域的二级或多级域名，主域有时候防御过于严密，就从子域名下手

    1. 挖掘工具Maltego
    2. 搜索引擎 如 ： google:``site:qq.com``
    3. 第三方网站查询：
    - tool.chinaz.com/subdomain
    - dnsdumpster.com/
    4. 证书透明度公开日志枚举：
    - censys.io
    5. 其他途径： 
    - phpinfo.me/domain
    - dns.aizhan.com



---
- # 使用Maltego

1. 使用Maltego ce（社区版），先注册一个账号

2. 成功注册完成后会进入这样一个界面

    ![001](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023322_220819_1679494098491.png)

3. 点击左上角添加一个新的图版

    ![002](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023322_225817_1679497097317.png)

4. 在左侧组件搜索domain，拖出来

    ![003](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023322_230144_1679497303646.png)

5. 测试使用`baidu.com`，在domain组件里填写`baidu.com`，右键domain打开搜索工具栏

    ![004](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023322_230652_1679497612000.png)

6. 可以用这些搜索项建立和该主域名有关的信息图

    ![005](https://cdn.statically.io/gh/Tlyh02/TL-s-pictualstorge@main/img/2023322_231119_1679497879211.png)

7. Maltego可以检查的东西有很多，如IP，注册地址，域名有关的信息等等，enjoy！
---

