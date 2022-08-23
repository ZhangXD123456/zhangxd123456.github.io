---
title: 使用github搭建免费的个人博客网站
date: '2022-08-01 12:46'
abbrlink: 9163
categories: ipad编程
tags:
    - 软件
    - 编程
    - ipad
---
# GitHub 搭建个人免费博客网站
## 第一 步 创建 New repository
![](http://ezblog.gnway.cc/i/2022/08/17/62fcf0769b779.jpeg)
## 第二步 在 Repository name 中输入网站的名字要使用 Owner 的小写。
![](http://ezblog.gnway.cc/i/2022/08/17/62fcf0be27891.png)
![](http://ezblog.gnway.cc/i/2022/08/17/62fcf1165ee16.png)
能看出来 Owner 的小写是一个特殊的仓库。成功后通过 https://zhangxd123456.github.io 可以访问自己的博客。目前还不可以，通过该地址访问提示 404 。
---
>ps:这里注意，命名的时候应当是 zhangxd123456.github.io 而不是 zhangxd123456，如果命名错了可以从下图的位置修改，setting->General->Repository name
![](http://ezblog.gnway.cc/i/2022/08/17/62fcf15e7e455.png)
![](http://ezblog.gnway.cc/i/2022/08/17/62fcf2c2a9705.png)
---
>ps：如果命名时没有按照规则比如命名为 zblog，输入网址 https://zblog.github.io 网址会跳转黄色网站。
## 第三步 初始化网站，在仓库 setting 属性中选择 pages 标签页初始化网站。初始化完成后地址变成了 https://zhangxd123456.github.io/zhangxd123456/，很奇怪。
![](http://ezblog.gnway.cc/i/2022/08/17/62fcf30809659.png)
---
>注意：在命名 repository 名字的时候注意时 owner 小写+github.io。如果仅用 owner 小写则登陆地址将变为 https://owner 小写.github.io/owner 小写/
