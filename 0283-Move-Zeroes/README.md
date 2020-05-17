# Move Zeroes

[Link](https://leetcode.com/problems/move-zeroes)

Difficulty: Easy

## Question

Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Example:**

```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

**Note:**

1. You must do this in-place without making a copy of the array.
2. Minimize the total number of operations.

## Analysis

- 空间最优，操作局部优化（双指针）

  第一个指针遍历数组 i
  第二个指针记录非零数字最后索引 j
  遍历数组遇到非零，填充非零的数字到数组中，并且 j++
  最后遍历 j 到 nums.length 填充 0

  空间复杂度: O(1)

  时间复杂度: O(n)

- 最优解
  慢指针（lastNonZeroAt）之前的所有元素都是非零的
  当前指针和慢速指针之间的所有元素都是零。
  当我们遇到一个非零元素时，我们需要交换当前指针和慢速指针指向的元素，然后前进两个指针。如果它是零元素，我们只前进当前指针。

## JavaScript

```JavaScript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
// Two Pointers
var moveZeroes = function(nums) {
  let lastNonZeroAt = 0
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i]
    if (num !== 0) {
      nums[lastNonZeroAt++] = num
    }
  }
  for (let i = lastNonZeroAt; i < nums.length; i++) {
    nums[i] = 0
  }
};
// 只遍历一次
var moveZeroes = function(nums) {
  for (let lastNonZeroAt = 0, i = 0; i < nums.length; i++) {
    if (nums[i] !== 0) {
      swap(nums, lastNonZeroAt++, i)
    }
  }
  function swap(nums, a, b) {
    const tmp = nums[a]
    nums[a] = nums[b]
    nums[b] = tmp
  }
}
```
