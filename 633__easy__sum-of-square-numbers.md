# Sum of Square Numbers

Given a non-negative integer c, your task is to decide whether there're two integers a and b such that a ** 2 + b ** 2 = c.

Example 1:

Input: 5

    Output: True
    Explanation: 1 * 1 + 2 * 2 = 5

Example 2:

    Input: 3
    Output: False


```JavaScript
/**
 * @param {number} c
 * @return {boolean}
 */
var judgeSquareSum = function(c) {
  for (let i = 0; i * i <= c; i++) {
    const diff = Math.sqrt(c - i * i)
    if (diff == parseInt(diff)) {
      return true
    }
  }

  return false
};
```