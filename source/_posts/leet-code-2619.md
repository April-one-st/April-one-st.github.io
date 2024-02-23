---
title: 2619. 数组原型对象的最后一个元素
cover: /img/10.png
categories: leetCode
keywords: leetCode
banner:
  type: img
  bgurl: /img/10.png
  bannerText:
---

<!-- @format -->

### 题目

> 请你编写一段代码实现一个数组方法，使任何数组都可以调用 array.last() 方法，这个方法将返回数组最后一个元素。如果数组中没有元素，则返回 -1 。<br>你可以假设数组是 JSON.parse 的输出结果。

> > 示例 1:<br>输入: nums = [null, {}, 3] <br>输出: 3 <br> 解释：调用 nums.last() 后返回最后一个元素： 3。
>
> > 示例 2:<br>输入: nums = []<br>输出: -1 <br> 解释： 因为此数组没有元素，所以应该返回 -1。

提示:

- arr 是一个有效的 JSON 数组
- 0 <= arr.length <= 1000

#### 题解:

```javascript
/**
 * @return {null|boolean|number|string|Array|Object}
 */
Array.prototype.last = function () {
  return this.length ? this[this.length - 1] : -1;
};
```
