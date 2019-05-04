# Isomorphic Strings

Given two strings s and t, determine if they are isomorphic.

Two strings are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

Example 1:

    Input: s = "egg", t = "add"
    Output: true

Example 2:

    Input: s = "foo", t = "bar"
    Output: false

Example 3:

    Input: s = "paper", t = "title"
    Output: true

Note:
You may assume both s and t have the same length.


```JavaScript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isIsomorphic = function(s, t) {
  const map = new Map()
  const set = new Set()

  for (let i = 0; i < s.length; i++) {
    const l = s.charAt(i)
    const r = t.charAt(i)

    if (map.has(l)) {
      if (map.get(l) !== r) {
        return false
      }
    } else {
      if (set.has(r)) return false

      map.set(l, r)
      set.add(r)
    }
  }

  return true
};

var isIsomorphic = function(s, t) {
  let i = 0

  while (i < s.length) {
    if (s.indexOf(s[i]) === t.indexOf(t[i])) {
      i++
    } else {
      break
    }
  }

  return i === s.length
}
```