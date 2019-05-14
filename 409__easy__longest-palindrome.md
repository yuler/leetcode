# Longest Palindrome

Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example "Aa" is not considered a palindrome here.

Note:
Assume the length of given string will not exceed 1,010.

Example:

    Input:
    "abccccdd"

    Output:
    7

    Explanation:
    One longest palindrome that can be built is "dccaccd", whose length is 7.


```JavaScript
/**
 * @param {string} s
 * @return {number}
 */
var longestPalindrome = function(s) {
  const map = {}
  for (let key of s) {
    map[key] = (map[key] || 0) + 1
  }
    
  let length = 0
  for (let count of Object.values(map)) {
    length += parseInt(count / 2) * 2
    if (length % 2 === 0 && count % 2 === 1) {
      length++
    }
  }
  return length
};
```