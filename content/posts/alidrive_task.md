---
title: "阿里云盘免费容量快速领取"
subtitle: ""
date: 2022-12-21T18:24:48+08:00
draft: false
author: "mxsix112"
authorLink: ""
authorEmail: ""
description: "快速完成相关任务"
keywords: ""
comment: false
weight: 0

tags:
- 阿里云盘
categories:
- 记录

hiddenFromHomePage: false
hiddenFromSearch: false

summary: ""
resources:
- name: featured-image
  src: featured-image.jpg
- name: featured-image-preview
  src: featured-image-preview.jpg

toc:
  enable: true
math:
  enable: false
lightgallery: true
seo:
  images: []

repost:
  enable: true
  url: "https://k.sina.com.cn/article_1823348853_6cae1875020016aqz.html"

# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->

最近在阿里云盘APP上看到免费扩容100G，并且有效时间是66年。但是领取之前需要完成三个任务分别为

1. [ ]开启相册备份
2. [ ]备份1000张图片
3. [ ]使用容量达到80G

如果之前一直使用阿里云盘第三项任务应该也是非常容易的，那么第二项备份1000张图片便是项及其有挑战性的任务，因为图片为个人隐私产品，所以通过代码生成非必要图片去完成相关任务。

## 具体流程

### 开启相册备份

登录阿里云盘，在首页发现那里可以看到“免费领66年容量”的热门任务，或者搜索福利社，找到这个任务。点进去可以看到三个任务，

　　第一步是“开启相册自动备份”的任务，点进去，看到4个选项，

- 必选的“开启相册自动备份”，开启即可。

- "**使用3G4G5G备份相册**"不要打开，

- "**允许后台自动备份**"不要打开，

  这两个是不让相册备份的必要条件。切记

- 选择相册备份，点进去，这个是不让你的隐私上传到网盘的重要条件，这里**选一个没用的文件夹**。例如表情包相册等

### 备份1000张图片

**用电脑端Windows的powershell来处理。**

1. 先在桌面新建文件夹，名称随意

2. 接着截屏一个小方块，命名"test.jpg"保存在这个文件夹里面

3. 在 文件夹管理器中输入powershell并回车

   ![示意图](https://assets.hifo.fun/imgs/blog/2022/12/powershell.webp "示意图")



​		复制下面的命令

```bash
for($n=0; $n -lt 999; $n=$n+1) { cp test.jpg new-$n.jpg }
```

​		然后到命令行窗口ctrl+v粘贴进去，回车就可以运行开始批量重命名复制了。瞬间，这个test.jpg的小图片就复制了999张，总共1000文件。

4. 最后电脑端登陆阿里云盘，在**左侧相册**栏目中新建一个文件夹存放图片，拖拽文件夹上传这1000张图片，整个操作1分钟内就搞定1000张照片备份任务了。

   ![操作示例](https://assets.hifo.fun/imgs/blog/2022/12/alidrive.webp "操作示例")



不想手动生成那就选择下载生成好的吧。{{< link href="https://share.hifo.fun/其他/1000.zip" content="1000张图片" title="1000张图片" download="https://share.hifo.fun/其他/1000.zip">}}



### 使用容量达到80G

最简单的方法保存别人分享的内容。{{< link "https://pan666.cn/" "阿里云盘资源网" "阿里云盘资源网">}}

<br>

最后，既然领了66年100g的容量，自然是要过桥拆板了，点头像，设置，**相册自动备份，然后关掉**就行了，接着把那个完成任务用的相册也删除掉，就完事了
