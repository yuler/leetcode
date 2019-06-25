# Transpose Matrix

```JavaScript
/**
 * @param {number[][]} A
 * @return {number[][]}
 */
var transpose = function(A) {
  const row = A.length;
  const col = A[0].length
  const result = new Array(col)
  for (let r = 0; r < row; r++) {
    for (let c = 0; c < col; c++) {
      if (!result[c]) result[c] = []
      result[c][r] = A[r][c]
    }
  }
  
  return result
};
```