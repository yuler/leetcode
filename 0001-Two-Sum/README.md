# Two Sum

## Question:

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the same element twice.

### Example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## js

遇到这题，第一反应是通过 for 循环，然后加上 Array 的 `indexOf` 方法判断。
其实这种实现没问题但是, 但是这样增加算法的时间复杂度。因为 `indexOf` 的复杂度就是 O(n)。这样总体的时间复杂度就变成 O(n^2) 了。

正确思路应该是采用 `Map` 数据结构，在遍历的时候将数组的值作为key和索引作为value存储到起来，`{value: index}`。
然后每次循环的时候计算差值，查询是否在 `Map` 中存在，如果存在，返回当前索引和 `Map` 中存储的索引

时间复杂度: O(n)
空间复杂度: O(n)

[what-is-the-time-complexity-of-javascripts-array-indexof](https://stackoverflow.com/questions/19287033/what-is-the-time-complexity-of-javascripts-array-indexof)

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
const twoSum = function(nums, target) {
  const map = new Map()
  let diff
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i]
    const diff = target - num
    if (map.has(diff)) {
      return [map.get(diff), i]
    }
    map.set(num, i)
  }
}
```

## go

## rust

