# Pascal's Triangle

Link: https://leetcode.com/problems/pascals-triangle/

Difficulty: Easy

## Question:

Given a non-negative integer numRows, generate the first numRows of Pascal's triangle.

![Animate](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)*In Pascal's triangle, each number is the sum of the two numbers directly above it.*

**Example:**

```
Input: 5
Output:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

## Analysis:

此题采用 **动态规划**
首先排除特殊情况 numRows = 1 或者 2 的时候。
然后我们初始化一个二维数组，然后每一行的数据是基于上一行生成的，并按照上面动画的方式进行填充

空间复杂度 O(numRows^2)

时间复杂度 O(numRows^2)

## JavaScript

```JavaScript
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
  if (numRows === 0) return []
  if (numRows === 1) return [[1]]
  if (numRows === 2) return [[1], [1, 1]]
  const result = [[1], [1, 1]]
  for (let i = 2; i < numRows; i++) {
    const row = [1]
    for (let j = 0; j < i - 1; j++) {
      row.push(result[i - 1][j] + result[i - 1][j + 1])
    }
    row.push(1)
    result.push(row)
  }
  return result
}
```