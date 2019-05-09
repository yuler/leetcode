# Move Zeroes

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Example:

Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
Note:

You must do this in-place without making a copy of the array.
Minimize the total number of operations.


```JavaScript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
  const length = nums.length
  let count = 0
  let i = 0
  while (i < length) {
    if (nums[i + count] === 0) {
      count++
      nums[i] = nums[i + 1]
      continue
    } else {
      nums[i] = nums[i + count]
    }
    i++
  }
  nums.splice(-count, count, ...Array.from({ length: count }).fill(0))
};
```