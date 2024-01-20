---
title: butterfly 魔改教程（1）
categories: blog
cover: /img/03.png
keywords: blog hexo
banner:
  type: img
  bgurl: /img/03.png
  bannerText:
---

<!-- @format -->

记录一些博客搭建过程中的魔改教程。

## 首页背景图替换为视频

1. 找到文件 themes\butterfly\layout\includes\header\index.pug

2. 添加代码（注意锁进）

```pug
<!-- 有两个 else if is_home(), 在第一个的里面直接添加就好 -->
else if is_home()
    if page.index_video ? page.index_video : theme.index_video
    video#index-video.videosy(autoplay='' loop='' muted='' __idm_id__='196610' style='object-fit:fill;width:100%;height:100%;')
        source(src=theme.index_video)
```

3. 添加主题配置文件 \_config.butterfly.yml

```yml
# 注意将 index_img 设置为false
# The banner image of home page
index_img: false # 下面添加
index_video: "your void url"
```

## 屏幕樱花效果

1.  \_config.yml 文件配置

```yml
inject:
  head:
    # - <link rel="stylesheet" href="/xxx.css">
  bottom:
    - <script src="https://cnhkbbs.github.io/staticcdn/hexo/sakura.js"></script> # 樱花动效
```

## 增加搜索功能

1. 安装插件

```shell
$ npm install hexo-generator-search --save
```

2. \_config.yml 中添加配置

```yml
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```

3. 修改 \_config.butterfly.yml 配置

```yml
local_search:
  enable: true
  preload: false
  CDN:
# 修改完后从新启动项目即可
```

## 导航栏魔改

### 搜索按钮右移

1. 修改 butterfly 主题的 themes/butterfly/layout/includes/header/nav.pug 文件

```pug
//- +表示新增代码 - 表示减少代码
//- 注意代码缩进
nav#nav
  span#blog_name
    a#site-name(href=url_for('/')) #[=config.title]

  #menus
+  !=partial('includes/header/menu_item', {}, {cache: true})
+  #nav-right
    if (theme.algolia_search.enable || theme.local_search.enable)
      #search-button
        a.site-page.social-icon.search
          i.fas.fa-search.fa-fw
+          //- span=' '+_p('search.title')
-    !=partial('includes/header/menu_item', {}, {cache: true})

    #toggle-menu
      a.site-page
        i.fas.fa-bars.fa-fw
```

2. 自定义 css 文件，并引入

```css
#nav-right {
  flex: 1 1 auto;
  justify-content: flex-end;
  margin-left: auto;
  display: flex;
  flex-wrap: nowrap;
}
```

### 鼠标移入放大效果

```css
/* 同样是自定义css文件引入主题 */
/* 去除导航栏选项中底下的蓝条 */
#nav *::after {
  background-color: transparent !important;
}

/* 导航栏菜单鼠标移入字体放大 */
#nav #site-name:hover,
#nav .menus_item:hover,
#nav #search-button:hover {
  font-size: 28px;
}
```
