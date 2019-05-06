# Power of Two

Given an integer, write a function to determine if it is a power of two.

Example 1:

    Input: 1
    Output: true 
    Explanation: 2**0 = 1

Example 2:

    Input: 16
    Output: true
    Explanation: 2**4 = 16

Example 3:

    Input: 218
    Output: false


```JavaScript
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfTwo = function(n) {
  while (n === parseInt(n) && n >= 2) {
    n /= 2
  }
  return n === 1
};

var isPowerOfTwo = function(n) {
  return n > 0 && !(n & (n-1))
};
```