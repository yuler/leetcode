# Shortest Distance to a Character

```JavaScript
/**
 * @param {string} S
 * @param {character} C
 * @return {number[]}
 */
var shortestToChar = function(S, C) {
  const result = new Array(S.length)
  for (let i = 0; i < S.length; i++) {
    const ch = S[i]
    let left = Infinity
    let right = Infinity
    if (S.slice(0, i).lastIndexOf(C) > -1) {
      left = i - S.slice(0, i).lastIndexOf(C)
    }
    
    if (S.indexOf(C, i) > -1) {
      right = S.indexOf(C, i) - i
    }
    const min = Math.min(left, right)
    result[i] = min
  }
  return result
};
```