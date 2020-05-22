# Fibonacci Number

[Link](https://leetcode.com/problems/fibonacci-number/)

Difficult: Easy

## Question

The **Fibonacci numbers**, commonly denoted `F(n)` form a sequence, called the **Fibonacci sequence**, such that each number is the sum of the two preceding ones, starting from `0` and `1`. That is,

```
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), for N > 1.
```

Given `N`, calculate `F(N)`.

**Example 1:**

```
Input: 2
Output: 1
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.
```

**Example 2:**

```
Input: 3
Output: 2
Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.
```

**Example 3:**

```
Input: 4
Output: 3
Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.
```

**Note:**

0 ≤ `N` ≤ 30.

## Analysis

求 **斐波那契数**。

- 第一思路想到的是采用递归方式：
  
  空间复杂度: O(n)

  时间复杂度: O(2^n)

- 记忆化自底向上的方法
  
  自底向上通过迭代计算斐波那契数的子问题并存储已计算的值，通过已计算的值进行计算。减少递归带来的重复计算。

  - 如果 N 小于等于 1，则返回 N。
  - 迭代 N，将计算出的答案存储在数组中。
  - 使用数组前面的两个斐波那契数计算当前的斐波那契数。
  - 知道我们计算到 N，则返回它的斐波那契数。

  空间复杂度: O(n)

  时间复杂度: O(n)

- 记忆化自顶向下的方法

  其实就是和第一种递归一样，支持递归的时候，创建一个 Cache 来避免重复计算

  我们先计算存储子问题的答案，然后利用子问题的答案计算当前斐波那契数的答案。我们将递归计算，但是通过记忆化不重复计算已计算的值

  - 如果 N <= 1，则返回 N
  - 调用和返回 memoize(N)
  - 如果 N 对应的斐波那契数存在，则返回。
  - 否则将计算 N 对应的斐波那契数为 memoize(N-1) + memoize(N-2)

  空间复杂度: O(n)

  时间复杂度: O(n)

- 自底向上进行迭代

  我们可以使用最小的**空间复杂度**，只存储前两位的值，来计算下一位的值。(动态规划？)

  空间复杂度: O(1)

  时间复杂度: O(n)

- 矩阵求幂

  ![公式](https://pic.leetcode-cn.com/09fd107ad5ce57b564aaae069bacd1b04fbb5033197d99305e3a45764bf07fee.png)

  使用矩阵幂运算从结果矩阵中（0，0）处的元素得到斐波那契数。

  <!-- @TODO 此处设计矩阵操作，不太熟悉。 -->

- 公式法

  使用黄金分割率计算第 `N` 个斐波那契数。[refs](https://demonstrations.wolfram.com/GeneralizedFibonacciSequenceAndTheGoldenRatio)

  空间复杂度: O(1)

  时间复杂度: O(1)

## JavaScript

```JavaScript
/**
 * @param {number} N
 * @return {number}
 */
// 递归
var fib = function(N) {
  if (N <= 1) {
    return N
  }
  return fib(N - 1) + fib(N - 2)
};
// 记忆化自底向上的方法
var fib = function(N) {
  if (N <= 1) {
    return N
  }
  return memoize(N)
};

function memoize(N) {
  const cache = {
    0: 0,
    1: 1
  }
  for (let i = 2; i <= N; i++) {
    cache[i] = cache[i - 1] + cache[i - 2]
  }
  return cache[N]
}
// 记忆化自顶向下的方法
var fib = function(N) {
  if (N <= 1) {
    return N
  }
  return memoize(N)
}
const cache = {
  0: 0,
  1: 1
}
function memoize(N) {
  if (cache[N] !== undefined) {
    return cache[N]
  }
  cache[N] = memoize(N - 1) + memoize(N - 2)
  return memoize(N)
}
// 自底向上进行迭代
var fib = function(N) {
  if (N <= 1) return N
  let first = 0
  let second = 1
  let last
  for (let i = 2; i <= N; i++) {
    last = first + second
    first = second
    second = last
  }
  return last
}
// 公式法
var fib = function(N) {
  const goldenRatio = (1 + Math.sqrt(5)) / 2
  return Math.round(Math.pow(goldenRatio, N)) / Math.sqrt(5)
}
```
