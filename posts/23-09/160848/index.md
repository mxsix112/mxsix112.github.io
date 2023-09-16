# Alist配置Webdav的问题



## 问题
Alist 是一个支持多种存储的文件列表程序，它支持部分云盘服务以及相关云存储，支持挂载Webdav。通过使用 Nginx 反向代理网站时，出现是第三方文件管理器 Webdav 服务无法进行文件和文件夹的<font color="#ff0000">修改、移动</font>等操作。经过查询，发现了这个问题的原因。
	1. WebDAV 的请求头存在自定义字段 “Destination”。在反向代理时，nginx 默认不会将 “Destination” 字段中 “https://in-naswebdav.yourdomain.com/...” 的 “https” 替换为 “http”，后台的 NAS 因而无法定位目标地址，进而出现 502 等一系列问题。
	2. 其次，WebDAV 对文件夹的创建以及文件和文件夹的重命名操作，其请求路径需以 “/” 结尾，而通过 nginx 的 url 往往缺少结尾的 “/”，导致操作失败。 

## 方法
使用 nginx 搭配模块 <span style="background:#40a9ff"><font color="#ffffff">headers-more-nginx-module</font></span>。以下步骤基于宝塔面板操作进行
1. 将已安装的nginx 进行卸载操作
2. 重新安装,在模块参数中添加
```
--add-module=/www/server/ngx_modules/headers_more
```
3. 前置参数中添加
```
mkdir /www/server/ngx_modules
cd /www/server/ngx_modules
wget https://github.com/openresty/headers-more-nginx-module/archive/refs/tags/v0.33.zip
unzip v0.33.zip
rm v0.33.zip
mv headers-more-nginx-module-0.33 headers_more
```

## 参考文章
1. [校园网环境下软路由及 NAS 的搭建](https://blog.jaspirit.cc/posts/69f0ff47/#4-3-%E5%B0%86NAS%E6%9C%8D%E5%8A%A1%E8%BF%9B%E8%A1%8CHTTPS%E5%8A%A0%E5%AF%86)  -Ja Spirit
2. [宝塔 Nginx 编译安装 headers_more 模块](https://blog.csdn.net/lizhihua0625/article/details/126098387) -Puamac

---

> 作者: mxsix112  
> URL: https://blog.hifo.fun/posts/23-09/160848/  

