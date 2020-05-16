# Two Sum II - Input array is sorted

[Link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted)

Difficulty: Easy

## Question

Given an array of integers that is already ***sorted in ascending order***, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

**Note:**

- Your returned answers (both index1 and index2) are not zero-based.
- You may assume that each input would have *exactly* one solution and you may not use the *same* element twice.

**Example:**

```
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
```

## Analysis

数字是已经升序排序了的，所以我们采用 Two Pointers 方法。

两个指针分别为第一个元素和最后一个元素，比较这连个数的只和与目标数字的大小。

如果比目标值小，我们将较小元素指针 +1。

如果比目标值大，我们将较大元素指针 -1。

空间复杂度: O(1)
时间复杂度: O(n)

## JavaScript

```JavaScript
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(numbers, target) {
  let i = 0;
  let j = numbers.length - 1
  while (i < j) {
    const sum = numbers[i] + numbers[j]
    if (sum === target) {
      return [i + 1, j + 1]
    } else if (sum < target) {
      i++
    } else {
      j--
    }
  }
  return []
};
```
