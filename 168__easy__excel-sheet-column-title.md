# Excel Sheet Column Title

Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:

    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
    ...

Example 1:

    Input: 1
    Output: "A"

Example 2:

    Input: 28
    Output: "AB"

Example 3:

    Input: 701
    Output: "ZY"


```JavaScript
/**
 * @param {number} n
 * @return {string}
 */
var convertToTitle = function(n) {
  const chars = 'ZABCDEFGHIJKLMNOPQRSTUVWXYZ'
  const result = []
  while (n > 26) {
    result.unshift(chars[n % 26])
    n = n % 26 === 0 ? parseInt(n / 26) - 1 : parseInt(n / 26)
  }
  result.unshift(chars[n])
  return result.join('')
}

var convertToTitle = function(n) {
  if (n <= 0) return ''
  let columnTitle = ''
  while (n > 0) {
    const remainder = n % 26 === 0 ? 26 : n % 26
    n = (n - remainder) / 26
    columnTitle = String.fromCharCode('A'.charCodeAt() - 1 + remainder) + columnTitle
  }
  return columnTitle
}
```