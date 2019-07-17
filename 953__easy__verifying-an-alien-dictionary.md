# Verifying an Alien Dictionary

```JavaScript
/**
 * @param {string[]} words
 * @param {string} order
 * @return {boolean}
 */
var isAlienSorted = function(words, order) {
  const map = Object.create(null)
  order.split('').forEach((ch, idx) => map[ch] = idx)
  
  for (let i = 0; i < words.length - 1; i++) {
    const word = words[i]
    const next = words[i + 1]
    if (!isorder(word, next)) return false
  }
  
  return true
    
  function isorder(a, b) {
    for (let i = 0; i < a.length; i++) {
      if (a[i] == b[i]) continue
      if (!b[i]) return false
      return map[a[i]] < map[b[i]]
    }
    return true
  }
};
```