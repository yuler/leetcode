# K-diff Pairs in an Array

[Link](https://leetcode.com/problems/k-diff-pairs-in-an-array/)

Difficult: Easy

## Question

Given an array of integers and an integer **k**, you need to find the number of **unique** k-diff pairs in the array. Here a **k-diff** pair is defined as an integer pair (i, j), where **i** and **j** are both numbers in the array and their [absolute difference](https://en.wikipedia.org/wiki/Absolute_difference) is **k**.

**Example 1:**

```
Input: [3, 1, 4, 1, 5], k = 2
Output: 2
Explanation: There are two 2-diff pairs in the array, (1, 3) and (3, 5).
Although we have two 1s in the input, we should only return the number of unique pairs.
```

**Example 2:**

```
Input:[1, 2, 3, 4, 5], k = 1
Output: 4
Explanation: There are four 1-diff pairs in the array, (1, 2), (2, 3), (3, 4) and (4, 5).
```

**Example 3:**

```
Input: [1, 3, 1, 5, 4], k = 0
Output: 1
Explanation: There is one 0-diff pair in the array, (1, 1).
```

**Note:**

- The pairs (i, j) and (j, i) count as the same pair.
- The length of the array won't exceed 10,000.
- All the integers in the given input belong to the range: [-1e7, 1e7].

空间复杂度: O(n)

时间复杂度: O(n)

## Solution

遍历数组，将每个数组项 `num` 保存到对应的 Map 对象({[`num`]: value })中，`value` 对应 `num` 出现的次数。

在遍历这个 Map 对应。

- 如果 `k < 0` 的时候，直接返回 0
- 如果 `k == 0` 的时候，只需要 `num` 位置上大于 2 的
- 如果 `k != 0` 的时候，只需要 Map 对象上有 `num + k` 这个 Key

### JavaScript

```JavaScript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findPairs = function(nums, k) {
  if (k < 0) return 0
  let count = 0
  const map = new Map()

  for (const num of nums) {
    map.set(num, (map.has(num) || 0) + 1)
  }

  for (const key of map.keys()) {
    if (k === 0) {
      if (map.get(key) >= 2) {
        count++
      }
    } else {
      if (map.has(key + k)) {
        count++
      }
    }
  }
  return count
};
```
