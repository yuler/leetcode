# Longest Continuous Increasing Subsequence

Given an unsorted array of integers, find the length of longest continuous increasing subsequence (subarray).

Example 1:

    Input: [1,3,5,4,7]
    Output: 3
    Explanation: The longest continuous increasing subsequence is [1,3,5], its length is 3. 
    Even though [1,3,5,7] is also an increasing subsequence, it's not a continuous one where 5 and 7 are separated by 4. 

Example 2:

    Input: [2,2,2,2,2]
    Output: 1
    Explanation: The longest continuous increasing subsequence is [2], its length is 1. 

Note: Length of the array will not exceed 10,000.


```JavaScript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findLengthOfLCIS = function(nums) {
  let ans = 0
  let anchor = 0
  for (let i = 0; i < nums.length; i++) {
    if (i > 0 && nums[i - 1] >= nums[i]) anchor = i
    ans = Math.max(ans, i - anchor + 1)
  }
  return ans
};
```