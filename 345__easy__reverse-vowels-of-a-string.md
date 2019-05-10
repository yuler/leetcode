# Reverse Vowels of a String

Write a function that takes a string as input and reverse only the vowels of a string.

Example 1:

    Input: "hello"
    Output: "holle"

Example 2:

    Input: "leetcode"
    Output: "leotcede"

Note:
The vowels does not include the letter "y".


```JavaScript
/**
 * @param {string} s
 * @return {string}
 */
var reverseVowels = function(s) {
  s = s.split('')
  let left = 0
  let right = s.length - 1
  while (left < right) {
    if (!/[aeiou]/i.test(s[left])) {
      left++
      continue
    }
    if (!/[aeiou]/i.test(s[right])) {
      right--
      continue
    }
    console.log(left, right)
    const temp = s[left]
    s[left] = s[right]
    s[right] = temp
    console.log(temp, s[left], s[right])
    left++
    right--
  }
  return s.join('')
};
```