# Minimum Index Sum of Two Lists

Suppose Andy and Doris want to choose a restaurant for dinner, and they both have a list of favorite restaurants represented by strings.

You need to help them find out their common interest with the least list index sum. If there is a choice tie between answers, output all of them with no order requirement. You could assume there always exists an answer.

Example 1:

    Input:
    ["Shogun", "Tapioca Express", "Burger King", "KFC"]
    ["Piatti", "The Grill at Torrey Pines", "Hungry Hunter Steakhouse", "Shogun"]
    Output: ["Shogun"]
    Explanation: The only restaurant they both like is "Shogun".

Example 2:

    Input:
    ["Shogun", "Tapioca Express", "Burger King", "KFC"]
    ["KFC", "Shogun", "Burger King"]
    Output: ["Shogun"]
    Explanation: The restaurant they both like and have the least index sum is "Shogun" with index sum 1 (0+1).

Note:
  1. The length of both lists will be in the range of [1, 1000].
  2. The length of strings in both lists will be in the range of [1, 30].
  3. The index is starting from 0 to the list length minus 1.
  4. No duplicates in both lists.


```JavaScript
/**
 * @param {string[]} list1
 * @param {string[]} list2
 * @return {string[]}
 */
var findRestaurant = function(list1, list2) {
  const result = []
  for (let sum = 0; sum < list1.length + list2.length - 1; sum++) {
    for (let i = 0; i <= sum; i++) {
      if (i < list1.length && sum - i < list2.length && list1[i] === list2[sum - i]) {
        result.push(list1[i])
      }
    }
    if (result.length > 0) 
      break
  }
  return result
};
```