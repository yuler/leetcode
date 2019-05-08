# Binary Tree Paths

Given a binary tree, return all root-to-leaf paths.

Note: A leaf is a node with no children.

Example:

Input:

       1
     /   \
    2     3
     \
      5

    Output: ["1->2->5", "1->3"]

    Explanation: All root-to-leaf paths are: 1->2->5, 1->3


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
 * @return {string[]}
 */
var binaryTreePaths = function(root) {
  if (!root) return []
  const routes = []
  binaryTreePath(root)
  return routes
  
  function binaryTreePath(root, path = '') {
    path = path ? `${path}->${root.val}` : `${root.val}`
    if (!root.left && !root.right) { 
      return routes.push(path)
    }
    if (root.left) binaryTreePath(root.left, path)
    if (root.right) binaryTreePath(root.right, path)
  }
};
```