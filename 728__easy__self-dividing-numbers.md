# Self Dividing Numbers

A self-dividing number is a number that is divisible by every digit it contains.

For example, 128 is a self-dividing number because 128 % 1 == 0, 128 % 2 == 0, and 128 % 8 == 0.

Also, a self-dividing number is not allowed to contain the digit zero.

Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.

Example 1:

    Input: 
    left = 1, right = 22
    Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]

Note:

The boundaries of each input argument are 1 <= left <= right <= 10000.


```JavaScript
/**
 * @param {number} left
 * @param {number} right
 * @return {number[]}
 */
var selfDividingNumbers = function(left, right) {
  const ans = []
  while (left <= right) {
    if (isDividingNumber(left)) ans.push(left)
    left++
  }
  return ans
  
  function isDividingNumber(num) {
    if (num === 0) return false
    if (num >= 1 && num < 10) return true
    const nums = num.toString().split('').map(n => Number(n))
    for (let i = 0; i < nums.length; i++) {
      if (num % nums[i] !== 0) return false
    }
    return true
  }
};
```