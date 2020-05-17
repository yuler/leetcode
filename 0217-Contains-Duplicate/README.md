# Contains Duplicate

[Link](https://leetcode.com/problems/contains-duplicate)

Difficulty: Easy

## Question

Given an array of integers, find if the array contains any duplicates.

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

**Example 1:**

```
Input: [1,2,3,1]
Output: true
```

**Example 2:**

```
Input: [1,2,3,4]
Output: false
```

**Example 3:**

```
Input: [1,1,1,3,3,4,3,2,4,2]
Output: true
```

## Analysis

使用 Hash Table 存储存储遍历的每个元素，如果遍历时候 Hash Table 存在改元素返回 true，否则遍历完数组返回 false。

空间复杂度: O(n)

时间复杂度: O(n)

## JavaScript

```JavaScript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
  const set = new Set()
  for (let i = 0; i < nums.length; i++) {
    if (set.has(nums[i])) return true
    set.add(nums[i])
  }
  return false
};
```
