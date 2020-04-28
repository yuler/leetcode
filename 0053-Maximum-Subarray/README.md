# Maximum Subarray

Link https://leetcode.com/problems/maximum-subarray

Difficulty: Easy

## Question:

Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

**Example:**

```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

**Follow up:**

If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

## Analysis:

**动态规划：**

子问题: dp[i] = max(dp[i - 1] + nums[i], nums[i])
初始化: max = nums[0]
从 1 开始遍历，nums[i] = dp[i], max = max(nums[i], max)

空间复杂度：O(1)

时间复杂度：O(n)

**分治法：**

我们把数组 nums 以中间的位置 m 分为左（left）右（right）两部分。那么有 left = nums[0]...nums[m - 1], right = nums[m + 1]...nums[n-1]。

最大子序列和的位置有以下三种情况：

1. 考虑中间元素nums[m], 跨越左右两部分，这里从中间元素开始，往左求出后缀最大，往右求出前缀最大, 保持连续性。
2. 不考虑中间元素，最大子序列和出现在左半部分，递归求解左边部分最大子序列和
3. 不考虑中间元素，最大子序列和出现在右半部分，递归求解右边部分最大子序列和

空间复杂度：O(1)

时间复杂度：O(n)

## JavaScript

```JavaScript
// 动态规划
const maxSubArray = nums => {
  let max = nums[0]
  for (let i = 1; i < nums.length; i++) {
    nums[i] = Math.max(nums[i - 1] + nums[i], nums[i])
    if (nums[i] > max) max = nums[i]
  }
  return max
}

// 分治法
const maxSubArray = nums => {
  return helper(nums, 0, nums.length - 1)
}

function helper(nums, left, right) {
  if (left === right) return nums[left]
  let sum = 0
  let lmax = -Number.MAX_VALUE
  let rmax = -Number.MAX_VALUE
  const middle = (left + right) >> 1
  const l = helper(nums, left, middle)
  const r = helper(nums, middle + 1, right)
  for (let i = middle; i >= left; i--) {
    sum += nums[i]
    if (sum > lmax) lmax = sum
  }
  sum = 0

  for (let i = middle + 1; i <= right; i++) {
    sum += nums[i]
    if (sum > rmax) rmax = sum
  }
  
  return Math.max(l, r, lmax + rmax)
}
```

## Go

```golang
// 动态规划
func maxSubArray(nums []int) int {
  max := nums[0]
  for i := 1; i < len(nums); i++ {
    nums[i] = Max(nums[i - 1] + nums[i], nums[i])
    if nums[i] > max {
      max = nums[i]
    }
  }
  return max
}
func Max(a, b int) int {
  if a > b {
    return a
  }
  return b
}
```

## Rust

```rust
// 动态规划
impl Solution {
  pub fn max_sub_array(nums: Vec<i32>) -> i32 {
    let mut max = nums[0];
    let mut last = nums[0];
    for i in 1..nums.len() {
      last = std::cmp::max(last + nums[i], nums[i]);
      max = std::cmp::max(last, max);
    }
    return max;
  }
}
```