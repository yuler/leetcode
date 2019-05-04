# Reverse Linked List

Reverse a singly linked list.

Example:

    Input: 1->2->3->4->5->NULL
    Output: 5->4->3->2->1->NULL

Follow up:

A linked list can be reversed either iteratively or recursively. Could you implement both?


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
 * @return {ListNode}
 */
var reverseList = function(head) {
  if (!head || !head.next) return head
  
  let next = new ListNode(head.val)
  let prev
  while (head.next) {
    prev = new ListNode(head.next.val)    
    prev.next = next
    head = head.next
    next = prev
  }

  return prev
};

var reverseList = function(head) {
  if (!head || !head.next) return head

  const newHead = reverseList(head.next)
  head.next.next = head
  head.next = null
  return newHead
}
```