---
title: Hexo-Next配置中遇到的问题解决
abbrlink: b038c3e3
date: 2020-02-16 15:28:32
tags:
- hexo
categories: 每日折腾
---

## 配置rss 订阅
 <!--more-->
  1.下载插件：

  ```
  npm install hexo-generator-feed --save
  ```



  2.在站点配置文件_config.yml中添加：

  ```
  feed:
    type: atom
    path: atom.xml
    limit: 20
    hub:
    content:
    content_limit: 140
    content_limit_delim: ' '
    order_by: -date
    icon: icon.png
    autodiscovery: true
    template:
  ```

  1.在主题配置文件_config.yml中修改：

  ```php
  # Set rss to false to disable feed link.
  # Leave rss as empty to use site's feed link.
  # Set rss to specific value if you have burned your feed already.
  rss: /atom.xml //注意：有一个空格
  ```

## 首页文章添加阴影

  V 7.7.1版本没有`blog\themes\next\source\css\_custom\custom.styl`文件，打开`next\source\css\_common\components\post`下的`post.styl`文件。

  <img src=image-20200213233811415.png style="zoom: 50%;" />

  如上图，找到.post-block 并添加如下代码：

  ```
  // 主页文章添加阴影效果
   .post-block {
     margin-top: 60px;
     margin-bottom: 60px;
     padding: 25px;
     -webkit-box-shadow: 0 0 5px rgba(202, 203, 203, .5);
     -moz-box-shadow: 0 0 5px rgba(202, 203, 204, .5);
    }
  ```

  效果：

<img src=image-20200214100423922.png style="zoom: 50%;" />

   

## hexo 修改主题后远程网站不更新

  尝试方法：

  1. 删除.deploy_git 和 public 文件夹，再执行hexo clean , hexo g , hexo d。

<img src=image-20200214120300489.png style="zoom: 50%;" />

  2. chrome 浏览器f12开控制台，勾选disable cache

<img src=image-20200214120540110.png style="zoom: 50%;" />


  3. 试了以上两种方法都没成功，最后在浏览器清除所有浏览数据后更新成功。



## 参考链接

- [Hexo-NexT配置超炫网页效果](https://www.jianshu.com/p/9f0e90cc32c2)

- [Hexo博客的Next主题 7.5版本给首页文章添加阴影](https://blog.csdn.net/qq_39119496/article/details/103372437)

 
