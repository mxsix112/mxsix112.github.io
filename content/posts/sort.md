---
title: "数组排序操作"
subtitle: ""
date: 2023-01-12T11:33:35+08:00
draft: true
author: "mxsix112"
authorLink: ""
authorEmail: ""
description: ""
keywords: ""
license: ""
comment: false
weight: 0
password: sort

tags:
- draft
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
lightgallery: false
seo:
  images: []

repost:
  enable: false
  url: ""

# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->

## 快速排序

- ### **思路**

	首先找一个基准，一般为数组中第一个数。然后比基准小的放在基准左边，大的放在基准右边。接着将基准左边的进行同样的操作，右边也是同样的操作。最后排序完成。

- ### **代码**

  ```java
  void quickSortBefore(int[] a, int left, int right) {
    if (left>right) return;
    //基准下标
    int base =a[left];
    int i = left;int j = right;
  
    //全部小的放左边大的放右边
    while (i < j) {
        //大的不动,直到找到小的
        while (i < j && a[j] >= base) j--;
        //小的不动,直到找到大的.
        while (i < j && a[i] <= base) i++;
        //如果左边大右边小然后交换值
        if (i < j) {
            swap(a, i, j);
        }
    }
    //交换基准位置下标为i
    swap(a,left,i);
    //左边重新排序
    quickSortBefore(a, left, j - 1);
    //右边重新排序
    quickSortBefore(a, j + 1, right);
  }
  void swap(int[] a, int i, int j) {
      int temp = a[i];
      a[i] = a[j];
      a[j] = temp;
  }

**思考：为什么先从右边先寻找接着左边在寻找**

>
>{6, 5, 1, 7, 9}
>
>
>假设从左边开始（与正确程序正好相反）
>
>```java
>while (nums[i] <= index && i < j) { 
>	i++; 
>}
>while (nums[j] >= index && j > i) {
>	j--;
>}
>```
>
>按照这个代码逻辑，走一遍，i 就会移动到现在的 数字 7 那个位置停下来，而  j 原来在 数字 9 那个位置
>
>于是，j 也会停留在数字 7 那个位置，然后 i == j 了，这时候交换基准数和 nums [i]
>
>交换后的数组为：[7,5,1,6,9]
>
>这时候，你会发现问题来了，这结果不对呀！！！
>
>问题在于当我们先从在边开始时，那么 i 所停留的那个位置肯定是大于基数 6 的
>
>而在上述例子中，为了满足 i<j 于是 j 也停留在 7 的位置，但最后交换回去的时候，7 就到了左边
>
>不行，因为我们原本 交换后数字 6 在边应该是全部小于 6，右边全部大于 6，但现在不行了。
>
>所以，我们必须从右边开始，也就是从基准数的对面开始。
