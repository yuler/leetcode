# N-ary Tree Postorder Traversal

Given an n-ary tree, return the postorder traversal of its nodes' values.

For example, given a 3-ary tree:

Return its postorder traversal as: [5,6,3,2,4,1].
 
Note:

Recursive solution is trivial, could you do it iteratively?


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
 * @return {number[]}
 */
var postorder = function(root) {
  const result = []  
  traverse(root)
  return result

  function traverse(root) {
    if (!root) return
    result.unshift(root.val)

    for (let i = root.children.length - 1; i >= 0; i--) {
     traverse(root.children[i]) 
    }
  }
};

var postorder = function(root) {
  if (!root) return []
  const result = []
  const stack = [root]
  let current = null

  while (stack.length) {
    current = stack.pop()
    result.unshift(current.val)

    for (let i = 0; i < current.length; i++) {
      stack.push(current.children[i])
    }
  }

  return result
}
```