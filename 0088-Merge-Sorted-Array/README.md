# Merge Sorted Array

Link: https://leetcode.com/problems/merge-sorted-array

Difficulty: Easy

## Question:

Given two sorted integer arrays *nums1* and *nums2*, merge *nums2* into *nums1* as one sorted array.

**Note:**

- The number of elements initialized in nums1 and nums2 are m and n respectively.
  
- You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2.


**Example:**

```
Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]
```

## Analysis:

采用 Two Pointers 方法，定义 `first = m - 1` 和 `second = n - 1` 两个指针，然后倒序遍历。 
if `nums1[first] > nums2[second]` => `nums[index] = nums1[first] & first--`  
else => `nums[index] = nums2[second] & second--`

空间复杂度 O(1) 
时间复杂度 O(m + n)

## JavaScript

```JavaScript
const merge = function(nums1, m, nums2, n) {
  let first = m - 1
  let second = n - 1
  for (let i = m + n - 1; 1 >= 0; i--) {
    if (second < 0) {
      break
    }

    if (nums1[first] > nums2[second]) {
      nums1[i] = nums1[first]
      first--
    } else {
      nums1[i] = nums2[second]
      second--
    }
  }
}
```
