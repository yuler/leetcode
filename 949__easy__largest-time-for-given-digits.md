# Largest Time for Given Digits

```JavaScript
/**
 * @param {number[]} A
 * @return {string}
 */
var largestTimeFromDigits = function(A) {
  let ans = -1
  for (let i = 0; i < 4; i++)
    for (let j = 0; j < 4; j++) if (j != i)
      for (let k = 0; k < 4; k++) if (k != i && k != j) {
        const l = 6 - i - j - k
        
        const hours = 10 * A[i] + A[j]
        const mins = 10 * A[k] + A[l]
        if (hours < 24 && mins < 60) {
          ans = Math.max(ans, hours * 60 + mins)
        }
      }

  return ans >= 0 ? parseInt(ans/60).toString().padStart(2, '0') + ':' + (ans%60).toString().padStart(2, '0') : ''
}
```