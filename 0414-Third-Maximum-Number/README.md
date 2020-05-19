# Third Maximum Number

[Link](https://leetcode.com/problems/third-maximum-number/)

Difficulty: Easy

## Question

Given a **non-empty** array of integers, return the **third** maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).

**Example 1:**

```
Input: [3, 2, 1]

Output: 1

Explanation: The third maximum is 1.
```

**Example 2:**

```
Input: [1, 2]

Output: 2

Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
```

Example 3:

```
Input: [2, 2, 3, 1]

Output: 1

Explanation: Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
```

## Analysis

此题目要求时间复杂度必须为 O(n)

定义三个变量 `firstMaximum`, `secondMaximum`, `thridMaximum` 分别存储对应的 第一最大值，第二最大值，第三最大值。初始值都为 -Infinity。

遍历数组，依次比较第一次最大值、第二最大值、第三最大值。如果满足条件就替换。

空间复杂度：O(1)

时间复杂度：O(n)

## JavaScript

```JavaScript
/**
 * @param {number[]} nums
 * @return {number}
 */
var thirdMax = function(nums) {
  let firstMaximum = -Infinity
  let secondMaximum = -Infinity
  let thridMaximum = -Infinity

  for (let i = 0; i < nums.length; i++) {
    const num = nums[i]
    if (num > firstMaximum) {
      thridMaximum = secondMaximum
      secondMaximum = firstMaximum
      firstMaximum = num
    } else if (num > secondMaximum) {
      thridMaximum = secondMaximum
      secondMaximum = num
    } else if (num > thridMaximum) {
      thridMaximum = num
    }
  }

  return thridMaximum === -Infinity
    ? firstMaximum
    : thridMaximum
};
```
