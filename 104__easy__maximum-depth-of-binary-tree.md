# Maximum Depth of Binary Tree

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

Note: A leaf is a node with no children.

Example:

Given binary tree [3,9,20,null,null,15,7],

      3
     / \
    9  20
      /  \
     15   7

return its depth = 3.


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
var maxDepth = function(root) {
  if (!root) return 0
  return max(root.left, root.right, 1)
  
  function max(left, right, sum) {
    if (!left && !right) return sum
    return Math.max(
      max(left && left.left, left && left.right, sum + 1),
      max(right && right.left, right && right.right, sum + 1)
    )
  }
};

const maxDepth = root => {
  if (!root) {
    return 0
  }
  
  const left = maxDepth(root.left)
  const right = maxDepth(root.right)
  
  return Math.max(left, right) + 1
};
```