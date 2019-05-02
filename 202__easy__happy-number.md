# Happy Number

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

Example: 

    Input: 19
    Output: true
    Explanation: 
    12 + 92 = 82
    82 + 22 = 68
    62 + 82 = 100
    12 + 02 + 02 = 1


```JavaScript
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
  const set = new Set()
  
  while (!set.has(n)) {
    set.add(n)
    n = sum(n)
  }
  
  return n === 1
  
  function sum(n) {
    return n.toString()
      .split('')
      .reduce((acc, val) => {
        return acc + val * val
      }, 0)
  }
};
```