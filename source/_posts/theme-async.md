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

# 添加cdn资源加载
cdn:
  css: ["https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css"]
  js:
    head: ["https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"]
    base:
    async:
    defer:
```

## 修改 loading 效果

1. 新建文件 `layout/preloader/page-preloader.ejs`

2. 添加代码

`添加其他样式时须将元素写在 trm-holder 元素内`

```html
<div class="trm-preloader">
  <div class="trm-holder">
    <div class="loading">
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
    </div>
  </div>
</div>
<style>
  .loading,
  .loading > div {
    position: relative;
    box-sizing: border-box;
  }

  .loading {
    display: block;
    font-size: 0;
    color: #afb42b;
  }

  .loading.la-dark {
    color: #afb42b;
  }

  .loading > div {
    display: inline-block;
    float: none;
    background-color: currentColor;
    border: 0 solid currentColor;
  }

  .loading {
    width: 10px;
    height: 10px;
  }

  .loading > div {
    position: absolute;
    width: 10px;
    height: 10px;
    margin-left: -25px;
    border-radius: 100%;
    animation: ball-running-dots-animate 2s linear infinite;
  }

  .loading > div:nth-child(1) {
    animation-delay: 0s;
  }

  .loading > div:nth-child(2) {
    animation-delay: -0.4s;
  }

  .loading > div:nth-child(3) {
    animation-delay: -0.8s;
  }

  .loading > div:nth-child(4) {
    animation-delay: -1.2s;
  }

  .loading > div:nth-child(5) {
    animation-delay: -1.6s;
  }

  .loading > div:nth-child(6) {
    animation-delay: -2s;
  }

  .loading > div:nth-child(7) {
    animation-delay: -2.4s;
  }

  .loading > div:nth-child(8) {
    animation-delay: -2.8s;
  }

  .loading > div:nth-child(9) {
    animation-delay: -3.2s;
  }

  .loading > div:nth-child(10) {
    animation-delay: -3.6s;
  }

  .loading.la-sm {
    width: 4px;
    height: 4px;
  }

  .loading.la-sm > div {
    width: 4px;
    height: 4px;
    margin-left: -12px;
  }

  .loading.la-2x {
    width: 20px;
    height: 20px;
  }

  .loading.la-2x > div {
    width: 20px;
    height: 20px;
    margin-left: -50px;
  }

  .loading.la-3x {
    width: 30px;
    height: 30px;
  }

  .loading.la-3x > div {
    width: 30px;
    height: 30px;
    margin-left: -75px;
  }

  @keyframes ball-running-dots-animate {
    0%,
    100% {
      width: 100%;
      height: 100%;
      transform: translateY(0) translateX(500%);
    }

    80% {
      transform: translateY(0) translateX(0);
    }

    85% {
      width: 100%;
      height: 100%;
      transform: translateY(-125%) translateX(0);
    }

    90% {
      width: 200%;
      height: 75%;
    }

    95% {
      width: 100%;
      height: 100%;
      transform: translateY(-100%) translateX(500%);
    }
  }
</style>
```

3. 添加配置

```yml
layout:
  page_loading: async/preloader/page-preloader
  # 其他文件配置
```

## 更改 links 结构

1. 新建文件 `layout/page/links.ejs`

2. 添加代码

```html
<div
  class="row trm-scroll-animation"
  style="margin-bottom: var(--card-bottom-card);"
>
  <div class="col-lg-12">
    <blockquote>
      <%-__('site.ruleText')%>：
      <br />
      <%- theme.user.ruleText %>
    </blockquote>
  </div>
</div>

<% if(Array.isArray(theme.links)){ %> <% theme.links.forEach(item=>{ %>
<div class="row trm-scroll-animation">
  <div class="col-lg-12">
    <h5 class="trm-title-with-divider">
      <%-__('item.title')%>
      <span data-number="02"></span>
    </h5>
  </div>
  <% item.values.forEach(item=>{ %>
  <div class="col-lg-6">
    <a href="<%- item.url %>" target="_blank" rel="nofollow">
      <div class="trm-service-icon-box trm-scroll-animation trm-p-20">
        <div class="trm-service-content">
          <div class="trm-icon">
            <img draggable="false" <%- onerror('flink') %> alt="<%- item.name
            %>" src="<%- item.image %>">
          </div>
          <div class="trm-service-text">
            <h6 class="trm-mb-10"><%- item.name %></h6>
            <div><%- item.desc ? truncate(item.desc,{length:32}) : '' %></div>
          </div>
        </div>
      </div>
    </a>
  </div>
  <%})%>
</div>
<%})%> <% } %> <% if(page.comments) { %> <%- partial(theme.layout.comment) %> <%
} %>
```

3. 添加配置

```yml
layout:
  page_links: async/page/links
  # 其他文件配置
```

4. \_data/links.yml 配置写法

```yml
# @format
- title: 博客框架
  values:
   - name: Hexo
      url: https://hexo.io/zh-tw/
      image: https://hexo.io/logo.svg
      desc: 快速、簡單且強大的網誌框架

- title: 博客主题
  values:
    - name: Hexo-Theme-Async
      url: https://hexo-theme-async.imalun.com/
      image: https://hexo-theme-async.imalun.com/logo.svg
      desc: 简洁、优雅、轻量、美观的用户界面。
```
