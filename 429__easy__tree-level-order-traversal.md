# N-ary Tree Level Order Traversal

Given an n-ary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example, given a 3-ary tree:

We should return its level order traversal:

    [
        [1],
        [3,2,4],
        [5,6]
    ]
 

Note:

The depth of the tree is at most 1000.
The total number of nodes is at most 5000.


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
 * @return {number[][]}
 */
var levelOrder = function(root) {
  const result = []
  let queue = []

  if (root == null) return result

  queue.push(root)
  while (queue.length) {
    const len = queue.length
    const temp = queue.map(node => node.val)
    for (let i = 0; i < len; i++) {
      const children = queue.pop().children
      if (children) queue.unshift(...children)
    }
    
    result.push(temp)
  }
  
  return result
};
```