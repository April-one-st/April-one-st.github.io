---
title: 2621. 睡眠函数
cover: /img/12.png
categories: leetCode
keywords: leetCode
banner:
  type: img
  bgurl: /img/12.png
  bannerText:
---

<!-- @format -->

### 题目

> 请你编写一个异步函数，它接收一个正整数参数 millis ，并休眠 millis 毫秒。要求此函数可以解析任何值。
>
> > 示例 1:<br>输入: millis = 100 <br>输出: 100 <br> 解释：<br>在 100ms 后此异步函数执行完时返回一个 Promise 对象
> > let t = Date.now();
> > sleep(100).then(() => {
> > &nbsp; &nbsp;console.log(Date.now() - t); // 100
> > });`
>
> > 示例 2:<br>输入: millis = 200<br>输出: 200 <br> 解释： 在 200ms 后函数执行完时返回一个 Promise 对象

提示:

- 1 <= millis <= 1000

#### 题解

```javascript
/**
 * @param {number} millis
 * @return {Promise}
 */
async function sleep(millis) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve();
    }, millis);
  });
}

/**
 * let t = Date.now()
 * sleep(100).then(() => console.log(Date.now() - t)) // 100
 */
```
