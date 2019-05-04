# Count Primes

Count the number of prime numbers less than a non-negative number, n.

Example:

    Input: 10
    Output: 4
    Explanation: There are 4 prime numbers less than 10, they are 2, 3, 5, 7.


```JavaScript
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
  let sum = 0
  for (let i = 1; i < n; i++) {
    if (isPrime(i)) {
      sum++
    }
  }
  
  return sum
  
  function isPrime(n) {
    if (n === 1) return false
    if (n === 2) return true
    let i = 2
    while (i <= Math.sqrt(n)) {
      if (n % i === 0) return false
      i++
    }
    return true
  }
};

var countPrimes = function(n) {
  const noPrimes = new Unit8Array(n)
  let count = 0
  for (let i = 2; i < n; i++) {
    if (!noPrimes) {
      count++
      let a = n / i
      for(let j = i; j < a ; j++){
        notPrimes[i * j]=true;
      }
    }
  }
  return count
}
```