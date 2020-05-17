# Contains Duplicate II

[Link](https://leetcode.com/problems/contains-duplicate-ii)

Difficulty: Easy

## Question

Given an array of integers and an integer *k*, find out whether there are two distinct indices *i* and *j* in the array such that **nums[i] = nums[j]** and the **absolute** difference between *i* and *j* is at most *k*.

**Example 1:**

```
Input: nums = [1,2,3,1], k = 3
Output: true
```

**Example 2:**

```
Input: nums = [1,0,1,1], k = 1
Output: true
```

**Example 3:**

```
Input: nums = [1,2,3,1,2,3], k = 2
Output: false
```

## Analysis

使用 Hash Table。

- 遍历数组，对于每个元素做一下操作：
  - 在 Hash Table 中搜索当前元素，如果找到就返回 true
  - 在 Hash Table 中插入当前元素
  - 如果当前 Hash Table 的大小超过 k，删除 Hash Table 中的最旧的元素
- 返回 false

空间复杂度: O(min(n, k))

时间复杂度: O(n)

## JavaScript

```JavaScript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
  const set = new Set()
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i]
    if (set.has(num)) return true
    set.add(num)
    if (set.size > k) {
      set.delete(nums[i - k])
    }
  }
  return false
};
```
