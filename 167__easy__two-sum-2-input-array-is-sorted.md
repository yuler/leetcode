# Two Sum II - Input array is sorted

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

Note:

Your returned answers (both index1 and index2) are not zero-based.
You may assume that each input would have exactly one solution and you may not use the same element twice.

Example:

    Input: numbers = [2,7,11,15], target = 9
    Output: [1,2]
    Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.


```JavaScript
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(numbers, target) {
  for (let i = 0; i < numbers.length; i++) {
    const val = numbers[i]
    const diff = target - val
    const index = numbers.lastIndexOf(diff)
    if (index > -1) {
      return [i + 1, index + 1]
    }
  }
};

var twoSum = function(numbers, target) {
  let left = 0
  let right = numbers.length - 1

  while (left < right) {
    let sum = numbers[left] + numbers[right]
    if (sum == target) {
      return [left + 1, right + 1]      
    } else if (sum < target) {
      left++
    } else {
      right--
    }
  }
}
```