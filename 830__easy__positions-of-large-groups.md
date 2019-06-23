# Positions of Large Groups

```JavaScript
/**
 * @param {string} S
 * @return {number[][]}
 */
var largeGroupPositions = function(S) {
  const ans = []
  let start = 0
  for (let i = 0; i < S.length; i++) {
    if (i === S.length - 1 || S[i] !== S[i + 1]) {
      if (i - start + 1 >= 3) {
        ans.push([start, i])
      }
      start = i + 1
    }
  }
  return ans
};
```