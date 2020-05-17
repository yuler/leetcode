# Rotate Array

[Link](https://leetcode.com/problems/rotate-array)

Difficulty: Easy

## Question

Given an array, rotate the array to the right by *k* steps, where *k* is non-negative.

**Follow up:**

- Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.
- Could you do it in-place with O(1) extra space?

**Example 1:**

```
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```

**Example 2:**

```
Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation:
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```

**Constraints:**

- 1 <= nums.length <= 2 * 10^4
- It's guaranteed that nums[i] fits in a 32 bit-signed integer.
- k >= 0

## Analysis

此题有多种解法，空间复杂度为 O(1) 的解法是：

1. 我们首先将所有元素反转，
2. 然后翻转前 k 个元素，
3. 再反转后面 n - k 个元素，

假设 n=7 且 k = 3

```
原始数组                  : 1 2 3 4 5 6 7
反转所有数字后             : 7 6 5 4 3 2 1
反转前 k 个数字后          : 5 6 7 4 3 2 1
反转后 n-k 个数字后        : 5 6 7 1 2 3 4 --> 结果
```

空间复杂度: O(1)

时间复杂度: O(n)

## JavaScript

```JavaScript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
  k %= nums.length
  reserve(nums, 0, nums.length - 1)
  reserve(nums, 0, k)
  reserve(nums, k, nums.length - 1)
  function reserve(nums, start, end) {
    while (start < end) {
      const tmp = nums[start]
      nums[start] = nums[end]
      nums[end] = tmp
      start++
      end--
    }
  }
};
```
