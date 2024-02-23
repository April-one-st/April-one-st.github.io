---
title: 2618. 检查是否是类的对象实例
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

> 请你编写一个函数，检查给定的值是否是给定类或超类的实例。可以传递给函数的数据类型没有限制。例如，值或类可能是 undefined 。

> > 示例 1:<br>输入: func = () => checkIfInstance(new Date(), Date) <br>输出: true <br> 解释：根据定义，Date 构造函数返回的对象是 Date 的一个实例。
>
> > 示例 2:<br>输入: func = () => { class Animal {}; class Dog extends Animal {}; return checkIfInstance(new Dog(), Animal); }<br>输出: true <br> 解释： Dog 是 Animal 的子类。因此，Dog 对象同时是 Dog 和 Animal 的实例。
>
> > 示例 3:<br>输入: func = () => checkIfInstance(Date, Date)<br>输出: false <br> 解释：日期的构造函数在逻辑上不能是其自身的实例。
>
> > 示例 4:<br>输入: func = () => checkIfInstance(5, Number)<br>输出: true <br> 解释： 5 是一个 Number。注意，"instanceof" 关键字将返回 false。

#### 题解一

- 如果没有 obj 或者 classFunction 则直接返回 false
- 使用 Object 将 obj 转为对象类型，使用 instanceof 判断 obj 是否在 classFunction 实例上

```javascript
/**
 * @param {*} obj
 * @param {*} classFunction
 * @return {boolean}
 */
var checkIfInstanceOf = function (obj, classFunction) {
  if (obj === null || obj === undefined || !(classFunction instanceof Function))
    return false;
  return Object(obj) instanceof classFunction;
};
```

#### 题解二

- 递归手动实现 instanceof

```javascript
/**
 * @param {*} obj
 * @param {*} classFunction
 * @return {boolean}
 */
var checkIfInstanceOf = function (obj, classFunction) {
  if (
    obj === null ||
    obj === undefined ||
    classFunction === null ||
    classFunction === undefined
  )
    return false;
  let pro = obj.__proto__;
  while (pro && pro !== classFunction.prototype) {
    pro = pro.__proto__;
  }
  return pro === classFunction.prototype;
};
```
