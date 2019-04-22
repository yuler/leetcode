# Pascal's Triangle II

Given a non-negative index k where k ≤ 33, return the kth index row of the Pascal's triangle.

Note that the row index starts from 0.

![pascal-triangle-2](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

In Pascal's triangle, each number is the sum of the two numbers directly above it.


Example:

    Input: 3
    Output: [1,3,3,1]
    Follow up:

Follow up:

Could you optimize your algorithm to use only O(k) extra space?


```JavaScript
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
  if (rowIndex === 0) return []
  if (rowIndex === 1) return [1, 1]

  const arr = getRow(rowIndex - 1)
  
  const copy = arr.slice()
  for (let i = 1, len = arr.length; i < len; i++) {
    arr[i] = copy[i - 1] + copy[i]
  }
  arr.push(1)
  return arr
};

var getRow = function(rowIndex) {
  return getPascalRow([1], 1)
  function getPascalRow(arr, row) {
    if (row === rowIndex + 1) {
      return arr
    }
    let child = []
    child.length = row
    child[0] = 1
    child[row] = 1
    for (let i = 1; i < row; i++) {
      child[i] = arr[i - 1] + arr[i]
    }
    return getPascalRow(child, row + 1)
  }
}
```