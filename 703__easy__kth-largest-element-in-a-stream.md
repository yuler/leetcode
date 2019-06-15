# Kth Largest Element in a Stream

Design a class to find the kth largest element in a stream. Note that it is the kth largest element in the sorted order, not the kth distinct element.

Your KthLargest class will have a constructor which accepts an integer k and an integer array nums, which contains initial elements from the stream. For each call to the method KthLargest.add, return the element representing the kth largest element in the stream.

Example:

    int k = 3;
    int[] arr = [4,5,8,2];
    KthLargest kthLargest = new KthLargest(3, arr);
    kthLargest.add(3);   // returns 4
    kthLargest.add(5);   // returns 5
    kthLargest.add(10);  // returns 5
    kthLargest.add(9);   // returns 8
    kthLargest.add(4);   // returns 8

Note: 
You may assume that nums' length ≥ k-1 and k ≥ 1.


```JavaScript
/**
 * @param {number} k
 * @param {number[]} nums
 */
var KthLargest = function(k, nums) {
  nums.sort((a, b) => a - b)
  this.k = k
  this.stream = nums
};

/** 
 * @param {number} val
 * @return {number}
 */
KthLargest.prototype.add = function(val) {
  const index = this.stream.findIndex(item => item > val)
  if (index > -1) {
    this.stream.splice(index, 0, val)
  } else {
    this.stream.push(val)
  }
  return this.stream[this.stream.length - this.k]
};

/** 
 * Your KthLargest object will be instantiated and called as such:
 * var obj = new KthLargest(k, nums)
 * var param_1 = obj.add(val)
 */
```