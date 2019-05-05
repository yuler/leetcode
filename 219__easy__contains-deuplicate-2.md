# Contains Duplicate II

Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k.

Example 1:

    Input: nums = [1,2,3,1], k = 3
    Output: true

Example 2:

    Input: nums = [1,0,1,1], k = 1
    Output: true

Example 3:

    Input: nums = [1,2,3,1,2,3], k = 2
    Output: false


```JavaScript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
  return nums.some((val, index) => {
    const nextIndex = nums.indexOf(val, index + 1)
    return nextIndex !== -1 && Math.abs(nums.indexOf(val, index + 1) - index) <= k
  })
};

var containsNearbyDuplicate = function(nums, k) {
  let map = new Map()

  for (let i = 0; i < nums.length; i++) {
    if (map.has(nums[i])) {
      const index = map.get(nums[i])
      const diff = Math.abs(index - i)
      if (diff <= k) return true
    }
    map.set(nums[i], i)
  }

  return false
}
```