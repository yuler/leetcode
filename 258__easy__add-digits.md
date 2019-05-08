# Add Digits

Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

Example:

    Input: 38
    Output: 2 
    Explanation: The process is like: 3 + 8 = 11, 1 + 1 = 2. 
                 Since 2 has only one digit, return it.

Follow up:
Could you do it without any loop/recursion in O(1) runtime?


```JavaScript
/**
 * @param {number} num
 * @return {number}
 */
var addDigits = function(num) {
  while (num >= 10) {
    num = addDigit(num)
  }

  return num

  function addDigit(n) {
    let sum = 0
    while (n != 0) {
      sum += n % 10
      n = parseInt(n / 10)
    }
    return sum
  }
};

var addDigits = function(num) {
  if (num === 0) return 0
  if (num % 9 === 0) return 9
  else return num % 9
}
```