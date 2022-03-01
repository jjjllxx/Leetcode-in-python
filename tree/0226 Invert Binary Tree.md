# 226. Invert Binary Tree
https://leetcode-cn.com/problems/invert-binary-tree/  
Given the root of a binary tree, invert the tree, and return its root.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/156178553-b325741c-a946-42b3-8176-a23f45b727d5.png)  
Input: root = [4,2,7,1,3,6,9]  
Output: [4,7,2,9,6,3,1]  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/156178632-5880ff72-5eda-42ae-add1-a5c0b886c87d.png)  
Input: root = [2,1,3]  
Output: [2,3,1]  

Example 3:  
Input: root = []  
Output: []  

Constraints:  
The number of nodes in the tree is in the range [0, 100].  
-100 <= Node.val <= 100  

``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        if not root:
            return root
        left=self.invertTree(root.left)
        right=self.invertTree(root.right)
        root.left,root.right=right,left
        return root
```

``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        def invert(node):
            if not node:
                return
            invert(node.left)
            invert(node.right)
            node.left,node.right=node.right,node.left
        invert(root)
        return root
```
