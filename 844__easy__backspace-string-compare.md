# Backspace String Compare

```JavaScript
/**
 * @param {string} S
 * @param {string} T
 * @return {boolean}
 */
var backspaceCompare = function(S, T) {
  return output(S) === output(T)
  function output(str) {
    let out = ''
    for (let i = 0; i < str.length; i++) {
      if (str[i] === '#') out = out.slice(0, out.length - 1)
      else out += str[i]
    }
    return out
  }t
};
```