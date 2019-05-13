# Sum of Left Leaves

Find the sum of all left leaves in a given binary tree.

Example:

        3
       / \
      9  20
        /  \
       15   7

    There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.


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
 * @return {number}
 */
var sumOfLeftLeaves = function(root) {
  if (!root) return 0

  let sum = 0
  
  if (root.left) {
    if (!root.left.left && !root.left.right) {
      sum += root.left.val
    } else {
      sum += sumOfLeftLeaves(root.left)
    }
  }  

  sum += sumOfLeftLeaves(root.right)

  return sum
};


```