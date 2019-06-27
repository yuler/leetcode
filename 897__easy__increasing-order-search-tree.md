# Increasing Order Search Tree

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
var increasingBST = function(root) {
  const ans = new TreeNode(0)
  let cur = ans
  inorder(root)
  return ans.right
  
  function inorder(node) {
    if (node == null) return
    inorder(node.left)
    node.left = null
    cur.right = node
    cur = node
    inorder(node.right)
  }
};
```