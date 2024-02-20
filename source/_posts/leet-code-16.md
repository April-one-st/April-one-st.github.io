---
title: 16. 最接近的三数之和
cover: /img/08.png
categories: leetCode
keywords: leetCode
banner:
  type: img
  bgurl: /img/08.png
  bannerText:
---

<!-- @format -->

### 题目

> 给你一个长度为 n 的整数数组 nums 和 一个目标值 target。请你从 nums 中选出三个整数，使它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在恰好一个解。
>
> > 示例 1:<br>输入：nums = [-1,2,1,-4], target = 1<br>输出：2<br>解释：与 target 最接近的和是 2 (-1 + 2 + 1 = 2) 。
>
> > 示例 2:<br>输入：nums = [0,0,0], target = 1<br>输出：0

#### 题解

1. 先将数组升序排列，初始化一个最小值

2. 遍历数组，定义双指针，如果当前和更接近，更新最小值

3. 根据当前三数之和和 target 的关系，移动指针

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */

var threeSumClosest = function (nums, target) {
  // 先将nums 按升序排序
  nums.sort((a, b) => a - b);
  const len = nums.length;
  //初始化一个最小值
  let res = Number.MAX_SAFE_INTEGER;
  for (let i = 0; i < len; i++) {
    // 定义左右指针
    let left = i + 1;
    let right = len - 1;
    while (left < right) {
      //计算出当前的三数之合
      const sum = nums[i] + nums[left] + nums[right];
      //更新最小值
      if (Math.abs(sum - target) < Math.abs(res - target)) {
        res = sum;
      }
      //根据最小值和target的关系移动左右指针
      if (sum < target) {
        left++;
      } else {
        right--;
      }
    }
  }
  return res;
};
```
