# 203. Remove Linked List Elements
https://leetcode-cn.com/problems/remove-linked-list-elements/  
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/155854572-022735f7-5539-4de2-b2ee-79a222d28f1d.png)  
Input: head = [1,2,6,3,4,5,6], val = 6  
Output: [1,2,3,4,5]  

Example 2:  
Input: head = [], val = 1  
Output: []  

Example 3:  
Input: head = [7,7,7,7], val = 7  
Output: []  

Constraints:  
The number of nodes in the list is in the range [0, 10^4].  
1 <= Node.val <= 50  
0 <= val <= 50  

``` python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeElements(self, head: ListNode, val: int) -> ListNode:
        dummyhead=ListNode(-1,head)
        p1=dummyhead
        while p1.next:
            if p1.next.val==val:
                p1.next=p1.next.next
            else:
                p1=p1.next
        return dummyhead.next
```
