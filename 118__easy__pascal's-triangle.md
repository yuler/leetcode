# Pascal's Triangle

Given a non-negative integer numRows, generate the first numRows of Pascal's triangle.

![pascal's-triangle](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

In Pascal's triangle, each number is the sum of the two numbers directly above it.

Example:

    Input: 5
    Output:
    [
         [1],
        [1,1],
       [1,2,1],
      [1,3,3,1],
     [1,4,6,4,1]
    ]


```JavaScript
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
  if (numRows == 0) return []
  
  const result = Array.from({length: numRows}).map(_ => [])
  
  for (let i = 0; i < numRows; i++) {
    result[i] = Array.from({length: i + 1}).map(v => 1)
    for (let j = 1; j < i; j++) {
      if (j - 1 >= 0 && i - 1 >= 0 && i >= 2) {
        result[i][j] = result[i-1][j-1] + result[i-1][j]
      }
    }
  }
  
  return result
};

var generate = function(numRows) {
  if (numRows === 0) return []
  if (numRows === 1) return [[1]]
  if (numRows === 2) return [[1][1, 1]]

  let arr = [[1], [1, 1]]

  for (let i = 2; i < numRows; i++) {
    let temp = [1, 1]
    for (let j = 1; j < i; j++) {
      temp.splice(j, 0, arr[i - 1][j - 1] + arr[i - 1][j])
    }
    arr.push(temp)
  }

  return arr
}
```

