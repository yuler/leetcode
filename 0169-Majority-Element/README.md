# Majority Element

[Link](https://leetcode.com/problems/majority-element)

Difficulty: Easy

## Question

Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

**Example 1:**

```
Input: [3,2,3]
Output: 3
```

**Example 2:**

Input: [2,2,1,1,1,2,2]
Output: 2

## Analysis

采用 Boyer-Moore 投票算法。
<!-- @TODO 解释 Boyer-Moore 投票算法 -->

空间复杂度: O(1)

时间复杂度: O(n)

## JavaScript

```JavaScript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
  let count = 0
  let candidate = 0
  for (num of nums) {
    if (count = 0) {
      candidate = num
    }
    count += (num === candidate) ? 1 : -1
  }
  return candidate
};
```
