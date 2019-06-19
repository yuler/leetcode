# Minimum Distance Between BST Nodes

Given a Binary Search Tree (BST) with the root node root, return the minimum difference between the values of any two different nodes in the tree.

Example :

    Input: root = [4,2,6,1,3,null,null]
    Output: 1
    Explanation:
    Note that root is a TreeNode object, not an array.

    The given tree [4,2,6,1,3,null,null] is represented by the following diagram:

              4
            /   \
          2      6
         / \    
        1   3  

    while the minimum difference in this tree is 1, it occurs between node 1 and node 2, also between node 3 and node 2.

Note:

The size of the BST will be between 2 and 100.
The BST is always valid, each node's value is an integer, and each node's value is different.


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
var minDiffInBST = function(root) {
  const nodes = []
  let min = Infinity
  traverse(root)
  nodes.sort((a, b) => a - b)
  for (let i = 0; i < nodes.length - 1; i++) {
    min = Math.min(Math.abs(nodes[i] - nodes[i + 1]), min)
  }
  return min
  
  function traverse(root) {
    if (!root) return
    nodes.push(root.val)
    if (root.left) {
      traverse(root.left)
    }
    if (root.right) {
      traverse(root.right)
    }
  }
};
```