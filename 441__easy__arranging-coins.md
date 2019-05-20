# Arranging Coins

You have a total of n coins that you want to form in a staircase shape, where every k-th row must have exactly k coins.

Given n, find the total number of full staircase rows that can be formed.

n is a non-negative integer and fits within the range of a 32-bit signed integer.

Example 1:

    n = 5

    The coins can form the following rows:
    ¤
    ¤ ¤
    ¤ ¤

    Because the 3rd row is incomplete, we return 2.

Example 2:

    n = 8

    The coins can form the following rows:
    ¤
    ¤ ¤
    ¤ ¤ ¤
    ¤ ¤

    Because the 4th row is incomplete, we return 3.


```JavaScript
/**
 * @param {number} n
 * @return {number}
 */
var arrangeCoins = function(n) {
  if (n < 2) return n
  
  let start = 0
  let end = n
  let mid
  
  while (start < end) {
    mid = Math.floor((start + end) / 2)
    const current = sum(mid)
    const next = sum(mid + 1)
    if (current <= n && next > n) return mid
    if (current > n) {
      end = mid
    } else {
      start = mid
    }
  }

  return mid

  function sum(n) {
    return (1 + n) * n /2
  }
};
```