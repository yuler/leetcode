# Palindrome Linked List

Given a singly linked list, determine if it is a palindrome.

Example 1:

    Input: 1->2
    Output: false

Example 2:

    Input: 1->2->2->1
    Output: true

Follow up:

Could you do it in O(n) time and O(1) space?


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
 * @return {boolean}
 */
var isPalindrome = function(head) {
  const array = []
  while (head) {
    array.push(head.val)
    head = head.next
  }
  return array.toString() === array.reverse().toString()
};
```