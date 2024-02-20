---
title: 204. 计数质数
cover: /img/08.png
categories: leetCode
keywords: leetCode
banner:
  type: img
  bgurl: /img/08.png
  bannerText:
---

<!-- @format -->

`质数（Prime Number）是指大于 1 的自然数中，除了 1 和自身外，不能被其他自然数整除的数。换句话说，质数只能被 1 和它本身整除，没有其他的正因数。`

> 给定整数 n ，返回 所有小于非负整数 n 的质数的数量 。
>
> > 示例 1:<br>输入: n = 10 <br>输出: 4 <br> 解释：小于 10 的质数一共有 4 个, 它们是 2, 3, 5, 7 。
>
> > 示例 2:<br>输入: n = 0<br>输出: 0
>
> > 示例 3:<br>输入: n = 1<br>输出: 0

#### 解法一

- 暴力解法直接遍历`该方法官方提示超时😭`

```javascript
// 判断一个数是不是质数
// Math.sqrt(number) 是 JavaScript 中 Math 对象的一个方法，用于返回一个数的平方根。
function isPrime(number) {
  if (number <= 1) {
    return false; // 质数必须大于 1
  }

  // 循环检查从 2 到 number - 1 的所有可能的因数
  for (let i = 2; i <= Math.sqrt(number); i++) {
    if (number % i === 0) {
      return false; // 如果能被整除，则不是质数
    }
  }

  return true; // 如果不能被任何数整除，则是质数
}

/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function (n) {
  let res = 0;
  for (let i = 2; i < n; ++i) {
    res += isPrime(i);
  }
  return res;
};
```

#### 埃氏筛

1. 初始化一个长度为 n 的布尔数组（或者称为标记数组），数组中的每个元素都被初始化为 true，表示对应的索引数是质数。

2. 从第一个质数 2 开始，遍历数组中从 2 开始的所有数字。如果某个数字的值为 true，说明它是质数，则将它的所有倍数标记为 false，因为它们不是质数。

3. 继续遍历下一个未被标记为 false 的数字，重复第二步操作，直到遍历到数组的末尾。

4. 最后，数组中仍然为 true 的索引即为质数。

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function (n) {
  let res = 0;
  const arr = new Array(n).fill(true);
  for (let i = 2; i < n; i++) {
    if (arr[i]) {
      res++;
      for (let j = i * i; j <= n; j += i) {
        arr[j] = false;
      }
    }
  }
  return res;
};
```
