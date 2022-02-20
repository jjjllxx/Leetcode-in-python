# 104. Maximum Depth of Binary Tree
https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/  
Given the root of a binary tree, return its maximum depth.  
A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.  

Example 1:   
![image](https://user-images.githubusercontent.com/60777462/154846541-7120101b-1e6b-410b-92b2-5d31bac99684.png)  
Input: root = [3,9,20,null,null,15,7]  
Output: 3  

Example 2:  
Input: root = [1,null,2]  
Output: 2  

Constraints:  
The number of nodes in the tree is in the range [0, 104].  
-100 <= Node.val <= 100  

## iteration
``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root: return 0
        depth,queue=0,[root]
        while queue:
            tmp=[]
            for node in queue:
                if node.left: 
                    tmp.append(node.left)
                if node.right:
                    tmp.append(node.right)
            queue=tmp
            depth+=1
        return depth
```

## recursion
``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        def dfs(node):
            if not node:
                return 0
            return max(dfs(node.left),dfs(node.right))+1
        return dfs(root)
```
