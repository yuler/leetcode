# Smallest Range I

```JavaScript
/**
 * @param {number[]} A
 * @param {number} K
 * @return {number}
 */
var smallestRangeI = function(A, K) {
  let min = A[0]
  let max = A[0]
  for (const val of A) {
    min = Math.min(min, val)
    max = Math.max(max, val)
  }
  return Math.max(0, max - min - 2 * K)
};
```