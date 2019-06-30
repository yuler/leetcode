# Valid Mountain Array

```JavaScript
/**
 * @param {number[]} A
 * @return {boolean}
 */
var validMountainArray = function(A) {
  if (A.length < 3) return false
  
  let down = false
  for (let i = 0; i < A.length - 1; i++) {
    if (i === 0 && A[i] > A[i+1]) return false
    if (A[i] === A[i + 1]) return false
    if (down && A[i] < A[i + 1]) return false
    if (A[i] > A[i+1] && !down) {
      down = true
    }
  }
  return down
};
```