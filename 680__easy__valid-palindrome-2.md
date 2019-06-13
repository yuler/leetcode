# Valid Palindrome II

Given a non-empty string s, you may delete at most one character. Judge whether you can make it a palindrome.

Example 1:

    Input: "aba"
    Output: True

Example 2:

    Input: "abca"
    Output: True
    Explanation: You could delete the character 'c'.

Note:
  1. The string will only contain lowercase characters a-z. The maximum length of the string is 50000.


```JavaScript
/**
 * @param {string} s
 * @return {boolean}
 */
var validPalindrome = function(s) {
  for (let i = 0; i < s.length; i ++) {
    if (s.charAt(i) != s.charAt(s.length - 1 - i)) {
      let j = s.length - 1 - i
      return (isPalindromeRange(s, i+1, j) || isPalindromeRange(s, i, j-1))
    }
  }
  
  return true
  
  function isPalindromeRange(s, i, j) {
    for (let k = i; k <= i + (j - i) / 2; k++) {
      if (s.charAt(k) !== s.charAt(j - k + i)) return false
    }
    
    return true
  }
};
```