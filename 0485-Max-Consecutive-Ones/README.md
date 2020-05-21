# Max Consecutive Ones

[Link](https://leetcode.com/problems/max-consecutive-ones/)

Difficulty: Easy

## Question

Given a binary array, find the maximum number of consecutive 1s in this array.

**Example 1:**

```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```

**Note:**

- The input array will only contain `0` and `1`.
- The length of input array is a positive integer and will not exceed 10,000

## Analysis

定义一个 `max = 0` 和 `count = 0` 然后，遍历数组。

如果是 1 ，`count++`，再 `max = Max(max, count)`。

如果是 0 ，`count = 0`。

空间复杂度: O(1)

时间复杂度: O(n)

## JavaScript

```JavaScript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
  let max = 0
  let count = 0
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i]
    if (num === 1) {
      count++
      max = Math.max(max, count)
    } else {
      count = 0
    }
  }
  return max
};
```
