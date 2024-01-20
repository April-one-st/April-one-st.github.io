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

记录下博客搭建过程，本站采用 [hexo](https://hexo.io/zh-cn/index.html) + [butterfly](https://butterfly.js.org/) 搭建完成。

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

1. 创建 sshkey

```bash
$ ssh-keygen -t rsa -C "your_email"
```

2. 查看 sshkey

```bash
$ cat /Users/电脑用户名/.ssh/id_rsa.pub
```

3.复制 sshkey，进入 github 绑定 sshkey

4. 安装插件

```bash
$ npm install hexo-deployer-git --save
```

5. 运行指令

```bash
# 编译
$ hexo g

# 推送
$ hexo d
```

## 主题应用

1. 安装主题

```bash
# hexo 项目根目录终端运行
$ git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```

2. 修改根目录下 <font color=#91b859>\_config.yml</font> 文件，将主题修改为 butterfly

```yml
$ theme: butterfly
```

3. 安装插件

```bash
# hexo 项目根目录终端运行
$ npm install hexo-renderer-pug hexo-renderer-stylus --save
```

4. 在 hexo 根目录下创建 <font color=#91b859>\_config.butterfly.yml</font> 文件

5. 将主题目录的 <font color=#91b859>\_config.yml</font> 内容复制到 <font color=#91b859>\_config.butterfly.yml</font> 里面去。
