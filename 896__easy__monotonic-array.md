# Monotonic Array

```JavaScript
/**
 * @param {number[]} A
 * @return {boolean}
 */
var isMonotonic = function(A) {
  let step = 0
  for (let i = 1; i < A.length; i++) {
    const prev = A[i - 1]
    const val = A[i]
    if (step === 0) step = val - prev
    if (step > 0 && val < prev) {
      return false
    } 
    if (step < 0 && val > prev) {
      return false
    }
  }
  
  return true
};
```