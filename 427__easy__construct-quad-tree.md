# Construct Quad Tree

We want to use quad trees to store an N x N boolean grid. Each cell in the grid can only be true or false. The root node represents the whole grid. For each node, it will be subdivided into four children nodes until the values in the region it represents are all the same.

Each node has another two boolean attributes : isLeaf and val. isLeaf is true if and only if the node is a leaf node. The val attribute for a leaf node contains the value of the region it represents.

Your task is to use a quad tree to represent a given grid. The following example may help you understand the problem better:

Given the 8 x 8 grid below, we want to construct the corresponding quad tree:


It can be divided according to the definition above:

The corresponding quad tree should be as following, where each node is represented as a (isLeaf, val) pair.

For the non-leaf nodes, val can be arbitrary, so it is represented as `*`. 

Note:

N is less than 1000 and guaranteened to be a power of 2.
If you want to know more about the quad tree, you can refer to its wiki.


```JavaScript
/**
 * // Definition for a QuadTree node.
 * function Node(val,isLeaf,topLeft,topRight,bottomLeft,bottomRight) {
 *    this.val = val;
 *    this.isLeaf = isLeaf;
 *    this.topLeft = topLeft;
 *    this.topRight = topRight;
 *    this.bottomLeft = bottomLeft;
 *    this.bottomRight = bottomRight;
 * };
 */
/**
 * @param {number[][]} grid
 * @return {Node}
 */
var construct = function(grid) {
  return build(0, 0, grid.length -1, grid.length - 1, grid)

  function build(r1, c1, r2, c2, grid) {
    if (r1 > r2 || c1 > c2) return null
    let isLeaf = true
    const val = grid[r1][c1]

    for (let i = r1; i <= r2; i++) {
      for (let j = c1; j <= c2; j++) {
        if (grid[i][j] !== val) {
          isLeaf = false
          break
        }
      }
    }

    if (isLeaf) {
      return new Node(val === 1, true, null, null, null, null)
    }

    const rowMid = parseInt((r1 + r2) / 2)
    const colMid = parseInt((c1 + c2) / 2)

    return new Node(false, false,
      build(r1, c1, rowMid, colMid, grid),
      build(r1, colMid + 1, rowMid, c2, grid),
      build(rowMid + 1, c1, r2, colMid, grid),
      build(rowMid + 1, colMid + 1, r2, c2, grid)
    )
  }
};
```