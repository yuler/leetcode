# Flipping an Image

```JavaScript
/**
 * @param {number[][]} A
 * @return {number[][]}
 */
var flipAndInvertImage = function(A) {
  const ans = new Array(A.length)
  for (let i = 0; i < A.length; i++) {
    ans[i] = A[i].reverse().map(a => 1 ^ a)
  }
  return ans
};
```