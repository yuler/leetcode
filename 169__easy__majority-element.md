# Majority Element

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

Example 1:

    Input: [3,2,3]
    Output: 

Example 2:

    Input: [2,2,1,1,1,2,2]
    Output: 2


```JavaScript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
  nums = nums.sort()
  return nums[parseInt(nums.length / 2)]
};

var majorityElement = function(nums) {
  let major = nums[0], count = 1
  for (var i = 1; i < nums.length; i++) {
    if (count === 0) {
      major = nums[i] 
      count++ 
    } else if (major === nums[i]) {
      count++ 
    } else {
      count--
    }
  }
  return major
}
```