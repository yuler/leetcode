# Two Sum IV - Input is a BST

Given a Binary Search Tree and a target number, return true if there exist two elements in the BST such that their sum is equal to the given target.

Example 1:

    Input: 
        5
       / \
      3   6
     / \   \
    2   4   7

    Target = 9

    Output: True
 

Example 2:

    Input: 
        5
       / \
      3   6
     / \   \
    2   4   7

    Target = 28

    Output: False


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
 * @param {number} k
 * @return {boolean}
 */
var findTarget = function(root, k) {
  const set = new Set()
  return find(root, k, set)
  
  function find(root, k, set) {
    if (root == null) return false
    if (set.has(k - root.val)) return true
    set.add(root.val)
    return find(root.left, k, set) || find(root.right, k, set)
  }
};
```