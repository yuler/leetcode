# Peak Index in a Mountain Array

```JavaScript
/**
 * @param {number[]} A
 * @return {number}
 */
var peakIndexInMountainArray = function(A) {
  let i = 0
  while (A[i] < A[i + 1]) i++
  return i
};
```