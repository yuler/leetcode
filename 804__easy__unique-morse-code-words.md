# Unique Morse Code Words

```JavaScript
/**
 * @param {string[]} words
 * @return {number}
 */
var uniqueMorseRepresentations = function(words) {
  const map = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
  const set = new Set()
  
  words.forEach(word => {
    const code = word.split('').map(ch => {
      return map[ch.charCodeAt(0) - 97]
    }).join('')
    set.add(code)
  })
  
  return set.size
};
```