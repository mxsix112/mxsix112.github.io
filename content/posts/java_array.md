---
title: "Java数组相关操作记录"
subtitle: ""
date: 2023-01-09T19:08:18+08:00
draft: false
author: "mxsix112"
authorLink: ""
authorEmail: ""
description: ""
keywords: ""
license: ""
comment: false
weight: 0
password: java

tags:
- java
- 数组
categories:
- Java

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
  enable: false
  url: ""

# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->

## 一维数组

> 对于一位数组，java对于一维数组的初始化操作为int[] a = new int[中间填写要创建的数组长度]
>
> 抑或是int[] a = {1,2,3,4,5} 直接在创建时赋值

本章节操作基于数组int[] array = {3,5,2,1,65}

### 寻求数组最小值

寻求一维数组的最小值在于先排序，再接着输出下标为0的值即可。而在java 中对于数组的排序有一个工具可快速完成排序操作即Arrays.sort(a) a为数组，Arrays 属于java.util类包。

```java
Arrays.sort(array);
System.out.println("最小值是: " +array[0]);

输出结果为:1
```

### 一维数组反转

通过逻辑分析，对于一维数组的反转，通过中间变量+循环即可做到

```java
for (int i = 0,j = array.length-1;i < j ; i++,j--) {//将数组反转
	int temp = array[i];//引入一个中间变量
	array[i] = array[j];
	array[j] = temp;
}
```

## 二维数组

java 中二维数组的初始化一共有三种情况

```java
int[][] a = new int[2][3]; //有两个一维数组，每个一维数组的长度是3
a[1][2] = 5;  //可以直接访问一维数组，因为已经分配了空间
          
//只分配了二维数组
int[][] b = new int[2][]; //有两个一维数组，每个一维数组的长度暂未分配
b[0]  =new int[3]; //必须事先分配长度，才可以访问
b[0][2] = 5;
        
//指定内容的同时，分配空间
int[][] c = new int[][]{
{1,2,4},
{4,5},
{6,7,8,9}
};
```

通过.length获取到的是二维数组的总行数。

### 二维数组排序

简单思路：复制到一维数组排完序后在复制回去

```java
void sort(int[][] array){
        System.out.println("------ 二维数组排序 ------");
        int[] array1 = new int[array.length*array[0].length];
        for (int i = 0; i < array.length; i++) {
            System.arraycopy(array[i],0,array1,i*array[i].length,array[i].length);
        }
        Arrays.sort(array1);
        for (int i = 0; i < array.length; i++) {
            System.arraycopy(array1,i*array[i].length,array[i],0,array[i].length);
        }
        twoDimensionalArray.output(array);
        /*0,8,16,24,32,*/
    }
```

