# Longest Univalue Path

Given a binary tree, find the length of the longest path where each node in the path has the same value. This path may or may not pass through the root.

The length of path between two nodes is represented by the number of edges between them.

Example 1:

    Input:
                  5
                 / \
                4   5
               / \   \
              1   1   5
    Output: 2

 
Example 2:

    Input:
                  1
                 / \
                4   5
               / \   \
              4   4   5
    Output: 2


Note: The given binary tree has not more than 10000 nodes. The height of the tree is not more than 1000.


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
var longestUnivaluePath = function(root) {
  let max = 0
  traverse(root)
  return max 
  
  function traverse(root) {
    if (root == null) return 0
    const left = traverse(root.left)
    const right = traverse(root.right)
    let arrowLeft = 0
    let arrowRight = 0
    if (root.left != null && root.left.val == root.val) {
      arrowLeft += left + 1
    }
    if (root.right != null && root.right.val == root.val) {
      arrowRight += right + 1
    }
    max = Math.max(max, arrowLeft + arrowRight)
    return Math.max(arrowLeft, arrowRight)
  }
};
```