# Search Insert Position

Link: https://leetcode.com/problems/search-insert-position/

Difficulty: Easy

## Question:

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

**Example 1:**

```
Input: [1,3,5,6], 5
Output: 2
```

**Example 2:**

```
Input: [1,3,5,6], 2
Output: 1
```

**Example 3:**

```
Input: [1,3,5,6], 7
Output: 4
```

**Example 4:**

```
Input: [1,3,5,6], 0
Output: 0
```

## Analysis:

因为数组是有序的，所以使用 Binary Search 方法。

定义 left = 0 和 right = nums.length - 1, 
然后求 middle = (left + right) / 2。
如果 nums[middle] == target 那么返回 middle, 
如果 nums[middle] < target, left = middle + 1, 
如果 nums[middle] > target right = middle - 1,
然后再求 middle 的值，直到 left > right 才结束。

空间复杂度：O(1)
时间复杂度：O(logN)

## JavaScript

```JavaScript
const searchInsert = function(nums, target) {
  let left = 0
  let right = nums.length - 1

  while (left <= right) {
    const middle = parseInt((left + right) / 2)
    if (nums[middle] < target) {
      left = middle + 1
    } else if (nums[middle] > target) {
      right = middle - 1
    } else {
      return middle
    }
  }

  return left
}
```

## Go

```golang
func searchInsert(nums []int, target int) int {
  left := 0
  right := len(nums) - 1
  for ; left <= right ; {
    middle := (left + right) / 2
    if nums[middle] == target {
      return middle
    } else if nums[middle] < target {
      left = middle + 1
    } else {
      right = middle - 1
    }
  }
  return left
}
```

## Rust

```rust
impl Solution {
  pub fn search_insert(nums: Vec<i32>, target: i32) -> i32 {
    let mut left = 0i32;
    let mut right = nums.len() as i32 - 1;
    while left <= right {
      let mut middle = (left + right) / 2;  
      if nums[middle as usize] == target {
        return middle;
      } else if (nums[middle as usize] < target) {
        left = middle + 1;
      } else {
        right = middle - 1;
      }
    }
    return left;
  }
}
```
