# 206. Reverse Linked List
https://leetcode-cn.com/problems/reverse-linked-list/  
Given the head of a singly linked list, reverse the list, and return the reversed list.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/155854779-406b4657-ac7f-47bd-afef-3631bf5b3f06.png)  
Input: head = [1,2,3,4,5]  
Output: [5,4,3,2,1]  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/155854785-70528cc9-f990-48de-93ef-1629967a4c82.png)  
Input: head = [1,2]  
Output: [2,1]  

Example 3:  
Input: head = []  
Output: []  

Constraints:  
The number of nodes in the list is the range [0, 5000].  
-5000 <= Node.val <= 5000  

Follow up: A linked list can be reversed either iteratively or recursively. Could you implement both?

## iteration
``` python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        if not head or not head.next:
            return head
        prev=None
        cur=head
        while cur:
            tmp=cur.next
            cur.next=prev
            prev=cur
            cur=tmp
        return prev
```

## recursion
``` python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        if not head or not head.next:
            return head

        newHead = self.reverseList(head.next)
        head.next.next = head
        head.next = None
        return newHead   
```
