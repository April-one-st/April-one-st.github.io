---
title: hexo源码 推送至 github
categories: blog
cover: /img/02.png
keywords: blog hexo github
banner:
  type: img
  bgurl: /img/02.png
  bannerText:
---

<!-- @format -->

可以将 hexo 的源码推送至 github，方便更换设备时直接拉取代码。

1. 去 github 上在博客的项目里新建一个分支 <font color=#91b859> hexo </font> ，并将其设置为默认分支。

2. 在本地新建一个文件夹，并将 hexo 分支的代码 clone 下来

3. 打开新建的文件夹，查看隐藏文件，删除掉除 <font color=#91b859> .git </font> 之外的所有文件

```bash
# mac隐藏文件查看方式,重复操作可隐藏
$ Command + Shift + .
```

4. 终端进入 hexo 下面，依次执行

```bash
$ git add .
$ git commit -m "feat: init"
$ git push origin hexo
# 此时再次进入 github 查看 hexo 分支的代码，发现已经是空的了
```

5. 将 .git 文件复制到 blog 项目的根目录下，并删除掉 <font color=#91b859> themes </font> 文件夹下的 <font color=#91b859> .git </font> 和 <font color=#91b859> .gitignore </font> 文件（包括各个主题下的也要删除，否则主题的代码推不上去）。

6. 终端进入博客根目录，依次执行

```bash
$ git add .
$ git commit -m "feat: init"
$ git push origin hexo
```

到这就已经可以了，后续可以将 github 上 hexo 分支的代码 clone 下来继续编写博客了。使用 git 管理代码，hexo 发布博客。
