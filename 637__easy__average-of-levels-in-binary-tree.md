# Average of Levels in Binary Tree

Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array.

Example 1:

    Input:
        3
       / \
      9  20
        /  \
       15   7
    Output: [3, 14.5, 11]
    Explanation:
    The average value of nodes on level 0 is 3,  on level 1 is 14.5, and on level 2 is 11. Hence return [3, 14.5, 11].

Note:
  1. The range of node's value is in the range of 32-bit signed integer.


```JavaScript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var averageOfLevels = function(root) {
  const count = []
  const result = []
  
  average(root, 0, result, count)
  for (let i = 0; i < result.length; i++) {
    result[i] = result[i] / count[i]
  }
  
  return result
    
  function average(root, i, sum, count) {
    if (root == null) return
    if (i < sum.length) {
       sum[i] = sum[i] + root.val
       count[i] = count[i] + 1
    } else {
       sum.push(1 * root.val)
       count.push(1)
    }
    average(root.left, i + 1, sum, count)
    average(root.right, i + 1, sum, count)
  }
};
```