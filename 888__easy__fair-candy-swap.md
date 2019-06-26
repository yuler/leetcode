# Fair Candy Swap

```JavaScript
/**
 * @param {number[]} A
 * @param {number[]} B
 * @return {number[]}
 */
var fairCandySwap = function(A, B) {
  const a = A.reduce((a, b) => a + b)
  const b = B.reduce((a, b) => a + b)
  const delta = parseInt((b - a) / 2)
  
  const set = new Set(B)
  
  for (const value of A) {
    if (set.has(value + delta)) {
      return [value, value + delta]
    }
  }
};
```