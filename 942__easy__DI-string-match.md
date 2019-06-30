# DI String Match

```JavaScript
/**
 * @param {string} S
 * @return {number[]}
 */
var diStringMatch = function(S) {
  const len = S.length
  let low = 0
  let high = len
  const ans = []
  
  for (let i = 0; i < len; i++) {
    if (S[i] === 'I') {
      ans[i] = low++
    } else {
      ans[i] = high--
    }
  }
  ans[len] = low
  return ans
};
```