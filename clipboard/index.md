# 保护你的剪切板


<!--more-->

> 每到618/双十一，各路平台口令乱飞。这也是一些网站拥有着为了增加部分收入，给相关网站增加了一些方式去“攻击”用户的剪切板，使得访问者的剪切板中拥有大量的口令垃圾，并且也会增加用户去购物平台时的时间。当然对于这种行为，一些手机拥有禁止软件访问剪切板的功能，会使得剪切板清净一些，但对于没有此项功能的手机用户来说，以下方法便是最简单的解决办法。



## 解决方案

1. 安装一个支持脚本运行的浏览器，类如via,alook,狐猴以及其他

2. [首页 (via-app.cn)](http://via-app.cn/#/tabBar/home)该网站中搜素复制授权，安装即可。



{{< admonition tip "若提示 **❗你的浏览器不支持安装插件** ，点击展开复制粘贴" true >}}

```js
// ==UserScript==
// @name        复制授权
// @include     *
// @version     1.0
// @author      -
// @description 2022/7/16 16:18:21
// ==/UserScript==

/*
 * @name: 复制授权
 * @Author: Sky
 * @version: 1.4
 * @description: 管理网页复制行为
 * @include: *
 * @createTime: 2020-8-8 11:55
 * @updateTime: 2021-11-7 23:10
 */
(function(){const
/* 等号后的数可供修改
 1为是 0为否 */
needc = 1, /* 拦截复制时是否弹窗确认 */
shows = 1, /* 是否显示小红点开关 */
/*－－－－以下勿改－－－－*/
 key = encodeURIComponent('复制授权:执行判断');
 if(window[key]){return;}
 try {
  window[key] = true;
  let red = true,
  lastCopyTime = 0;
  function copyHandle(e){
   function stopCopy(){e.preventDefault();e.stopImmediatePropagation();lastCopyTime = Date.now();}
   if(Date.now() - lastCopyTime < 100){stopCopy();return;}
   if(red && !(needc && confirm('网页正在尝试复制，是否允许？'))){stopCopy();}
  }
  document.addEventListener('copy',(e)=>copyHandle(e),{'passive':false, 'capture':true});
  Array.from(document.getElementsByTagName('iframe')).forEach((i)=>i.contentDocument.addEventListener('copy',(e)=>copyHandle(e),{'passive':false, 'capture':true}));
  if(shows){
   const sw = document.createElement("div");
   sw.style = 'position:fixed!important;bottom:45%;right:10px;z-index:999999;width:14px;height:14px;opacity:0.4;border-radius:7px;background:red';
   document.body.appendChild(sw);
   sw.addEventListener('touchmove', function(e){
    sw.style.right = sw.style.bottom = '';
    sw.style.left = (e.touches[0].clientX - 7) + 'px';
    sw.style.top = (e.touches[0].clientY - 7) + 'px';
   }, {'passive':true});
   sw.addEventListener('click', function(e){
    sw.style.background = red ? 'green' : 'red'
    red = !red;
   }, {'passive':true});
  }
 } catch(err){console.log('复制授权：', err);}
})();

```
{{< /admonition >}}



4. 最终效果

   ![复制提示](https://assets.hifo.fun/imgs/blog/2022/11/jiantieban.png)


---

> 作者: mxsix112  
> URL: https://notes.hifo.fun/clipboard/  

