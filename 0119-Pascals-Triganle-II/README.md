# Pascal's Triangle II

Link: https://leetcode.com/problems/pascals-triangle-ii/

Difficulty: Easy

## Question:

Given a non-negative index *k* where k ≤ 33, return the k^th index row of the Pascal's triangle.

Note that the row index starts from 0.

![Animated](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)*In Pascal's triangle, each number is the sum of the two numbers directly above it.*

**Example:**

```
Input: 3
Output: [1,3,3,1]
```

**Follow up:**

Could you optimize your algorithm to use only *O(k)* extra space?

## Analysis:

这题是上一题的 **杨辉三角** 的进阶版本。
**区别**：给的参数 k 是 0 开始的，返回的是一维数组（以 k 行元素作为数组），然后再加上了 k ≤ 33 和 空间复杂度为 **O(k)** 的要求。
上一题我们解法是通过 **动态规划**，记住上一行的运算结果，再下一行的计算的时候需要采用上一行的运算结果。
我们可以通过杨辉三角的规律（同一行，第 `i + 1` 项是第 `i` 项的 `( k - i ) /( i + 1 )` 倍）

比如：
  - 第 k 索引行的第 0 项：1
  - 第 k 索引行的第 1 项：1 * k
  - 第 k 索引行的第 2 项：1 * k * ( k - 1) / 2
  - 第 k 索引行的第 3 项：[1 * k * ( k - 1) / 2 ] * ( k - 2 ) / 3

空间复杂度：**O(n)**

时间复杂度：**O(n)**

**refs:** ![李永乐讲计算弹珠抽奖游戏的中奖概率](https://www.youtube.com/watch?v=w6HYlUNGq4I)

## JavaScript:

```JavaScript
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
  const res = new Array(rowIndex + 1)
  let index = 1
  for (let i = 0; i <= rowIndex; i++) {
    res[i] = index
    console.log(index)
    index = index * (rowIndex - i) / (i + 1)
  }
  return res
};
```
