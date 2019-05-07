# Valid Anagram

Given two strings s and t , write a function to determine if t is an anagram of s.

Example 1:

    Input: s = "anagram", t = "nagaram"
    Output: true

Example 2:

    Input: s = "rat", t = "car"
    Output: false

Note:
You may assume the string contains only lowercase alphabets.

Follow up:
What if the inputs contain unicode characters? How would you adapt your solution to such case?


```JavaScript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
  if (s.length !== t.length) return false
  
  const arr1 = s.split('').sort()
  const arr2 = t.split('').sort()
  return arr1.join('') === arr2.join('')
};

var isAnagram = function(s, t) {
  const sMap = getMap(s)
  const tMap = getMap(t)

  for (let i = 0; i < sMap.length; i++) {
    if (sMap[i] !== tMap[i]) return false
  }

  return true

  function getMap(s) {
    const map = new Array(26).fill(0)
    const aCode = 'a'.charCodeAt(0)
    for (let i = 0; i < s.length; i++) {
      map[s.charCodeAt(i) - aCode] += 1
    }
    return map
  }
}
```