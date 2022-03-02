# 237. Delete Node in a Linked List
https://leetcode-cn.com/problems/delete-node-in-a-linked-list/  
Write a function to delete a node in a singly-linked list. You will not be given access to the head of the list, instead you will be given access to the node to be deleted directly.

It is guaranteed that the node to be deleted is not a tail node in the list.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/156284381-ba9e5fbb-4b0a-4bd8-8101-a6e4f0f2ce4f.png)  
Input: head = [4,5,1,9], node = 5  
Output: [4,1,9]  
Explanation: You are given the second node with value 5, the linked list should become 4 -> 1 -> 9 after calling your function.  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/156284427-e8adf8c5-70fa-4d41-86b5-d9562d9ba4ca.png)  
Input: head = [4,5,1,9], node = 1  
Output: [4,5,9]  
Explanation: You are given the third node with value 1, the linked list should become 4 -> 5 -> 9 after calling your function.  

Constraints:  
The number of the nodes in the given list is in the range [2, 1000].  
-1000 <= Node.val <= 1000  
The value of each node in the list is unique.  
The node to be deleted is in the list and is not a tail node  

``` python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val=node.next.val
        node.next=node.next.next
```
