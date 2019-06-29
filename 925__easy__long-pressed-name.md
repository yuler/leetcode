# Long Pressed Name

```JavaScript
/**
 * @param {string} name
 * @param {string} typed
 * @return {boolean}
 */
var isLongPressedName = function(name, typed) {
  if (name === typed) return true
  
  let j = 0
  for (let i = 0; i < name.length; i++) {
    const ch = name[i]
    
    if (j === typed.length) return false
    
    if (typed[j] !== ch) {
      if (j === 0 || typed[j - 1] !== typed[j]) return false
      
      let cur = typed[j]
      while (j < typed.length && typed[j] === cur) {
        j++
      }
      if (j === typed.length || typed[j] !== ch) {
        return false
      }
    }
    
    j++
  }
  
  return true
};
```