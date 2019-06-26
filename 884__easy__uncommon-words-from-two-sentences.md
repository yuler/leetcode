# Uncommon Words from Two Sentences

```JavaScript
/**
 * @param {string} A
 * @param {string} B
 * @return {string[]}
 */
var uncommonFromSentences = function(A, B) {
  const count = new Map()
  for (const word of A.split(' ')) {
    count.set(word, (count.get(word) || 0) + 1)  
  }
  for (const word of B.split(' ')) {
    count.set(word, (count.get(word) || 0) + 1)  
  }
  
  const ans = []
  for (const [key, val] of count.entries()) {
    if (val === 1) {
      ans.push(key)
    }
  }
  
  return ans
};
```