# Balanced Binary Tree

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

Example 1:

Given the following tree [3,9,20,null,null,15,7]:

      3
     / \
    9  20
      /  \
     15   7

Return true.

Example 2:

Given the following tree [1,2,2,3,3,null,null,4,4]:

           1
          / \
         2   2
        / \
       3   3
      / \
     4   4

Return false.


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
 * @return {boolean}
 */
var isBalanced = function(root) {
  if (!root) return true

  let left = depth(root.left)
  let right = depth(root.right)
  if (Math.abs(left - right) > 1) return false
  else {
    let res = isBalanced(root.left)
    if (!res) return false
    res = isBalanced(root.right)
    if (!res) return false
  }
  return true
  
  function depth(root) {
    if (!root) return 0
    let left = depth(root.left)
    let right = depth(root.right)
    return Math.max(left, right) + 1
  }
};

var isBalanced = function(root) {
  return getHeight(root) !== -1

  function getHeight(root) {
    if (!root) return 0

    const left = getHeight(root.left)
    const right = getHeight(root.right)

    if (left === -1 || right === -1 || Math.abs(left - right) > 1) {
      return false
    }

    return Math.max(left, right) + 1
  }
}


```

