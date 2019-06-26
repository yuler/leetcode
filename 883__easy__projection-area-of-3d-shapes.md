# Projection Area of 3D Shapes

```JavaScript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var projectionArea = function(grid) {
  const length = grid.length
  let ans = 0
  
  for (let i = 0; i < length; i++) {
    let row = 0
    let col = 0
    for (let j = 0; j < length; j++) {
      if (grid[i][j] > 0) ans++
      row = Math.max(row, grid[i][j])
      col = Math.max(col, grid[j][i])
    }
    ans += row + col
  }
  
  return ans
};
```