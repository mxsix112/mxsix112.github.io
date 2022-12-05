---
title: "笔记本关机等待时间久"
subtitle: ""
date: 2022-09-15T14:14:37+08:00
draft: false
author: "mxsix112"
authorLink: ""
authorEmail: ""
description: "对于联想amd系列有效"
keywords: "amd,联想,笔记本,小新"
comment: false
weight: 0

tags:
- 笔记本
categories:
- 记录

hiddenFromHomePage: false
hiddenFromSearch: false

summary: ""


toc:
  enable: true
math:
  enable: false
lightgallery: false
seo:
  images: []

repost:
  enable: false
  url: ""

# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->

> 重装完系统后，发现笔记本关机时，屏幕率先息灭，但是电源灯依旧处于电量状态，需等待一段时间才会熄灭。

## 解决方法

1. 下载[Amd Audio Coprocessor 驱动](https://drivers.softpedia.com/get/SOUND-CARD/OTHER-SOUNDCARDS/Compal-AMD-Audio-CoProcessor-Driver-2-89-0-59-for-Windows-10-S-64-bit.shtml)
2. `Win + S` 输入「设备管理器」并打开
3. 找到`系统设备`-`Amd Audio Coprocessor`-`右键属性`-`驱动程序`-`更新驱动程序`-`查看我的电脑以查找驱动程序`，根据提示选择即可。

## 参考文章

1. [大家注意amd audio coprocessor这个驱动「百度贴吧」](https://tieba.baidu.com/p/6947714197)
2. [锐龙版小新出现关机时间长的情况的解决办法「联想社区」](https://mclub.lenovo.com.cn/forum.php?mod=viewthread&tid=5602166&forcemobile=1)
3. [更新AMD AMD Audio CoProcessor驱动后开机、关机、重启非常慢「联想社区」](https://mclub.lenovo.com.cn/thread-7813296-1-1.html)
