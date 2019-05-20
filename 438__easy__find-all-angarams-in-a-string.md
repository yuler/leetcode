# Find All Anagrams in a String

Given a string s and a non-empty string p, find all the start indices of p's anagrams in s.

Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100.

The order of output does not matter.

Example 1:

    Input:
    s: "cbaebabacd" p: "abc"

    Output:
    [0, 6]

    Explanation:
    The substring with start index = 0 is "cba", which is an anagram of "abc".
    The substring with start index = 6 is "bac", which is an anagram of "abc".

Example 2:

    Input:
    s: "abab" p: "ab"

    Output:
    [0, 1, 2]

    Explanation:
    The substring with start index = 0 is "ab", which is an anagram of "ab".
    The substring with start index = 1 is "ba", which is an anagram of "ab".
    The substring with start index = 2 is "ab", which is an anagram of "ab".


```JavaScript
/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function(s, p) {
  const indexs = []

  const map = new Map()
  for (let i = 0; i < p.length; i++) {
    const key = p[i]
    const value = map.get(key) || 0
    map.set(key, value + 1)
  }

  const cache = new Set()
  const len = p.length
  for (let i = 0; i < s.length - len - 1; i++) {
    const str = s.slice(i, len + i)
    if (cache.has(str)) {
      indexs.push(i)
      continue
    }

    if (isAnagram(str, map)) {
      indexs.push(i)
      cache.add(str)
    }
  }

  return indexs

  function isAnagram(str, map) {
    const set = new Set(str)
    if (set.size !== map.size) return false
    
    for (const key of map.keys()) {
      if (!str.includes(key)) return false
      if (str.split('').filter(s => s === key).length !== map.get(key)) return false
    }

    return true
  }
};

var findAnagrams = function(s, p) {
  let len = p.length
  let res = []
  if (s.length < len) return []
  let sArray = new Array(26).fill(0)
  let pArray = new Array(26).fill(0)

  for (let ch of p) {
    pArray[char2Index(ch)]++
  }

  for (let i = 0; i < len; i++) {
    sArray[char2Index(s[i])]++
  }

  if (isAnagram(sArray, pArray)) {
    res.push(0)
  }

  for (let i = len; i < s.length; i++) {
    sArray[char2Index(s[i])]++
    sArray[char2Index(s[i - len])]--
    if(isAnagram(sArray, pArray)) res.push(i - len + 1)
  }

  return res

  function char2Index(char) {
    return char.charCodeAt(0) - 97
  }

  function isAnagram(sArray, pArray) {
    for (let i = 0; i < 26; i++) {
      if (sArray[i] !== pArray[i]) {
        return false
      }
    }
    return true
  }
}
```