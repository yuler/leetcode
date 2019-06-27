# Reverse Only Letters

```JavaScript
/**
 * @param {string} S
 * @return {string}
 */
var reverseOnlyLetters = function(S) {
  let j = S.length - 1
  let ans = ''
  for (let i = 0; i < S.length; i++) {
    if (/[a-zA-Z]/.test(S[i])) {
      while (!/[a-zA-Z]/.test(S[j]))
        j--
      ans += S[j--]
    } else {
      ans += S[i]
    }
  }
  return ans
};
```