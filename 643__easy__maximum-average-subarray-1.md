# Maximum Average Subarray I

Given an array consisting of n integers, find the contiguous subarray of given length k that has the maximum average value. And you need to output the maximum average value.

Example 1:

    Input: [1,12,-5,-6,50,3], k = 4
    Output: 12.75
    Explanation: Maximum average is (12-5-6+50)/4 = 51/4 = 12.75
 

Note:

  1. 1 <= k <= n <= 30,000.
  2. Elements of the given array will be in the range [-10,000, 10,000].


```JavaScript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findMaxAverage = function(nums, k) {
  let sum = 0
  for (let i = 0; i < k; i++) {
     sum += nums[i]
  }
  
  let res = sum
  for (let i = k; i < nums.length; i++) {
    sum += nums[i] - nums[i - k]
    res = Math.max(res, sum)
  }
  return res / k
};
```