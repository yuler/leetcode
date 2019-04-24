# Valid Palindrome

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Note: For the purpose of this problem, we define empty string as valid palindrome.

Example 1:

    Input: "A man, a plan, a canal: Panama"
    Output: true


Example 2:

    Input: "race a car"
    Output: false


```JavaScript
/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function(s) {
  s = s.toLowerCase().replace(/[^\w]/g, '')
  return s === s.split('').reverse().join('')
};

var isPalindrome = function(s) {
  s = s.replace(/\W/g, '').toLowerCase()
  
  let left = 0
  let right = s.length - 1

  while (left < right) {
    if (s[left] !== s[right]) return false
    left++
    right--
  }

  return true
}
```