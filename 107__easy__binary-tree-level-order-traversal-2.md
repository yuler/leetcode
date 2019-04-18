# Binary Tree Level Order Traversal II

Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:
Given binary tree [3,9,20,null,null,15,7],

      3
     / \
    9  20
      /  \
     15   7

return its bottom-up level order traversal as:

    [
      [15,7],
      [9,20],
      [3]
    ]


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
 * @return {number[][]}
 */
var levelOrderBottom = function(root) {
  if (!root) return []

  const result = [[root.val]]
  collection(root.left, root.right, 1)

  function collection(left, right, level) {
    if (!left & !right) return
    if (!result[level]) result[level] = []
    if (left) {
      result[level].push(left.val)
      collection(left.left, left.right, level + 1)
    }
    if (right) {
      result[level].push(right.val)
      collection(right.left, right.right, level + 1)
    }
  }

  return result.reverse()
};
```