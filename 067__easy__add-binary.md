# Add Binary

Given two binary strings, return their sum (also a binary string).

The input strings are both non-empty and contains only characters 1 or 0.

Example 1:

    Input: a = "11", b = "1"
    Output: "100"

Example 2:

    Input: a = "1010", b = "1011"
    Output: "10101"


```JavaScript
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
  const aLength = a.length
  const bLength = b.length
  let maxLength = Math.max(aLength, bLength)
  
  a = a.padStart(maxLength, '0')
  b = b.padStart(maxLength, '0')
  
  const array = Array(maxLength)
  let carry = 0
  
  while (maxLength--) {
    const sum = Number(a[maxLength]) + Number(b[maxLength]) + carry
    if (sum >= 2) {
      array[maxLength] = sum % 2
      carry = 1
    } else {
      array[maxLength] = sum
      carry = 0
    }
  }

  if (carry) {
    array.unshift(1)
  }

  return array.join('')
};

var addBinary = function(a, b) {
  const b1 = a.split('').reverse()
  const b2 = b.split('').reverse()

  const max = Math.max(b1.length, b2.length)

  let sum = ''
  let carry = 0
  let curr

  for (let i = 0; i < max; i++) {
    curr = (b1[i] ^ b2[i]) ^ carry
    carry = carry ? b1[i] | b2[i] : b1[i] & b2[i]
    sum = '' + curry + sum
  }

  if (carry) {
    sum = '1' + sum
  }

  return sum
}
```