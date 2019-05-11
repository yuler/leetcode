# Valid Perfect Square

Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note: Do not use any built-in library function such as sqrt.

Example 1:

    Input: 16
    Output: true

Example 2:

    Input: 14
    Output: false


```JavaScript
/**
 * @param {number} num
 * @return {boolean}
 */
var isPerfectSquare = function(num) {
  return Math.sqrt(num) % 1 === 0
};

var isPerfectSquare = function(num) {
  if (num === 0) return true
  else if (num === 1) return true
  else return sqrt(num, 1, Math.floor(num / 2))

  function sqrt(x, l, r) {
    while (l <= r) {
      let mid = l + Math.floor((r - l) / 2)
      let square = mid ** 2
      if (square === x) return true
      else if (square <= x) return sqrt(x, mid + 1, r)
      else return sqrt(x, l, mid - 1)
    }
  }
}
```