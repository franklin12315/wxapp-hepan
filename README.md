## 清水河畔小程序

清水河畔的小程序，方便大家没事的时候水河畔。

之前主要在写后台，对 `js` 什么的不是很熟悉，有不对的地方希望大家提出来哈，欢迎 `PR`。

### 实现的功能

目前实现的功能主要是查看帖子信息：

1. 最新回复
1. 最近发表
1. 今日热门
1. 版块列表
1. 帖子详情
1. 用户登录和退出
1. 查看用户收藏、评论以及发表过的帖子
1. 首页和帖子详情页的分享功能，增加了分享的按钮
1. 评论功能

我发现帖子详情页面的分享给朋友的功能很有用啊，非常方便大家水河畔，哈哈。

### 待实现的功能

1. 搜索功能
1. 发表帖子

其他功能对自己来说还不是非常必要，先不实现了。。。

### 服务端

小程序中发请求需要指定域名，并且必须是使用 `https` 协议，而河畔好像没有支持，所以在自己的腾讯云服务器上运行 `nginx` 对请求进行了转发，配置文件在 `server` 文件夹下。

### 本地运行

本地运行的时候，将 `app.js` 中的 `URL` 改成下面的链接，然后在开发者工具中关闭 `https` 校验即可。

```
http://bbs.uestc.edu.cn/mobcent/app/web/index.php
```

### 已知的问题

主要在帖子详情页面，帖子的内容有几种类型，目前文本、音频、图片都可以正常查看，但是超链接和附件没有进行支持。

#### 1、超链接内容

帖子内容中以及评论中的链接只显示了文字部分，没有显示实际的 `url`。

比如河畔返回的一个链接的原始数据为：

```json
{
  "infor": "页面显示的文字内容",
  "type": "4",
  "url": "http://www.baidu.com"
}
```

在小程序里面只会显示 `infor` 信息，并且为纯文本。

#### 2、表情包

由于表情包也是一个超链接内容，而且存在排版的问题，我直接将这些表情替换成了 `[表情]`，所以小程序中看到的表情都是这个。

#### 3、附件

帖子中的附件信息没有进行展示。

#### 4、其他不重要的内容

对评论的点评内容目前无法显示，还有投票功能也没有支持。

### 参考

河畔 API 通过参考了下面几个库整理得到，这里表示感谢。

[UESTC-BBS/API-Docs](https://github.com/UESTC-BBS/API-Docs)

[XuChunH/CampusBBS](https://github.com/XuChunH/CampusBBS)

[yiyuanliu/Hepan](https://github.com/yiyuanliu/Hepan)

更多 API 信息见[这里](https://github.com/gogotanc/wxapp-hepan/issues/1)

### 截图展示

<div style="float:left;border:solid 1px 000;margin:2px;">
    <img src="images/001-index.png" width="200" height="400">
    <img src="images/002-forum.png" width="200" height="400">
    <img src="images/003-person.png" width="200" height="400">
    <img src="images/004-topic.png" width="200" height="400">
    <img src="images/005-reply.png" width="200" height="400">
    <img src="images/006-board.png" width="200" height="400">
</div>
