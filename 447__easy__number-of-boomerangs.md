# Number of Boomerangs

Given n points in the plane that are all pairwise distinct, a "boomerang" is a tuple of points (i, j, k) such that the distance between i and j equals the distance between i and k (the order of the tuple matters).

Find the number of boomerangs. You may assume that n will be at most 500 and coordinates of points are all in the range [-10000, 10000] (inclusive).

Example:

    Input:
    [[0,0],[1,0],[2,0]]

    Output:
    2

    Explanation:
    The two boomerangs are [[1,0],[0,0],[2,0]] and [[1,0],[2,0],[0,0]]


```JavaScript
/**
 * @param {number[][]} points
 * @return {number}
 */
var numberOfBoomerangs = function(points) {
  const map = new Map()
  let count = 0
  
  for (let i = 0; i < points.length; i++)   {
    for (let j = 0; j < points.length; j++) {
      if (i == j) continue

      const key = getDistance(points[i], points[j])
      const value = (map.get(key) || 0) + 1
      map.set(key, value)
    }

    for (const val of map.values()) {
      count += val * (val -1)
    }

    map.clear()
  }

  return count

  function getDistance(point1, point2) {
    const dx = point1[0] - point2[0]
    const dy = point1[1] - point2[1]

    return dx * dx + dy * dy
  }
};
```