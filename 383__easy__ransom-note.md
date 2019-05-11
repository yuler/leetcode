# Ransom Note

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

Note:
You may assume that both strings contain only lowercase letters.

    canConstruct("a", "b") -> false
    canConstruct("aa", "ab") -> false
    canConstruct("aa", "aab") -> true


```JavaScript
/**
 * @param {string} ransomNote
 * @param {string} magazine
 * @return {boolean}
 */
var canConstruct = function(ransomNote, magazine) {
  const map = {}
  for (let i = 0; i < ransomNote.length; i++) {
    const char = ransomNote[i]
    const index = magazine.indexOf(char, map[char] || 0)
    if (index === -1) {
      return false
    }
    map[char] = index + 1
  }
  return true
};
```