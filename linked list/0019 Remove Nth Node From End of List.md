# 19. Remove Nth Node From End of List
https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list  
Given the head of a linked list, remove the nth node from the end of the list and return its head.

Example 1:
<img width="555" alt="image" src="https://user-images.githubusercontent.com/60777462/152930521-170f5081-9adc-4796-9ca8-12f1122ec85d.png">

Input: head = [1,2,3,4,5], n = 2  
Output: [1,2,3,5]  

Example 2:  
Input: head = [1], n = 1  
Output: []  

Example 3:  
Input: head = [1,2], n = 1   
Output: [1]  

Constraints:  
The number of nodes in the list is sz.  
1 <= sz <= 30  
0 <= Node.val <= 100  
1 <= n <= sz  

Follow up: Could you do this in one pass?  

``` python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        tmp=ListNode(0,head)
        slow=tmp
        fast=head
        for i in range(n):
            fast=fast.next
        while fast:
            slow=slow.next
            fast=fast.next
        slow.next=slow.next.next
        return tmp.next
```
