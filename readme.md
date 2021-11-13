@[TOC]

# 关键技术
	- pwa
	- service works

# 简介
## pwa
首先说明我是通过youtube发现的这个东西，上网一搜，居然是14 15年就出现的技术了。 

PWA（Progressive Web Apps，渐进式 Web 应用）运用现代的 Web API 以及传统的渐进式增强策略来创建跨平台 Web 应用程序。这些应用无处不在、功能丰富，使其具有与原生应用相同的用户体验优势。这组文档和指南告诉您有关 PWA 的所有信息。

## service works (简称sw)
Service Worker 是浏览器和网络之间的虚拟代理。 它们终于解决了前端开发人员多年来一直在努力解决的一些问题，其中最值得关注的是，解决了如何正确缓存网站资源并使其在离线时可用的问题。

Service Worker 运行在一个与页面 JavaScript 主线程独立的线程上，并且无权访问 DOM 结构。这引入了一种与传统 Web 编程不同的方式：它的 API 是非阻塞的，并且可以在不同的上下文之间发送和接收信息。您可分配给 Service Worker 一些任务，并通过基于 Promise 的方法在任务完成时收到结果。

它不仅仅提供离线功能，还可以做包括处理通知、在单独的线程上执行繁重的计算等事务。Service workers 非常强大，因为他们可以控制网络请求、修改网络请求、返回缓存的自定义响应，或者合成响应。


## 看效果
当打开这个网址[https://www.190otc.com/pwa/index.html](https://www.190otc.com/pwa/index.html) 的时候，chrome浏览器会有一个安装的图标，点击后，可以进行安装。
	可以通过[chrome://apps](chrme://apps)查看已经安装的apps，并且进行卸载。
	这个网址是我做测试使用的，可能有一天打不开了，可以去我的[github](https://github.com/iml6yu/pwa_demo)上下载源码，放到任何一个支持https协议的网站上部署一下。 重点，<span style="color:red;">**一定要支持https协议**</span>。
![在这里插入图片描述](https://img-blog.csdnimg.cn/23cb1142d14640cf8422a3f5b7a36ff7.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaW1sNnl1,size_20,color_FFFFFF,t_70,g_se,x_16)

安装后的效果
桌面图标效果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/e1cfbddf2b214d1bb93b57fb98972ff9.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaW1sNnl1,size_15,color_FFFFFF,t_70,g_se,x_16)

启动后的效果
![在这里插入图片描述](https://img-blog.csdnimg.cn/1b9677a2f7c64229b92ac1e854da183c.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaW1sNnl1,size_20,color_FFFFFF,t_70,g_se,x_16)


# 实现方法：
- 方法1：你是一个懒惰的人，不想看代码，只想先看看实现效果，那就去[github](https://github.com/iml6yu/pwa_demo)上下载源码，直接发布到支持https的网站上就可以了。 
- 方法二：看我下面的内容一点点介绍吧。

## 创建目录结构如下

我们先创建一个关于 PWA 的项目文件夹，
进入文件夹下我们准备一张 256x256的图片一张，作为我们的应用程序图标。
- 创建一个 index.html 文件
- 创建一个 main.css 文件
- 创建一个 manifest.json 文件
- 创建一个 sw.js 文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/eb13875a88bc4fb79a01a61faad81a64.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAaW1sNnl1,size_16,color_FFFFFF,t_70,g_se,x_16)

## 重点介绍manifest.json内容

```javascript
{
  "short_name": "190桌面系统",
  "name": "190桌面系统",
  "description": "这是一个测试网页 ©iml6yu", 
  "icons": [
    {
      "src": "logo.png",
      "type": "image/png",
      "sizes": "256x256"
    } 
  ],
  "start_url": "index.html",
  "background_color": "#3f51b5",
  "display": "standalone", 
  "theme_color": "#3f51b5" 
}
```

## 其他代码
存储在[https://github.com/iml6yu/pwa_demo](https://github.com/iml6yu/pwa_demo)上，支持下载。







> https://developer.mozilla.org/zh-CN/docs/Web/Progressive_web_apps
> https://developer.mozilla.org/zh-CN/docs/Web/Progressive_web_apps/Offline_Service_workers
> https://blog.csdn.net/lecepin/article/details/64906620?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163680249516780262574797%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=163680249516780262574797&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-3-64906620.pc_search_result_control_group&utm_term=pwa&spm=1018.2226.3001.4187
> https://blog.csdn.net/qq_32447301/article/details/82907632?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163680249516780262574797%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=163680249516780262574797&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-82907632.pc_search_result_control_group&utm_term=pwa&spm=1018.2226.3001.4187
