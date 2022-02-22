# 145. Binary Tree Postorder Traversal
https://leetcode-cn.com/problems/binary-tree-postorder-traversal/  
Given the root of a binary tree, return the postorder traversal of its nodes' values.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/155175412-0ed669ed-e068-4a29-af45-054821659647.png)  
Input: root = [1,null,2,3]  
Output: [3,2,1]  

Example 2:   
Input: root = []  
Output: []  

Example 3:  
Input: root = [1]  
Output: [1]  

Constraints:  
The number of the nodes in the tree is in the range [0, 100].  
-100 <= Node.val <= 100  

Follow up: Recursive solution is trivial, could you do it iteratively?  

``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        res=[]
        def postorder(node):
            if not node:
                return []
            postorder(node.left)
            postorder(node.right)
            res.append(node.val)
            return res
        return postorder(root)
```
