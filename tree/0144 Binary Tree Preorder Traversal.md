# 144. Binary Tree Preorder Traversal
https://leetcode-cn.com/problems/binary-tree-preorder-traversal/  
Given the root of a binary tree, return the preorder traversal of its nodes' values.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/155174831-191f3a0d-aa79-428d-9094-3314e8d79b0b.png)  
Input: root = [1,null,2,3]  
Output: [1,2,3]  

Example 2:  
Input: root = []  
Output: []  

Example 3:  
Input: root = [1]  
Output: [1]  

Constraints:  
The number of nodes in the tree is in the range [0, 100].  
-100 <= Node.val <= 100  

Follow up: Recursive solution is trivial, could you do it iteratively?  

## recursion
``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        def preorder(node):
            if not node:
                return []
            res.append(node.val)
            preorder(node.left)
            preorder(node.right)
            return res
        
        res=[]
        return preorder(root)   
```
