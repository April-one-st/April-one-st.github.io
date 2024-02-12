---
title: hexo-theme-async 魔改教程
categories: blog
cover: /img/05.png
keywords: blog hexo
banner:
  type: img
  bgurl: /img/05.png
  bannerText:
---

<!-- @format -->

## 添加评论功能

1. [申请 gitalk](https://github.com/gitalk/gitalk/blob/master/readme-cn.md)

2. 找到目录 ===》 `node_modules/hexo-theme-async/layout/third-party/comment` 文件夹，该文件夹为评论部分

3. 新建文件 gitalk.container.ejs 文件，并粘贴下面代码

```
<!-- 评论渲染的位置 -->
<div class="trm-card trm-scroll-animation comment-container">
    <div id="gitalk-container"></div>
</div>
<!-- 引入cdn资源 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css">
<script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>
<!-- 初始化gitalk -->
<script data-swup-reload-script>
    (function () {
        var gitalk = new Gitalk({
            clientID: ******, gitalk创建的id
            clientSecret: ********, gitalk 创建的clientSecret
            repo: 'xxxxx.github.io' , // 仓库名称
            owner: 'April-one-st', //作者
            admin: ['April-one-st'], //管理员
            id: location.pathname,      //id
            distractionFreeMode: false,  // 无干扰模式
            pagerDirection: 'last', // 评论展示的顺序
            language: 'zh-CN' //语言
            })
            gitalk.render('gitalk-container')
    })()
</script>
```

4. 找到目录 ===》 `node_modules/hexo-theme-async/layout/third-party/comment/index.ejs` 文件,添加判断(注意缩进，+号需要去掉)

```
<% let comment = theme.comment%>
<% if(comment.bComments.enable) { %>
    <%- partial('./b-comments') %>
<% } else if(comment.twikoo.enable) { %>
    <%- partial('./twikoo') %>
<% } else if(comment.giscus.enable) { %>
    <%- partial('./giscus') %>
<% } else if(comment.gitalk.enable) { %>
    <%- partial('./gitalk-container') %>
<% } %>
```

5. 一键三连

```
hexo clean && hexo g && hexo d
```
