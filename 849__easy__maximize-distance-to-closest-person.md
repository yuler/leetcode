# Maximize Distance to Closest Person

```JavaScript
/**
 * @param {number[]} seats
 * @return {number}
 */
var maxDistToClosest = function(seats) {
  const length = seats.length
  let prev = -1
  let next = 0
  let ans = 0
  
  for (let i = 0; i < length; i++) {
    if (seats[i]) {
      prev = i
    } else {
      while (next < length && seats[next] === 0 || next < i) {
        next++
      }
      const left = prev === -1 ? length : i - prev
      const right = next === length ? length : next - i
      ans = Math.max(ans, Math.min(left, right))
    }
  }
  
  return ans
};
```