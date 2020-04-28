# Remove Element

Link https://leetcode.com/problems/remove-element/

Difficulty: Easy

## Quesition:

Given an array nums and a value val, remove all instances of that value [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array** [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

**Example 1:**

```
Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.

It doesn't matter what you leave beyond the returned length.
```

**Example 2:**

```
Given nums = [0,1,2,2,3,0,4,2], val = 2,

Your function should return length = 5, with the first five elements of nums containing 0, 1, 3, 0, and 4.

Note that the order of those five elements can be arbitrary.

It doesn't matter what values are set beyond the returned length.
```

**Clarification:**

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by **reference**, which means modification to the input array will be known to the caller as well.

Internally you can think of this:

```
// nums is passed in by reference. (i.e., without making a copy)
int len = removeElement(nums, val);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```

## Analysis:

要求不要使用额外的数组，空间复杂度 O(1)，数组的顺序可以改变。
参考 (Remove-Duplicates-from-Sorted-Array#Analysis)[../0026-Remove-Duplicates-from-Sorted-Array#Analysis]
使用 快慢指针，slow = -1, fast = 0，使用 fast 指针遍历数组，当 target !== nums[fast]，nums[slow + 1] = nums[fast]。

空间复杂度：O(1)
时间复杂度：O(n)

## JavaScript

```JavaScript
const removeElement = function(nums, val) {
  let slow = -1
  for (let fast = 0; fast < nums.length; fast++) {
    if (val !== nums[fast]) {
      slow++
      nums[slow] = nums[fast]
    }
  }
  return slow + 1
}
```

## Go

```golang
func removeElement(nums []int, val int) int {
  slow := -1
  for fast := 0; fast < len(nums); fast++ {
    if val != nums[fast] {
      slow++
      nums[slow] = nums[fast]
    }
  }
  return slow + 1
}
```

## Rust

```rust
impl Solution {
  pub fn remove_element(nums: &mut Vec<i32>, val: i32) -> i32 {
    if nums.is_empty() {
      return 0;
    }
    let mut slow = 0;
    for fast in 0..nums.len() {
      if val != nums[fast] {
        nums[slow] = nums[fast];
        slow += 1;
      }
    }
    return slow as i32;
  }
}
```
