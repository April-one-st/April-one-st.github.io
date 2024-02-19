---
title: 博客搭建
cover: /img/01.png
categories: blog
keywords: blog hexo
banner:
  type: img
  bgurl: /img/01.png
  bannerText:
---

<!-- @format -->

记录下博客搭建过程，本站采用 [hexo](https://hexo.io/zh-cn/index.html) + [Hexo-Theme-Async](https://hexo-theme-async.imalun.com/) 搭建完成。

## hexo 建站

1. 安装 hexo

```bash
$ npm install hexo-cli -g
```

2. 初始化 hexo

```bash
$ hexo init
```

3. 安装依赖

```bash
$ npm install
```

4. 项目编译

```bash
$ hexo generate
# 简写
$ hexo g
```

5. 运行项目

```bash
$ hexo server
# 简写
$ hexo s
# 运行之后在本地浏览器访问 http://localhost:4000/ 即可预览
```

## 推送至 github

1. github 新建项目，项目名称必须以 `项目名.github.io` 格式命名

2. 本地生成 sshkey

```bash
$ ssh-keygen -t rsa -C "your_email"
```

3. 复制 sshkey，进入 github 绑定 sshkey(`shkey路径=》 /Users/电脑用户名/.ssh/id_rsa.pub`)

4. 安装插件

```bash
$ npm install hexo-deployer-git --save
```

5. 将 github 仓库地址复制到 config.yml 中

```yml
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: git
  # 你的博客地址
  repo: github url
  branch: master
```

6. 运行指令

```bash
# 清理缓存
$ hexo clean

# 编译
$ hexo g

# 推送
$ hexo d
```

## 主题应用

`请确保已经安装渲染器： hexo-renderer-ejs 和 hexo-renderer-less。`

```bash
$ npm install --save hexo-renderer-less hexo-renderer-ejs
```

1. 安装[主题](https://hexo-theme-async.imalun.com/)

```bash
$ npm i hexo-theme-async@latest
```

2. 启用主题

   修改根目录下 <font color=#91b859>\_config.yml</font> 文件，将主题修改为 async

```yml
$ theme: async
```

3. 配置主题 Config

- 在 hexo 目录下新建 \_config.async.yml
