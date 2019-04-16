# Same Tree

Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.

Example 1:

    Input:     1         1
              / \       / \
             2   3     2   3
            [1,2,3],  [1,2,3]
    Output: true

Example 2:

    Input:     1         1
              /           \
             2             2
            [1,2],     [1,null,2]
    Output: false

Example 3:

    Input:     1         1
              / \       / \
             2   1     1   2
            [1,2,1],  [1,1,2]
    Output: false


```JavaScript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {boolean}
 */
var isSameTree = function(p, q) {
  if (!p && !q) return true
  console.log(p, q)
  if (!p || !q || p.val !== q.val) return false
  return isSameTree(p.left, q.left) && isSameTree(p.right, q.right)
};

var isSameTree = function(p, q) {
  let stack = [p, q]

  while (stack.length > 0) {
    var q = stack.pop()
    var p = stack.pop()

    if (!p && !q) continue

    if (!p || !q) return false

    if (p.val === q.val) {
      stack.push(p.left)
      stack.push(q.left)
      stack.push(p.right)
      stack.push(q.right)
    } else {
      return false
    }
  }

  return true
}
```