# N-ary Tree Preorder Traversal

Given an n-ary tree, return the preorder traversal of its nodes' values.

For example, given a 3-ary tree:

Return its preorder traversal as: [1,3,5,6,2,4].

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
var preorder = function(root) {
  const result = []
  traverse(root)
  return result

  function traverse(root) {
    if (!root) return
    result.push(root.val)
    if (root.children) root.children.forEach(children => traverse(children))
  }
};

var preorder = function(root) {
  if (!root) return []
  const result = []
  const stack = [root]
  let current = null

  while (stack.length) {
    current = stack.pop()
    result.push(current.val)

    for (let i = current.children.length - 1; i >= 0; i--) {
      stack.push(current.children[i])
    }
  }

  return result
}
```