## 演示站

https://www.heson10.com/volantis

效果图：

![volantis-heson魔改版](https://7.dusays.com/2020/11/04/a3a0a83094db6.png)



## 为什么创建这个？

因为满足部分同志不愿修改主题的心愿，就把我之前用的魔改volantis放出来。

## 相对于volantis修改的功能

- 侧边栏左侧
- 上升气泡
- 热门文章（手动加）

![](https://7.dusays.com/2020/11/04/aee47db7cb65c.png)

- 商用版本fontawesome（很全）

![](https://7.dusays.com/2020/11/04/a8e55166f33dc.png)

- 集成手机微信发送短博文功能，效果如：https://www.heson10.com/volantis/bb

![](https://7.dusays.com/2020/11/04/17a3553131fa7.png)

- github底部样式（默认关闭，配置文件可修改）
 ![image-20201104133155951](C:\Users\Heson\AppData\Roaming\Typora\typora-user-images\image-20201104133155951.png)
- 彩虹标签云

![](https://7.dusays.com/2020/11/04/f5b40162c7040.png)

- 谷歌思源宋体字体（快速异步加载）

## 下载主题

```
git clone https://github.com/heson525/volantis-heson.git themes/volantis-heson
```

## 更换主题

打开根目录`_config.yml`文件

```
theme: volantis-heson
```

## 安装依赖

改根目录下的`package.json`文件

```json
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "build": "hexo generate",
    "clean": "hexo clean",
    "deploy": "hexo deploy",
    "server": "hexo server"
  },
  "hexo": {
    "version": "5.1.1"
  },
  "dependencies": {
    "hexo": "^5.1.1",
    "hexo-abbrlink": "^2.2.1",
    "hexo-deployer-git": "^2.1.0",
    "hexo-generator-archive": "^1.0.0",
    "hexo-generator-category": "^1.0.0",
    "hexo-generator-feed": "^3.0.0",
    "hexo-generator-index": "^2.0.0",
    "hexo-generator-json-content": "^4.2.3",
    "hexo-generator-tag": "^1.0.0",
    "hexo-related-popular-posts": "^5.0.1",
    "hexo-renderer-ejs": "^1.0.0",
    "hexo-renderer-marked": "^3.0.0",
    "hexo-renderer-stylus": "^2.0.0",
    "hexo-server": "^2.0.0",
    "hexo-wordcount": "^6.0.1"
  }
}

```

然后输入下面命令，本地预览

```
npm install && hexo cl && hexo g && hexo s
```

## 修改主题配置

在主题目录的config.yml中找到`☆`符号

这些都是必须修改的项目，在修改的内容在里面已经说明

## FAQ

Q1:首页文章的头图怎么添加？

A1:在md文章头部的`frontmater`里面添加`headimg: 链接地址`

Q2:怎么添加`分类`、`标签`和`说说`页面？

A2:输入命令：

```
hexo new page categories
hexo new page tags
hexo new page bb
hexo new page links          
hexo new page guestbook
```

然后分别在生成的两个index.md里的`frontmater`里面添加`layout: category`和`layout: tag`和`layout: bb`和`layout: friends`

| 命令                     | 对应模板         |
| ------------------------ | ---------------- |
| hexo new page categories | layout: category |
| hexo new page tags       | layout: tag      |
| hexo new page bb         | layout: bb       |
| hexo new page links      | layout: friends  |
| hexo new page guestbook  | 无               |

Q3:怎么调用友情链接？

A3:我用的是gitee动态调用，这样的好处是：可以直接申请审核，不用动代码加友情链接。

我得调用代码：

```
{% issues sites | api=https://gitee.com/api/v5/repos/heson525_admin/links/issues?sort=created&direction=asc&labels=active&state=open&page=1&per_page=100 | group=group:技术大佬,朋友们 %}
```

其中api要换成自己的gitee链接，我这个链接中`heson525_admin`是我的用户名，`links`是仓库名后面的`group`是分组，`active`是判断是否显示的标签。

