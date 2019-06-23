# Most Common Word

```JavaScript
/**
 * @param {string} paragraph
 * @param {string[]} banned
 * @return {string}
 */
var mostCommonWord = function(paragraph, banned) {
  const words = paragraph.replace(/[^\w\s]/g, ' ').split(/\s+/)
  const map = new Map()
  for (let i = 0; i < words.length; i++) {
    const word = words[i].toLowerCase()
    if (banned.includes(word)) continue
    map.set(word, (map.get(word) || 0) + 1)
  }
  
  let max = 0
  let ans = 0
  for (const [key, value] of map.entries()) {
    if (value > max) {
      max = value
      ans = key
    }
  } 
  
  return ans
};
```