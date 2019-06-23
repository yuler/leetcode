# Largest Triangle area

```JavaScript
/**
 * @param {number[][]} points
 * @return {number}
 */
var largestTriangleArea = function(points) {
  let ans = 0
  for (let i = 0; i < points.length; ++i) {
    for (let j = i + 1; j < points.length; ++j) {
      for (let k = j + 1; k < points.length; ++k) {
        ans = Math.max(ans, area(points[i], points[j], points[k]))
      }
    }
  }
  return ans
  
  function area(i, j, k) {
    return 0.5 * Math.abs(i[0] * j[1] + j[0] * k[1] + k[0] * i[1] -
                         i[1] * j[0] - j[1] * k[0] - k[1] * i[0])
  }
};
```