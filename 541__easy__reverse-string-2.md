# Reverse String II

Given a string and an integer k, you need to reverse the first k characters for every 2k characters counting from the start of the string. If there are less than k characters left, reverse all of them. If there are less than 2k but greater than or equal to k characters, then reverse the first k characters and left the other as original.

Example:

    Input: s = "abcdefg", k = 2
    Output: "bacdfeg"

Restrictions:
  1. The string consists of lower English letters only.
  2. Length of the given string and k will in the range [1, 10000]


```JavaScript
/**
 * @param {string} s
 * @param {number} k
 * @return {string}
 */
var reverseStr = function(s, k) {
  let result = ''
  for (let i = 0; i < s.length; i += 2 * k) {
    const str = s.slice(i, i + 2 * k)
    result += str.slice(0, k).split('').reverse().join('') + str.slice(k, 2 * k)
  }
  return result
};
```