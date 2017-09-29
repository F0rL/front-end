>这是一道非常经典的面试题，需要对网络应用是如何工作有一个层次化的认知，涉及到浏览器、HTTP协议、网络服务器等相关知识。在这里只发表下个人初步的理解。

* __在浏览器地址栏输入目标网站的URL__
例如：  **https://www.baidu.com/**
![](http://upload-images.jianshu.io/upload_images/8120037-7c8959f7101b7ec2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600) 其中，*https://* 代表使用ssl传输的超文本传输协议，*www.baidu.com* 代表域名。
* __域名解析，查找域名对应的IP地址__
1.浏览器缓存——浏览器会缓存[DNS](https://baike.baidu.com/item/dns/427444?fr=aladdin)记录一段时间。
2.系统缓存——如果在浏览器缓存里没有找到需要的记录，浏览器会调用系统缓存中的记录（windows系统存储在host文件中）。
3.路由器缓存——将查询请求发向路由器，一般会有自己的DNS缓存。
4.ISP DNS 缓存——即向互联网服务提供商（电信、联通等）查找。
5.如果经历以上四步还无法找到对应IP，则向根域名服务器查找域名对应IP地址。根域名服务器把请求转发到下一级，直到找到对应IP。

* __与服务器建立连接并给web服务器发送一个HTTP请求__
浏览器根据连接到web服务器（一般为[TCP/IP协议](https://baike.baidu.com/item/TCP%2FIP%E5%8D%8F%E8%AE%AE/212915?fr=aladdin)），向服务器发送请求，发送请求的过程中，浏览器会向Web服务器以*Stream(流)*的形式传输数据，告诉Web服务器要访问服务器里面的哪个Web应用下的Web资源。
* __服务器处理请求__
服务器（常见的有 [Apache](https://baike.baidu.com/item/apache/6265?fr=aladdin)、[Nginx](https://baike.baidu.com/item/nginx/3817705?fr=aladdin)、IIS、Lighttpd）接收到浏览器传输的数据后，开始解析接收到的数据，生成[HTML](https://baike.baidu.com/item/HTML/97049?fr=aladdin)文件并返回给浏览器。![](http://upload-images.jianshu.io/upload_images/8120037-3803773b8fd6792a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/400)
* __浏览器处理__
*HTML*字符串被浏览器接受后被一句句读取解析。
解析到*link*标签后重新发送请求获取[css](https://baike.baidu.com/item/CSS/5457?fr=aladdin)
解析到*script*标签后发送请求获取[js](https://baike.baidu.com/item/javascript/321142?fr=aladdin&fromid=10687961&fromtitle=js)，并执行代码
解析到*img*标签后发送请求获取图片资源
浏览器根据*HTML*和*CSS*计算得到渲染树，绘制到屏幕上，*js*会被执行。