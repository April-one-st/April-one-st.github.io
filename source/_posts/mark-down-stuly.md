---
title: Markdown 语法学习 （基本语法）
categories: Markdown
cover:
keywords: Markdown Study
banner:
  type: img
  bgurl:
  bannerText:
---

<!-- @format -->

学习 markdown 语法，[官网地址](https://markdown.com.cn/intro.html)

## 标题语法

创建标题，可以在 title 前面添加 #。 #的数量代表了标题的级别

| Markdown 语法  | 预览效果                          | HTML 语法｜        |
| -------------- | --------------------------------- | ------------------ |
| # level 1      | <h1>level 1</h1>                  | \<h1>level 1\</h1> |
| ## level 2     | <h2 class="test-h2"> level 2</h2> | \<h2>level 2\</h2> |
| ### level 3    | <h3> level 3</h3>                 | \<h3>level 3\</h3> |
| #### level 4   | <h4 class="test-h4"> level 4</h4> | \<h4>level 4\</h4> |
| ##### level 5  | <h5 class="test-h5"> level 5</h5> | \<h5>level 5\</h5> |
| ###### level 6 | <h6 class="test-h6"> level 6</h6> | \<h6>level 6\</h6> |

## 段落

多个段落之间使用空白行隔开

| Markdown 语法                                                                                              | 预览效果                                                                                                   | HTML 语法｜                                                                                                           |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| <p>I really like using Markdown.</p> <p>I think I'll use it to format all of my documents from now on.</p> | <p>I really like using Markdown.</p> <p>I think I'll use it to format all of my documents from now on.</p> | \<p>I really like using Markdown.\</p><br/> \<p>I think I'll use it to format all of my documents from now on.\</p>｜ |

## 换行语法

在一行的末尾添加两个或多个空格，然后按回车键,即可创建一个换行(\<br>)。

| Markdown 语法                                                  | 预览效果                                                       | HTML 语法                                                                  |
| -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------------------- |
| <p>This is the first line.<br>And this is the second line.</p> | <p>This is the first line.<br>And this is the second line.</p> | \<p>This is the first line.<br>\<br> <br>And this is the second line.\</p> |

## 强调语法

### 粗体

可以在内容前后添加两个\*\*xxx\*\* 或者 \_\_xxx\_\_

| Markdown 语法                  | 预览效果                   | HTML 语法｜                               |
| ------------------------------ | -------------------------- | ----------------------------------------- |
| I just love \*\*bold text\*\*. | I just love **bold text**. | I just love \<strong>bold text\</strong>. |
| I just love\_\_bold text\_\_.  | I just love **bold text**. | I just love \<strong>bold text\</strong>. |

### 斜体

同粗体，但是前后各添加一个\* 或者一个\_

### 粗体和斜体

同时实现粗体和斜体 前后各添加三个\*\*\*或者\_\_\_

## 引用语法

`本博客已对该样式做了修改，原本样式可参考`[官网](https://markdown.com.cn/basic-syntax/blockquotes.html)

语法： 在段落前面添加一个 > 符号

```
> Dorothy followed her through many of the beautiful rooms in her castle.
```

渲染效果

> Dorothy followed her through many of the beautiful rooms in her castle.

**多个段落的引用**

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

`效果预览`

> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

**嵌套引用**

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

`效果预览`

> Dorothy followed her through many of the beautiful rooms in her castle.
>
> > The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

**带有其他元素块的引用**

```
> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.
```

`效果预览`

> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>   _Everything_ is going according to **plan**.

## 列表语法

### 有序列表

| Markdown 语法                                                      | 预览效果                                                           | HTML 语法                                                                                                             |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| 1. First item<br>2. Second item<br>3. Third item<br>4. Fourth item | 1. First item<br>2. Second item<br>3. Third item<br>4. Fourth item | \<ol><br>\<li>First item\</li><br>\<li>Second item\</li><br>\<li>Third item\</li><br>\<li>Fourth item\</li><br>\</ol> |

### 无序列表

` 本博客已对该样式做了修改，原本样式可参考`[官网](https://markdown.com.cn/basic-syntax/lists.html)

| Markdown 语法                                                       | 预览效果                                                                                                    | HTML 语法                                                                                                             |
| ------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| \- First item<br> \- Second item<br>\- Third item<br>\- Fourth item | <ul><br><li>First item</li><br><li>Second item</li><br><li>Third item</li><br><li>Fourth item</li><br></ul> | \<ul><br>\<li>First item\</li><br>\<li>Second item\</li><br>\<li>Third item\</li><br>\<li>Fourth item\</li><br>\</ul> |

## 代码语法

要将单词或短语表示为代码，将其包裹在反引号 (`) 中。

| Markdown 语法                         | 预览效果                                       | HTML 语法｜                                      |
| ------------------------------------- | ---------------------------------------------- | ------------------------------------------------ |
| At the command prompt, type \`nano\`. | At the command prompt, type <code>nano</code>. | At the command prompt, type \<code>nano\</code>. |

## 分割线语法

在单独一行上使用三个或多个星号 (\*\*\*)、破折号 (---) 或下划线 (\_\_\_) ，并且不能包含其他内容。

`效果预览`：

Try to put a blank line before...

---

...and after a horizontal rule.

## 链接语法

\[链接标题\]\(链接地址\)。

## 图片语法

\!\[图片名称\]\(图片地址\)
