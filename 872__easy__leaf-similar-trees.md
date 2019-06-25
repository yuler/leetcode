# Leaf-Similar Trees

```JavaScript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root1
 * @param {TreeNode} root2
 * @return {boolean}
 */
var leafSimilar = function(root1, root2) {
  const leaves1 = []
  const leaves2 = []
  dfs(root1, leaves1)
  dfs(root2, leaves2)
  
  return equals(leaves1, leaves2)
  
  function dfs(node, leaves) {
    if (node != null) {
      if (node.left == null && node.right == null) {
        leaves.push(node.val)
      }
      dfs(node.left, leaves)
      dfs(node.right, leaves)
    }
  }
  
  function equals(arr1, arr2) {
    if (arr1.length !== arr2.length) return false
    for (let i = 0; i < arr1.length; i++) {
      if (arr1[i] !== arr2[i]) return false
    }
    return true
  }
};
```