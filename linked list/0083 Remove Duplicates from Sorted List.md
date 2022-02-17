# 83. Remove Duplicates from Sorted List
https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list  
Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/154484436-138dcd5c-63de-4dd5-a397-9ccb3ed1409d.png)  
Input: head = [1,1,2]  
Output: [1,2]  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/154484485-f6a8d0ff-8acc-453e-8173-ec5ff8ca80a2.png)  
Input: head = [1,1,2,3,3]  
Output: [1,2,3]  

Constraints:  
The number of nodes in the list is in the range [0, 300].  
-100 <= Node.val <= 100  
The list is guaranteed to be sorted in ascending order.  

``` python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        dummyhead=ListNode(-101,head)
        pre,cur=dummyhead,head
        while cur:
            if pre.val==cur.val:
                pre.next=cur.next
                cur=pre.next
            else:
                pre=pre.next
                cur=cur.next
        return dummyhead.next
```
