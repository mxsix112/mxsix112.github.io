---
title: "Java字符串相关操作"
subtitle: ""
date: 2023-01-10T10:48:41+08:00
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
- 字符串
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

## 随机字符串

数字0~9 十进制范围 48-57

大写字母 65-90 

小写字母 97-122

{{< admonition warning "ASCII码表" false >}}

| 字符 | 十进制数字 | 十六进制数字 |
| ---- | ---------- | ------------ |
| !    | 33         | 21           |
| "    | 34         | 22           |
| #    | 35         | 23           |
| $    | 36         | 24           |
| %    | 37         | 25           |
| &    | 38         | 26           |
| '    | 39         | 27           |
| (    | 40         | 28           |
| )    | 41         | 29           |
| *    | 42         | 2A           |
| +    | 43         | 2B           |
| ,    | 44         | 2C           |
| -    | 45         | 2D           |
| .    | 46         | 2E           |
| /    | 47         | 2F           |
| 0    | 48         | 30           |
| 1    | 49         | 31           |
| 2    | 50         | 32           |
| 3    | 51         | 33           |
| 4    | 52         | 34           |
| 5    | 53         | 35           |
| 6    | 54         | 36           |
| 7    | 55         | 37           |
| 8    | 56         | 38           |
| 9    | 57         | 39           |
| :    | 58         | 3A           |
| ;    | 59         | 3B           |
| <    | 60         | 3C           |
| =    | 61         | 3D           |
| >    | 62         | 3E           |
| @    | 64         | 40           |
| A    | 65         | 41           |
| B    | 66         | 42           |
| C    | 67         | 43           |
| D    | 68         | 44           |
| E    | 69         | 45           |
| F    | 70         | 46           |
| G    | 71         | 47           |
| H    | 72         | 48           |
| I    | 73         | 49           |
| J    | 74         | 4A           |
| K    | 75         | 4B           |
| L    | 76         | 4C           |
| M    | 77         | 4D           |
| N    | 78         | 4E           |
| O    | 79         | 4F           |
| P    | 80         | 50           |
| Q    | 81         | 51           |
| R    | 82         | 52           |
| S    | 83         | 53           |
| T    | 84         | 54           |
| U    | 85         | 55           |
| V    | 86         | 56           |
| W    | 87         | 57           |
| X    | 88         | 58           |
| Y    | 89         | 59           |
| Z    | 90         | 5A           |
| [    | 91         | 5B           |
| \    | 92         | 5C           |
| ]    | 93         | 5D           |
| ^    | 94         | 5E           |
| _    | 95         | 5F           |
| `    | 96         | 60           |
| a    | 97         | 61           |
| b    | 98         | 62           |
| c    | 99         | 63           |
| d    | 100        | 64           |
| e    | 101        | 65           |
| f    | 102        | 66           |
| g    | 103        | 67           |
| h    | 104        | 68           |
| i    | 105        | 69           |
| j    | 106        | 6A           |
| k    | 107        | 6B           |
| l    | 108        | 6C           |
| m    | 109        | 6D           |
| n    | 110        | 6E           |
| o    | 111        | 6F           |
| p    | 112        | 70           |
| q    | 113        | 71           |
| r    | 114        | 72           |
| s    | 115        | 73           |
| t    | 116        | 74           |
| u    | 117        | 75           |
| v    | 118        | 76           |
| w    | 119        | 77           |
| x    | 120        | 78           |
| y    | 121        | 79           |
| z    | 122        | 7A           |
| {    | 123        | 7B           |
| \|   | 124        | 7C           |
| }    | 125        | 7D           |
| ~    | 126        | 7E           |

{{< /admonition >}}

```java
void charRandom(int length){
        StringBuilder randomString = new StringBuilder();
        Random random = new Random();//随机数生成类
        int num;
        char c;
        for (int i = 0; i < length; i++) {
            num = random.nextInt(75) + 48; //随机数范围是48，122
            //48-57 数字 65-90 是大写字母 97-122是小写字母

            if ((num > 57 && num < 65) || (90 < num && num < 97)) {
                i--;
                continue;
            }
            System.out.print(num+"\t");
            c = (char) num;
            randomString.append(c);
        }
        System.out.println(randomString);
    }
```

## 字符串数组排序

> 通过获取字符串数组中的每一个字符开串头字符ascll 码进行选择排序比较

```java
 void sortString() {
        String[] strings = new String[8];
        for (int i = 0; i < strings.length; i++) {
            strings[i] = characterTest.charRandom(5);
        }
        System.out.println(Arrays.toString(strings));

        /*选择排序*/
        for (int i = 0; i < strings.length - 1; i++) {
            for (int j = i + 1; j < strings.length; j++) {
                char i1 = strings[i].charAt(0);
                char i2 = strings[j].charAt(0);
                //如果其中有一个那么他就是true 数字放前面并进行排序操作
                if (Character.isUpperCase(i1)){
                    i1= Character.toLowerCase(i1);
                }
                if (Character.isUpperCase(i2)){
                    i2= Character.toLowerCase(i2);
                }
                if (i2 < i1 ) {
                    String a = strings[i];
                    strings[i] = strings[j];
                    strings[j] = a;
                }
            }
        }
        for (String i : strings) {
            System.out.println(i);
        }
        System.out.println(Arrays.toString(strings));
    }
```

## 暴力破解密码

随机生成3位密码(范围是数字,小写字母,大写字母)。再通过多层循环以及递归方式去寻找密码。

### 多层循环破解

> 多层循环破解通过三层嵌套循环找到密码

```java
void BruteForce(){
        System.out.println(a);
        char[] chars = new char[a.length()];
        /*多层循环寻找密码*/
        long begin = System.currentTimeMillis();
        outLoop:
        for (int i = '0'; i < 'z'; i++) {
            for (int j = '0'; j < 'z'; j++) {
                for (int z = '0'; z < 'z'; z++) {
					//通过Character类中isLetterOrDigit去判断是否为数字或字母，不是则提前进入下一循环。
                    if (!Character.isLetterOrDigit(i) || !Character.isLetterOrDigit(j) || !Character.isLetterOrDigit(z)) {
                        continue;
                    }
                    chars[0]=(char)i;
                    chars[1]=(char)j;
                    chars[2]=(char)z;
                    if (String.valueOf(chars).equals(a)) {
                        long end = System.currentTimeMillis();
                        System.out.printf("暴力破解密码为%s,消耗时间为%s ms", String.valueOf(chars),end - begin);
                        break outLoop;
                    }
                }
            }
        }
    }
```

### 递归实现破解密码

>通过递归方式进行密码寻找

```java
boolean isreturn=false;
    void findPass(char []random,int index){
        long start=System.currentTimeMillis();  //计算时间
        for(int i='0';i<='z';i++){
            if(!Character.isLetterOrDigit(i))
                continue;
            random[index] = (char) i;
            if(index<random.length-1){  //如果数组没有填满则递归，进入套娃
                if(isreturn)  //判断结束语句应该放这里，因为第一个(套娃)递归结束之后，会回到进入递归的方法这里也就是for循环里面，遇到return结束上一个套娃，直到全部结束
                    return;
                findPass(random,index+1);
            }else if(String.valueOf(random).equals(this.a)){
                System.out.println("密码已经找到："+String.valueOf(random));
                long end=System.currentTimeMillis();
                System.out.format("使用递归穷举法耗费的时间是：%d ms %n",(end-start));
                isreturn=true;  //用于结束全部的方法
                return;  //结束该递归(套娃)方法
            }
        }
    }
```

