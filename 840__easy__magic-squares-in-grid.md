# Magic Squares In Grid

```JavaScript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var numMagicSquaresInside = function(grid) {
  const r = grid.length
  const c = grid[0].length
  
  let ans = 0
  for (let i = 0; i < r - 2; ++i) {
    for (let j = 0; j < c - 2; ++j) {
      if (grid[i + 1][j + 1] != 5) continue
      if (magic(grid[i][j], grid[i][j + 1], grid[i][j + 2],
               grid[i + 1][j], grid[i + 1][j + 1], grid[i + 1][j + 2],
               grid[i + 2][j], grid[i + 2][j + 1], grid[i + 2][j + 2])
      ) {
        ans++
      }
    }
  }
  return ans
  
  function magic(...vals) {
    const set = new Set(vals)
    if (set.size !== 9) return false
    for (let i = 1; i <= 9; i++) {
      if (!set.has(i)) return false
    }
    return (vals[0] + vals[1] + vals[2] == 15 &&
      vals[3] + vals[4] + vals[5] == 15 &&
      vals[6] + vals[7] + vals[8] == 15 &&
      vals[0] + vals[3] + vals[6] == 15 &&
      vals[1] + vals[4] + vals[7] == 15 &&
      vals[2] + vals[5] + vals[8] == 15 &&
      vals[0] + vals[4] + vals[8] == 15 &&
      vals[2] + vals[4] + vals[6] == 15)
  }
};
```