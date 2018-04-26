[TOC]

## 清水河畔小程序

清水河畔的小程序，方便大家没事的时候水河畔。之前主要在写后台，对 `js` 什么的不是很熟悉，有不对的地方希望大家提出来哈，欢迎 PR。

### 实现的功能

目前实现的功能主要是查看帖子信息：

1. 最新回复版块
2. 最近发表版块
3. 今日热门版块
4. 帖子详情和评论
5. 用户登录和退出

### 待实现的功能

1. 发表评论
2. 发表帖子
3. 搜索功能
4. 所有版块浏览

其他功能对自己来说还不是非常必要，先不实现了。。。

### 实现

使用了[有赞 UI](https://github.com/youzan/zanui-weapp)提供的组件，其实也就登录表单那里用到了，其他的内容都是自己写的，都非常的简单。

### 服务端

由于从小程序中发请求需要指定域名，并且必须是 https 协议，而河畔好像没有支持 https，所以在自己的腾讯云服务器上运行 `nginx` 对请求进行了转发，nginx 的配置文件在 `server` 文件夹下。

### 本地运行

本地运行的时候，将小程序中所有 `wx.request` 中的 `url` 改成如下的链接即可。

```
http://bbs.uestc.edu.cn/mobcent/app/web/index.php
```

