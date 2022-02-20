# 102. Binary Tree Level Order Traversal
https://leetcode-cn.com/problems/binary-tree-level-order-traversal  
Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/154846257-74c7f8f8-7b1c-4ec3-83b8-7453a54a9110.png)  
Input: root = [3,9,20,null,null,15,7]  
Output: [[3],[9,20],[15,7]]  

Example 2:  
Input: root = [1]  
Output: [[1]]  

Example 3:  
Input: root = []  
Output: []  

Constraints:  
The number of nodes in the tree is in the range [0, 2000].  
-1000 <= Node.val <= 1000  

``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        que=collections.deque()
        que.append(root)
        quenext=collections.deque()
        ans,tmp=[],[]
        while que:
            node=que.popleft()
            if node:
                quenext.append(node.left)
                quenext.append(node.right)
                tmp.append(node.val)
            if not que:
                que=quenext
                quenext=collections.deque()
                if tmp:
                    ans.append(tmp)
                    tmp=[]
        return ans     
```
