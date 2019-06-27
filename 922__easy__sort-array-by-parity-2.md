# Sort Array By Parity II

```JavaScript
/**
 * @param {number[]} A
 * @return {number[]}
 */
var sortArrayByParityII = function(A) {
  const evens = []
  const odds = []
  for (let i = 0; i < A.length; i++) {
    const val = A[i]
    if (val % 2 === 0) {
      evens.push(val)
    } else {
      odds.push(val)
    }
  }
  
  const ans = []
  for (let i = 0; i < evens.length; i++) {
    ans.push(evens[i], odds[i])
  }
  return ans
};
```