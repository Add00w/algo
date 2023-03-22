# Merge two sorted lists

> You are given the heads of two sorted linked lists `list1` and `list2`.
- Merge the two lists in a one sorted list. The list should be made by splicing together the nodes of the first two lists.
- Return the head of the merged linked list.

## Example 1:
```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```
## Example 2:
```
Input: list1 = [], list2 = []
Output: []
```
## Example 3:
```
Input: list1 = [], list2 = [0]
Output: [0]
```
## Dart
### Solution
```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *   int val;
 *   ListNode? next;
 *   ListNode([this.val = 0, this.next]);
 * }
 */
class Solution {
  ListNode? mergeTwoLists(ListNode? list1, ListNode? list2) {
    /// if one of the two lists null the answer simply is the other
    if (list1 == null) return list2;
    if (list2 == null) return list1;

    late ListNode mergedListHead;

    if (list1.val > list2.val) {
      mergedListHead = list2;
      list2 = list2.next;
    } else {
      mergedListHead = list1;
      list1 = list1.next;
    }
    ListNode currentNode = mergedListHead;
    while (list1 != null && list2 != null) {
      if (list1.val < list2.val) {
        currentNode.next = list1;
        list1 = list1.next;
      } else {
        currentNode.next = list2;
        list2 = list2.next;
      }
        /// Update currentNode to point the last node
        currentNode = currentNode.next!;


    }
    /// Add the remaining items in the longer list
    /// to the end of the final list
      if (list1 == null) {
        currentNode.next = list2;
      } else {
        currentNode.next = list1;
      }
    return mergedListHead;
  }
}
```