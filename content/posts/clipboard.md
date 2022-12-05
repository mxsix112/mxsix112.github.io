---
title: "油猴脚本Share"
subtitle: ""
date: 2022-11-01T11:17:21+08:00
draft: false
author: "mxsix112"
authorLink: ""
authorEmail: ""
description: "给网站复制增加授权&链接可点击"
keywords: "双十一,口令,骚扰"
comment: false
weight: 0

tags:
- 剪切板
- 双11
- 链接
categories:
- 记录

hiddenFromHomePage: false
hiddenFromSearch: false

summary: ""
featuredImage: "https://assets.hifo.fun/imgs/blog/2022/11/clipboard.png"

toc:
  enable: true
math:
  enable: false
seo:
  images: []

repost:
  enable: true
  url: ""

# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->

## 网站复制授权

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

{{< image src="https://assets.hifo.fun/imgs/blog/2022/11/jiantieban.png" tite="最终效果" caption="最终效果展示" height="450px" >}}


## 链接可点击

{{< admonition tip "若提示 **❗你的浏览器不支持安装插件** ，点击展开复制粘贴" true >}}

```js
// ==UserScript==
// @name        文本链接可点击
// @namespace   
// @match       *://*/*
// @grant       none
// @version     1.0
// @author      text to link
// @description 2022/11/29 13:09:30
// ==/UserScript==

var k = ".//text()[not(ancestor::" + "a form head noscript option script style title textarea".split(" ").join(") and not(ancestor::") + ")]", l = RegExp("(\\b[a-z][-+.0-9a-z]*://((([-.0-9_a-z~]|%[0-9a-f][0-9a-f]|[!$&-,:;=])*@)?(\\[(([0-9a-f]{1,4}:){6}([0-9a-f]{1,4}:[0-9a-f]{1,4}|(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5]))|::([0-9a-f]{1,4}:){5}([0-9a-f]{1,4}:[0-9a-f]{1,4}|(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5]))|([0-9a-f]{1,4})?::([0-9a-f]{1,4}:){4}([0-9a-f]{1,4}:[0-9a-f]{1,4}|(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5]))|(([0-9a-f]{1,4}:)?[0-9a-f]{1,4})?::([0-9a-f]{1,4}:){3}([0-9a-f]{1,4}:[0-9a-f]{1,4}|(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5]))|(([0-9a-f]{1,4}:){0,2}[0-9a-f]{1,4})?::([0-9a-f]{1,4}:){2}([0-9a-f]{1,4}:[0-9a-f]{1,4}|(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5]))|(([0-9a-f]{1,4}:){0,3}[0-9a-f]{1,4})?::[0-9a-f]{1,4}:([0-9a-f]{1,4}:[0-9a-f]{1,4}|(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5]))|(([0-9a-f]{1,4}:){0,4}[0-9a-f]{1,4})?::([0-9a-f]{1,4}:[0-9a-f]{1,4}|(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5]))|(([0-9a-f]{1,4}:){0,5}[0-9a-f]{1,4})?::[0-9a-f]{1,4}|(([0-9a-f]{1,4}:){0,6}[0-9a-f]{1,4})?::|v[0-9a-f]+\\.[!$&-.0-;=_a-z~]+)\\]|(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])\\.(\\d|[1-9]\\d|1\\d{2}|2[0-4]\\d|25[0-5])|([-.0-9_a-z~]|%[0-9a-f][0-9a-f]|[!$&-,;=])*)(:\\d*)?(/([-.0-9_a-z~]|%[0-9a-f][0-9a-f]|[!$&-,:;=@])*)*|/(([-.0-9_a-z~]|%[0-9a-f][0-9a-f]|[!$&-,:;=@])+(/([-.0-9_a-z~]|%[0-9a-f][0-9a-f]|[!$&-,:;=@])*)*)?|([-.0-9_a-z~]|%[0-9a-f][0-9a-f]|[!$&-,:;=@])+(/([-.0-9_a-z~]|%[0-9a-f][0-9a-f]|[!$&-,:;=@])*)*)?(\\?([-.0-9_a-z~]|%[0-9a-f][0-9a-f]|[!$&-,/:;=?@])*)?(#([-.0-9_a-z~]|%[0-9a-f][0-9a-f]|[!$&-,/:;=?@])*)?\\b|about:[a-z]+|#?[a-z0-9._%+-]+@([a-z0-9+-]+\\.)+[a-z0-9#]+\\b|\\b([a-z0-9+-]+\\.)+(ac|ad|aero|ae|af|ag|ai|al|am|an|ao|aq|arpa|ar|asia|as|at|au|aw|ax|az|ba|bb|bd|be|bf|bg|bh|biz|bi|bj|bm|bn|bo|br|bs|bt|bv|bw|by|bz|cat|ca|cc|cd|cf|cg|ch|ci|ck|cl|cm|cn|coop|com|co|cr|cu|cv|cx|cy|cz|de|dj|dk|dm|do|dz|ec|edu|ee|eg|er|es|et|eu|fi|fj|fk|fm|fo|fr|ga|gb|gd|ge|gf|gg|gh|gi|gl|gm|gn|gov|gp|gq|gr|gs|gt|gu|gw|gy|hk|hm|hn|hr|hu|id|ie|il|im|info|int|in|io|iq|ir|is|it|je|jm|jobs|jo|jp|ke|kg|kh|ki|km|kn|kp|kr|kw|ky|kz|la|lb|lc|li|lk|lr|ls|lt|lu|lv|ly|ma|mc|md|me|mg|mh|mil|mk|ml|mm|mn|mobi|mo|mp|mq|mr|ms|mt|museum|mu|mv|mw|mx|my|mz|name|na|nagoya|nc|net|ne|nf|ng|ni|nl|no|np|nr|nu|nz|om|org|pa|pe|pf|pg|ph|pk|pl|pm|pn|pro|pr|ps|pt|pw|py|qa|re|ro|rs|ru|rw|sa|sb|sc|sd|se|sg|sh|si|sj|sk|sl|sm|sn|so|sr|st|su|sv|sy|sz|tc|td|tel|tf|tg|th|tj|tk|tl|tm|tn|to|tokyo|tp|travel|tr|tt|tv|tw|tz|ua|ug|uk|um|us|uy|uz|va|vc|ve|vg|vi|vn|vu|wf|ws|xn--0zwm56d|xn--11b5bs3a9aj6g|xn--80akhbyknj4f|xn--9t4b11yi5a|xn--deba0ad|xn--g6w251d|xn--hgbk6aj7f53bba|xn--hlcj6aya9esc7a|xn--jxalpdlp|xn--kgbechtv|xn--zckzah|ye|yt|yu|za|zm|zw)(?![\\w])(/([\\w\\.\\-\\$&%/:=#~!]*\\??[\\w\\.\\-\\$&%/:=#~!]*[\\w\\-\\$/#])?)?)", "gi"); m(document.body); (new window.MutationObserver(function (c) { c.forEach(function (c) { m(c.target) }) })).observe(document.body, { childList: !0, subtree: !0 }); function m(c) { function f() { for (var c = null, e = 0; c = b.snapshotItem(d++);) { var g = c.parentNode; if (g && ("PRE" != g.tagName || !g.className) && (n(c), 50 < ++e)) return setTimeout(f, 0) } } if (!c.className || !c.className.match(/\blinkifyplus\b/)) { var b = document.evaluate(k, c, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null), d = 0; setTimeout(f, 0) } } function n(c) { var f = [], b = "", d; for (d = c; ;) { d = d.nextSibling; if (null == d) break; if ("WBR" != d.tagName) break; f.push(d); d = d.nextSibling; if (null == d || d.nodeType != Node.TEXT_NODE) { f.pop(); break } f.push(d); b += d.textContent } for (var h = c.textContent + b, e = null, g = 0; d = l.exec(h);) { null == e && (e = document.createElement("span"), e.className = "textlinkplus"); var b = d[0].replace(/\.*$/, ""), p = b.length; e.appendChild(document.createTextNode(h.substring(g, d.index))); a = document.createElement("a"); a.className = "textlinkplus"; a.appendChild(document.createTextNode(b)); 0 > b.indexOf(":/") && (0 < b.indexOf("@ftp.") || b.match(/^ftp\./) ? b = "ftp://" + b : 0 < b.indexOf("@irc.") || b.match(/^irc\./) ? b = "irc://" + b : 0 > b.indexOf(":") && 0 > b.indexOf("www.") && 0 < b.indexOf("@") ? (b = b.replace(/^#/, "").replace(/#.*/, ""), b = "mailto:" + b) : 0 != b.indexOf("about:") && (b = "http://" + b)); b = b.replace(/^(ttp:|tp:|p:|h..p:)/, "http:"); a.setAttribute("href", b); e.appendChild(a); g = d.index + p } if (e) { e.appendChild(document.createTextNode(h.substring(g, h.length))); try { f.forEach(function (b) { c.parentNode.removeChild(b) }), c.parentNode.replaceChild(e, c) } catch (q) { console.error(q), console.log(c) } } };
```

{{< /admonition >}}

{{< image src="https://assets.hifo.fun/imgs/blog/2022/12/text_to_link.png" tite="最终效果" caption="最终效果展示" >}}

### 链接可点击插件下载

> 脚本内容为Chrome 插件Text to link的JS文件，适用于无法安装插件的浏览器使用。text to link 在Chrome拓展商店原链接已Not Found。需要的自行下载。
>
> {{< link href="https://share.hifo.fun/其他/texttolink.zip" content="text to link" title="链接可点击" download="https://share.hifo.fun/%E5%85%B6%E4%BB%96/texttolink.zip" card=true >}}
>
> {{< link "https://www.cnblogs.com/xwwin/p/15244217.html" "Chrome安装本地插件" ""  true >}}
