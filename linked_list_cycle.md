# Linked List Cycle
>Given head, the head of a linked list, determine if the linked list has a cycle in it. There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Return true if there is a cycle in the linked list. Otherwise, return false.

## Example 1:
```
Input: head = [3,2,0,-4]
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
```
## Example 2:
```
Input: head = [1,2]
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.
```
## Example 3:
```
Input: head = [1]
Output: false
Explanation: There is no cycle in the linked list.
```

## Dart
#### Solution
*Leetcode didn't support dart for this problem*


## Python
#### Solution
*Time complexity: O(n)*

*Space complexity: O(1)*
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        # Create two pointers fastPointer and slowPointer
        fastPointer=head
        slowPointer=head
        while(fastPointer!=None and fastPointer.next!=None):
            # Increment fastPointer by 2
            fastPointer=fastPointer.next.next
            # Increment slowPointer by 1
            slowPointer=slowPointer.next
            # If these two pointers overlap means we have cycle
            if fastPointer==slowPointer:
                return True
        # If the loop ends without returning true
        # no cycle
        return False
```
