# Invert Binary Tree

Invert a binary tree.

Example:

Input:

         4
       /   \
      2     7
     / \   / \
    1   3 6   9

Output:

         4
       /   \
      7     2
     / \   / \
    9   6 3   1

Trivia:
This problem was inspired by this original tweet by Max Howell:

Google: 90% of our engineers use the software you wrote (Homebrew), but you can’t invert a binary tree on a whiteboard so f*** off.


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
 * @return {TreeNode}
 */
var invertTree = function(root) {
  if (!root) return root
  const left = invertTree(root.left)
  const right = invertTree(root.right)
  root.left = right
  root.right = left
  return root
};

var invertTree = function(root) {
  if (root) {
    const temp = root.left
    root.left = root.right
    root.right = temp
    if (root.left) invertTree(root.left)
    if (root.right) invertTree(root.right)
  }
  return root
}
```