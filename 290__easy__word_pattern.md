# Word Pattern

Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

Example 1:

    Input: pattern = "abba", str = "dog cat cat dog"
    Output: true

Example 2:

    Input:pattern = "abba", str = "dog cat cat fish"
    Output: false

Example 3:

    Input: pattern = "aaaa", str = "dog cat cat dog"
    Output: false

Example 4:

    Input: pattern = "abba", str = "dog dog dog dog"
    Output: false

Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters that may be separated by a single space.


```JavaScript
/**
 * @param {string} pattern
 * @param {string} str
 * @return {boolean}
 */
var wordPattern = function(pattern, str) {
  const words = str.split(' ')
  if (pattern.length !== words.length) return false
    
  const map1 = new Map()
  const map2 = new Map()
  
  for (let i = 0; i < words.length; i++) {
    const p = pattern[i]
    const w = words[i]
    if (!map1.has(p) && !map2.has(w)) {
      map1.set(p, w)
      map2.set(w, p)
    } else if (map2.get(w) !== p || map1.get(p) !== w) {
      return false
    }
  }
    
  return true
};
```