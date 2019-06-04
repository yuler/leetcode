# Quad Tree Intersection

A quadtree is a tree data in which each internal node has exactly four children: topLeft, topRight, bottomLeft and bottomRight. Quad trees are often used to partition a two-dimensional space by recursively subdividing it into four quadrants or regions.

We want to store True/False information in our quad tree. The quad tree is used to represent a N * N boolean grid. For each node, it will be subdivided into four children nodes until the values in the region it represents are all the same. Each node has another two boolean attributes : isLeaf and val. isLeaf is true if and only if the node is a leaf node. The val attribute for a leaf node contains the value of the region it represents.

For example, below are two quad trees A and B:

    A:
    +-------+-------+   T: true
    |       |       |   F: false
    |   T   |   T   |
    |       |       |
    +-------+-------+
    |       |       |
    |   F   |   F   |
    |       |       |
    +-------+-------+
    topLeft: T
    topRight: T
    bottomLeft: F
    bottomRight: F

    B:               
    +-------+---+---+
    |       | F | F |
    |   T   +---+---+
    |       | T | T |
    +-------+---+---+
    |       |       |
    |   T   |   F   |
    |       |       |
    +-------+-------+
    topLeft: T
    topRight:
         topLeft: F
         topRight: F
         bottomLeft: T
         bottomRight: T
    bottomLeft: T
    bottomRight: F
 

Your task is to implement a function that will take two quadtrees and return a quadtree that represents the logical OR (or union) of the two trees.

    A:                 B:                 C (A or B):
    +-------+-------+  +-------+---+---+  +-------+-------+
    |       |       |  |       | F | F |  |       |       |
    |   T   |   T   |  |   T   +---+---+  |   T   |   T   |
    |       |       |  |       | T | T |  |       |       |
    +-------+-------+  +-------+---+---+  +-------+-------+
    |       |       |  |       |       |  |       |       |
    |   F   |   F   |  |   T   |   F   |  |   T   |   F   |
    |       |       |  |       |       |  |       |       |
    +-------+-------+  +-------+-------+  +-------+-------+

Note:

  1. Both A and B represent grids of size N * N.
  2. N is guaranteed to be a power of 2.
  3. If you want to know more about the quad tree, you can refer to its wiki.
  4. The logic OR operation is defined as this: "A or B" is true if A is true, or if B is true, or if both A and B are true.


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
 * @param {Node} quadTree1
 * @param {Node} quadTree2
 * @return {Node}
 */
var intersect = function(quadTree1, quadTree2) {
  if (quadTree1.isLeaf) {
    return quadTree1.val ? quadTree1 : quadTree2
  }

  if (quadTree2.isLeaf) {
    return quadTree2.val ? quadTree2 : quadTree1
  }

  quadTree1.topLeft = intersect(quadTree1.topLeft, quadTree2.topLeft)
  quadTree1.topRight = intersect(quadTree1.topRight, quadTree2.topRight)
  quadTree1.bottomLeft = intersect(quadTree1.bottomLeft, quadTree2.bottomLeft)
  quadTree1.bottomRight = intersect(quadTree1.bottomRight, quadTree2.bottomRight)

  if (quadTree1.topLeft.isLeaf && quadTree1.topRight.isLeaf 
    && quadTree1.bottomLeft.isLeaf && quadTree1.bottomRight.isLeaf
    && quadTree1.topLeft.val == quadTree1.topRight.val 
    && quadTree1.topRight.val == quadTree1.bottomLeft.val 
    && quadTree1.bottomLeft.val == quadTree1.bottomRight.val) {
    quadTree1.isLeaf = true
    quadTree1.val = quadTree1.topLeft.val
  }

  return quadTree1
};
```