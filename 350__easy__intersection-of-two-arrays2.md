# 350. Intersection of Two Arrays II

Given two arrays, write a function to compute their intersection.

Example 1:

    Input: nums1 = [1,2,2,1], nums2 = [2,2]
    Output: [2,2]

Example 2:

    Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
    Output: [4,9]

Note:

Each element in the result should appear as many times as it shows in both arrays.
The result can be in any order.

Follow up:

  What if the given array is already sorted? How would you optimize your algorithm?
  What if nums1's size is small compared to nums2's size? Which algorithm is better?
  What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?


```JavaScript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
  const result = []
  const map = {}
  
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
    const index = longNums.indexOf(num, map[num] || 0)
    if (index > -1) {
      map[num] = index + 1
      result.push(num)
    }
  }

  return result
};
```