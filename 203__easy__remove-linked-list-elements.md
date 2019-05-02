# Remove Linked List Elements

Remove all elements from a linked list of integers that have value val.

Example:

    Input:  1->2->6->3->4->5->6, val = 6
    Output: 1->2->3->4->5


```JavaScript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function(head, val) {
  if (!head) return null
  head.next = removeElements(head.next, val)
  return head.val === val ? head.next : head
};
```