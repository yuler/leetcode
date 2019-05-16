# Third Maximum Number

Given a non-empty array of integers, return the third maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).

Example 1:

    Input: [3, 2, 1]

    Output: 1

    Explanation: The third maximum is 1.

Example 2:

    Input: [1, 2]

    Output: 2

    Explanation: The third maximum does not exist, so the maximum (2) is returned instead.

Example 3:

    Input: [2, 2, 3, 1]

    Output: 1

    Explanation: Note that the third maximum here means the third maximum distinct number.
    Both numbers with value 2 are both considered as second maximum.


```JavaScript
/**
 * @param {number[]} nums
 * @return {number}
 */
var thirdMax = function(nums) {
  const set = new Set(nums.sort((a, b) => b - a))
  const arr = Array.from(set)
  return arr.length >= 3 ? arr[2] : arr[0]
};

var thirdMax = function(nums) {
  let max = -Infinity
  let second = -Infinity
  let third = -Infinity
  
  nums.forEach(num => {
    if (num > max){
      third = second
      second = max
      max = num
    } else if (num > second && num < max){
      third = second
      second = num
    } else if (num > third && num < second){
      third = num
    }
  })
  
  return third !== -Infinity 
    ? third 
    : max
};
```