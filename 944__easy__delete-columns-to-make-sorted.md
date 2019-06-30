# Delete Columns to Make Sorted

```JavaScript
/**
 * @param {string[]} A
 * @return {number}
 */
var minDeletionSize = function(A) {
  let ans = 0
  
  for (let c = 0; c < A[0].length; c++) {
    for (let r = 0; r < A.length - 1; r++) {
      if (A[r][c] > A[r + 1][c]) {
        ans++
        break
      }
    }
  }
  
  return ans
};
```