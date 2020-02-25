---
title: Hexo的图片显示问题
tags:
  - hexo
abbrlink: 7552
date: 2020-02-17 23:21:16
---

## 踩坑历程
在使用hexo发博客的时候发现发图片有点麻烦，记录一下踩坑历程。
 <!--more-->
- 参照[Hexo博客搭建之在文章中插入图片](https://yanyinhong.github.io/2017/05/02/How-to-insert-image-in-hexo-post/)这篇文章使用相对路径可以正常发图，但是后年发现因为我的博文生成的是永久链接导致只能使用标签插件语法。

- 发图之后发现图片显示过大，欲调显示比例，但是标签插件语法我不会缩放啊啊啊（如下）：
    ```
    {% asset_img image.jpg This is an image %}
    ```

- 尝试使用typora里面插入图片的语法（如下）：
    ```
    <img src="/Users/lyy/Library/Application Support/typora-user-images/image-20200213233811415.png" alt="image-20200213233811415" style="zoom: 50%;" />
    ```
    根据相对路径的方法改为：
    ```
    <img src=image-20200213233811415.png style="zoom: 50%;" />
    ```
    发到网站上发现查看图片链接地址：
    ```
    http://localhost:4000/archives/Hexo-Next%E9%85%8D%E7%BD%AE%E4%B8%AD%E9%81%87%E5%88%B0%E7%9A%84%E9%97%AE%E9%A2%98%E8%A7%A3%E5%86%B3/image-20200213233811415.png
    ```
    
    Hexo-Next%E...B3这一段是我的同名文件夹的名称，具体请看[Hexo博客搭建之在文章中插入图片](https://yanyinhong.github.io/2017/05/02/How-to-insert-image-in-hexo-post/)，但是这就少了一段abbrlink对应的一段字符(如下图)

    <img src=997342BA-E266-4339-BE45-E890D90DAE2E.png style="zoom: 50%;" />

    所以修改为
    ```
    <img src=b038c3e3/image-20200213233811415.png style="zoom: 50%;" />
    ```
    例子：

    <img src=8BA2FD05-18AF-4629-AC52-2A2D3EE72EDD.png style="zoom: 50%;" />

    显示正常并且缩放为原来的50%

- 但是这也太麻烦了每次还要复制abbrlink, 可能是永久链接的锅，把站点配置文件的permalink:改回默认的:year/:month/:day/:title/，再用
    ```
    <img src=image-20200213233811415.png style="zoom: 50%;" />
    ```
    显示正常，网站图片链接路径正常，缩放也正常。

## 总结
- 不要用标签插件语法
- 相对路径有问题，可能是post_asset_folder的默认设置原因，但是因为我懒，就在config里面的路径改回了默认的，毕竟搭它的目的是写博客，珍爱生命，远离折腾（逃）。
