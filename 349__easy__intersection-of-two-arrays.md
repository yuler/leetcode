# Intersection of Two Arrays

Given two arrays, write a function to compute their intersection.

Example 1:

    Input: nums1 = [1,2,2,1], nums2 = [2,2]
    Output: [2]

Example 2:

    Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
    Output: [9,4]

Note:

Each element in the result must be unique.
The result can be in any order.


```JavaScript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function(nums1, nums2) {
  const result = []
  const set = new Set()
  
  let shortNums, longNums
  if (nums1.length > nums2.length) {
    shortNums = nums2
    longNums = nums1
  } else {
    shortNums = nums1
    longNums = nums2
  }
  for (let i = 0; i < shortNums.length; i++) {
    const num = shortNums[i]
    if (longNums.indexOf(num) > -1) {
      if (set.has(num)) continue
      result.push(num)
      set.add(num)
    }
  }

  return result
};
```