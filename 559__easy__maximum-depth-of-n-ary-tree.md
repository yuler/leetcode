# Maximum Depth of N-ary Tree

Given a n-ary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

For example, given a 3-ary tree:

 


 

We should return its max depth, which is 3.


Note:

  1. The depth of the tree is at most 1000.
  2. The total number of nodes is at most 5000.


```JavaScript
/**
 * // Definition for a Node.
 * function Node(val,children) {
 *    this.val = val;
 *    this.children = children;
 * };
 */
/**
 * @param {Node} root
 * @return {number}
 */
var maxDepth = function(root) {
  if (!root) return 0
  let count = 1
  for (const node of root.children) {
    count = Math.max(count, maxDepth(node) + 1)
  }
  return count
};
```