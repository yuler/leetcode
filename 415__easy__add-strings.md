# Add Strings

Given two non-negative integers num1 and num2 represented as string, return the sum of num1 and num2.

Note:

  The length of both num1 and num2 is < 5100.
  Both num1 and num2 contains only digits 0-9.
  Both num1 and num2 does not contain any leading zero.
  You must not use any built-in BigInteger library or convert the inputs to integer directly.


```JavaScript
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var addStrings = function(num1, num2) {
  let max = Math.max(num1.length, num2.length)
  
  num1 = num1.padStart(max, '0')
  num2 = num2.padStart(max, '0')
  
  let result = ''
  let carry = 0
  while (max) {
    max--
    const sum = parseInt(num1[max]) + parseInt(num2[max]) + carry
    carry = sum >= 10 ? 1 : 0
    result = sum % 10 + result
  }
  
  return carry ? '1' + result : result
};
```