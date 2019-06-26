# Surface Area of 3D Shapes

```JavaScript
/**
 * @param {string[]} A
 * @return {number}
 */
var numSpecialEquivGroups = function(A) {
  const set = new Set()
  for (const ch of A) {
    const count = Array.from({ length: 52 }).fill(0)
    for (let i = 0; i < ch.length; i ++) {
      count[ch.charCodeAt(i) - 'a'.charCodeAt(0) + 26 * (i % 2)]++
    }
    set.add(count.join(''))
  }
  
  return set.size
};
```