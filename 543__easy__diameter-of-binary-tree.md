# Diameter of Binary Tree

Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

Example:

    Given a binary tree 
              1
             / \
            2   3
           / \     
          4   5
Return 3, which is the length of the path [4,2,1,3] or [5,2,1,3].

Note: The length of path between two nodes is represented by the number of edges between them.


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
var diameterOfBinaryTree = function(root) {
  let path = 1
  depth(root)
  return path - 1
  
  function depth(node) {
    if (!node) return 0
    const l = depth(node.left)
    const r = depth(node.right)
    path = Math.max(path, l + r + 1)
    return Math.max(l, r) + 1
  }
};
```