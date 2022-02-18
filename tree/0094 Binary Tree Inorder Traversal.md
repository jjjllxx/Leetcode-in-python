# 94. Binary Tree Inorder Traversal
Given the root of a binary tree, return the inorder traversal of its nodes' values.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/154602074-c4194021-740e-47f7-9881-d62aafccfa45.png)  
Input: root = [1,null,2,3]  
Output: [1,3,2]  

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

``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        def inorder(node):
            if not node:
                return []
            inorder(node.left)
            res.append(node.val)
            inorder(node.right)
            return res

        res=[]
        return inorder(root)
```
