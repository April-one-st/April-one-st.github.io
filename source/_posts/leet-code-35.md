---
title: 35. 搜索插入位置
cover: /img/06.png
categories: leetCode
keywords: leetCode
banner:
  type: img
  bgurl: /img/06.png
  bannerText:
---

<!-- @format -->

### 题目

> 给定一个排序的整数数组 nums 和一个整数目标值 target ，请在数组中找到 target ，并返回其下标。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。请必须使用时间复杂度为 `O(log n)` 的算法。
>
> > 示例 1:<br>输入: nums = [1,3,5,6], target = 5 <br>输出: 2
>
> > 示例 2:<br>输入: nums = [1,3,5,6], target = 2<br>输出: 1

#### 解法 1

直接遍历所有元素

```javascript
var searchInsert = function (nums, target) {
  // 如果没有则遍历nums
  for (let i = 0; i < nums.length; i++) {
    // 当target 等于当前值，则直接返回index
    if (target === nums[i]) {
      return i;
    }
    // 当target 小于当前值时，则插入到当前的位置，并返回index
    if (target < nums[i]) {
      nums.splice(i, 0, target);
      return i;
    }
    // 当遍历结束，target仍然大于所有值时，则插入到nums最后，并返回index
    if (i === nums.length - 1 && target > nums[i]) {
      nums.push(target);
      return i + 1;
    }
  }
};
```

#### 解法 2

1. 定义起始和结束坐标（left,right）
2. 每次都根据起始和结束坐标查找中间坐标位置(mid)
3. 如果中间坐标等于目标元素，则直接返回
   - 如果中间坐标大于目标元素，则 right 左移
   - 如果中间坐标小于目标元素，则 left 右移
4. 重复上述步骤，知道找到目标元素位置

```javascript
var searchInsert = function (nums, target) {
  let left = 0;
  let right = nums.length - 1;
  let result = nums.length;

  while (left <= right) {
    let mid = left + Math.floor((right - left) / 2);
    if (target <= nums[mid]) {
      result = mid;
      right = mid - 1;
    } else if (target > nums[mid]) {
      left = mid + 1;
    }
  }
  return result;
};
```
