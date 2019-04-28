# Excel Sheet Column Number

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...

Example 1:

    Input: "A"
    Output: 1


Example 2:

    Input: "AB"
    Output: 28

Example 3:

    Input: "ZY"
    Output: 701


```JavaScript
/**
 * @param {string} s
 * @return {number}
 */
var titleToNumber = function(s) {
  let sum = 0
  for (var i = 0; i < s.length; i++) {
    sum += (s[s.length - i - 1].charCodeAt() - 64) * 26 ** i
  }
  return sum
};
```