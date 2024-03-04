---
title: 2620. 计数器
cover: /img/11.png
categories: leetCode
keywords: leetCode
banner:
  type: img
  bgurl: /img/11.png
  bannerText:
---

<!-- @format -->

### 题目

> 给定一个整型参数 n，请你编写并返回一个 counter 函数。这个 counter 函数最初返回 n，每次调用它时会返回前一个值加 1 的值 ( n , n + 1 , n + 2 ，等等)。

> > 示例 1:<br>输入: n = 10<br>["call","call","call"] <br>输出: [10,11,12] <br> 解释：counter() = 10 // 第一次调用 counter()，返回 n。<br>counter() = 11 // 返回上次调用的值加 1。<br>counter() = 12 // 返回上次调用的值加 1。
>
> > 示例 2:<br>输入: n = -2<br> ["call","call","call","call","call"]<br>输出: [-2,-1,0,1,2] <br> 解释： counter() 最初返回 -2。然后在每个后续调用后增加 1。

提示:

- -1000 <= n <= 1000
- 0 <= calls.length <= 1000
- calls[i] === "call"

#### 题解

- 利用闭包的原理

```javascript
/**
 * @param {number} n
 * @return {Function} counter
 */
var createCounter = function (n) {
  return function () {
    return n++;
  };
};
```
