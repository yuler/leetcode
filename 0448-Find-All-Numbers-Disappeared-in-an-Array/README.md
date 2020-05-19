# Find All Numbers Disappeared in an Array

[Link](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)

Difficulty: Easy

## Question

Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

**Example:**

```
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
```

## Analysis

要求，空间复杂度为 O(1)，时间复杂度为 O(n) 的算法。

我们先以某种方式标记已访问过的数组，然后再找到缺失的数字。

遍历数组，我们将 `nums[i]` 对应的索引位置的数字标记为负数，即 `nums[nums[i] - 1] * -1`。遍历的时候如果遇到 `nums[i]` 为负数，说明我们已经存在数字 `i + 1`。

最后再遍历数组，找到 > 0 的数字（即没有被访问过的索引）。

## JavaScript

```JavaScript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findDisappearedNumbers = function(nums) {
  for (let i = 0; i < nums.length; i++) {
    const num = Math.abs(nums[i])
    if (nums[num - 1] > 0) {
      nums[num - 1] = nums[num - 1] * -1
    }
  }
  
  const result = []
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i]
    if (num > 0) {
      result.push(i + 1)
    }
  }
  return result
};
```
