---
title: 14. 最长公共前缀
cover: /img/07.png
categories: leetCode
keywords: leetCode
banner:
  type: img
  bgurl: /img/07.png
  bannerText:
---

<!-- @format -->

> 编写一个函数来查找字符串数组中的最长公共前缀。如果不存在公共前缀，返回空字符串 ""。
>
> > 示例 1:<br>输入：strs = ["flower","flow","flight"]<br>输出："fl"
>
> > 示例 2:<br>输入：strs = ["dog","racecar","car"]<br>输出：""<br>解释：输入不存在公共前缀。

#### 解法 1:

```javascript
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function (strs) {
  let res = "";
  //不存在则直接返回res
  if (!strs.length) return res;
  //第一层遍历strs[0]第一个value，获取公共字符
  for (let i = 0; i < strs[0].length; i++) {
    // 第二层遍历strs，判断是否存在公共前缀，如不存在则直接返回res
    for (let j = 0; j < strs.length; j++) {
      if (strs[0][i] !== strs[j][i]) return res;
    }
    // 当strs的所有item都满足条件时，继续增加公共字符长度测试
    res += strs[0][i];
  }
  return res;
};
```

#### 解法 2:

```javascript
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function (strs) {
  // 初始直接定义为strs[0]
  let res = strs[0] ? strs[0] : "";
  for (let i = 0; i < strs.length; i++) {
    // 循环判断strs的每个item是否都包含res
    while (strs[i].indexOf(res) === -1 && res.length) {
      // 如果不包含，则将res的长度减1继续判断，直至满足条件或者res为''
      res = res.slice(0, res.length - 1);
    }
  }
  return res;
};
```
