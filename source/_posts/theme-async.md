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

<!-- ## 添加评论功能

1. [申请 gitalk](https://github.com/gitalk/gitalk/blob/master/readme-cn.md)

2. 找到目录 ===》 `node_modules/hexo-theme-async/layout/third-party/comment` 文件夹，该文件夹为评论部分

3. 新建文件 gitalk.container.ejs 文件，并粘贴下面代码

```

<div class="trm-card trm-scroll-animation comment-container">
    <div id="gitalk-container"></div>
</div>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css">
<script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>

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
``` -->

## 修改主题色

1. 创建文件 `_data/style/index.less`

2. 添加代码

```less
// 可以自己在 var-primary 方法里添加变量，去更改颜色
.var-primary(@primary: #afb42b; @primary-bg: #fcfcfe; @primary-bg2: #f4f5f7; @primary-fixed-button: #ffffff; @primary-weak: #c0ca33) {
  --primary: @primary;
  --primary-70: fade(@primary, 70%);
  --primary-50: fade(@primary, 50%);
  --primary-30: fade(@primary, 30%);
  --primary-weak: @primary-weak;
  --primary-weak-50: fade(@primary-weak, 50%);
  --theme-bg-color: @primary-bg; // 主题背景色
  --theme-bg2-color: @primary-bg2; // 主题背景色2
  --fixed-button-bg-color: @primary-fixed-button; // 侧边栏按钮颜色
}

// 亮色主题色
:root {
  .var-primary(#afb42b);
  // 暗色主题色
  &.dark {
    .var-primary(#b2cf87,#1f2623,#141e1b, #2b312c );
  }
}
```

## 搜索移动到侧栏按钮

1. 新建文件 `layout/fixed-btn.ejs`

2. 添加代码

```html
<% let is_toc = is_post() && (theme.toc.enable && page.toc !== false ) let
toc_content = ''; if(is_toc){ toc_content = toc(page.content, {list_number:
theme.toc.list_number, max_depth: theme.toc.max_depth, min_depth:
theme.toc.min_depth}); is_toc = is_toc && toc_content.length > 1; } %>
<div class="trm-fixed-container">
  <% if(theme.search.enable){ %> <% if(theme.search.type === 'local'){ %>
  <div
    id="trm-search-btn"
    class=" trm-fixed-btn trm-search-btn"
    data-title="<%- __('rightside.search') %>"
  >
    <%- icon(theme.icons.search) %>
  </div>
  <% }%> <% } %> <% if(is_toc) { %>
  <div
    class="trm-fixed-btn post-toc-btn"
    data-title="<%- __('rightside.toc_title') %>"
  >
    <%- icon(theme.icons.toc_tag) %>
  </div>
  <% } %> <% if(is_post() && theme.rightside.readmode) { %>
  <div
    class="trm-fixed-btn"
    data-title="<%- __('rightside.readmode_title') %>"
    onclick="asyncFun.switchReadMode()"
  >
    <%- icon(theme.icons.read) %>
  </div>
  <% } %> <% if(theme.rightside.aside && !page.single_column) { %>
  <div
    class="trm-fixed-btn hidden-md"
    data-title="<%- __('rightside.aside') %>"
    onclick="asyncFun.switchSingleColumn()"
  >
    <%- icon(theme.icons.arrows) %>
  </div>
  <% } %>
  <div
    id="trm-back-top"
    class="trm-fixed-btn"
    data-title="<%- __('rightside.back_to_top') %>"
  >
    <%- icon(theme.icons.back_top) %>
  </div>
</div>
```

3. \_config.async.yml 添加配置

```yml
layout:
  fixed_btn: async/fixed-btn
  # 其他文件配置
```

## 添加 gitalk 评论功能

1. [申请 gitalk](https://github.com/gitalk/gitalk/blob/master/readme-cn.md)

2. 新建文件 `layout/comment/index.ejs`

3. 添加代码

```html
<!-- 评论渲染的位置 -->
<div class="trm-card trm-scroll-animation comment-container">
  <div id="gitalk-container"></div>
</div>
<!-- 引入cdn资源 -->
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css"
/>
<script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>
<!-- 初始化gitalk -->
<script data-swup-reload-script>
  (function () {
    var gitalk = new Gitalk({
      clientID: "4850f2013499cd6d90b4",
      clientSecret: "577bf49bdbe8cfe2c12b6f8931815d775039ae90",
      repo: "April-one-st.github.io",
      owner: "April-one-st",
      admin: ["April-one-st"],
      id: location.pathname, // Ensure uniqueness and length less than 50
      distractionFreeMode: false, // Facebook-like distraction free mode
      pagerDirection: "last",
      language: "zh-CN",
    });
    gitalk.render("gitalk-container");
  })();
</script>
```

4. \_config.async.yml 添加配置

```yml
layout:
  comment: async/comment/index
  # 其他文件配置
```
