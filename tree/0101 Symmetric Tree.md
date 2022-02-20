# 101. Symmetric Tree
https://leetcode-cn.com/problems/symmetric-tree/  
Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/154846114-b69b0a84-2c74-4cc5-aa51-8869d69b1fec.png)  
Input: root = [1,2,2,3,4,4,3]  
Output: true  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/154846131-e2b7307e-5b8e-460c-8a02-ce05f30bc001.png)  
Input: root = [1,2,2,null,3,null,3]  
Output: false  

Constraints:  
The number of nodes in the tree is in the range [1, 1000].  
-100 <= Node.val <= 100  

Follow up: Could you solve it both recursively and iteratively?  

## iteration
``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        que=collections.deque()
        que.append(root)
        quenext=collections.deque()
        while que:
            node=que.popleft()
            if node:
                quenext.append(node.left)
                quenext.append(node.right)
            if not que:
                n=len(quenext)
                if n%2:
                    return False
                for i in range(n//2):
                    head,tail=quenext[i],quenext[n-i-1]
                    if (not head and tail) or (head and not tail):
                        return False
                    if head and tail and (head.val!=tail.val):
                        return False
                que=quenext
                quenext=collections.deque()
        return True
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
    def isSymmetric(self, root: TreeNode) -> bool:
        def compare(node1,node2):
            if not node1 and not node2:
                return True
            elif not node1 or not node2:
                return False
            elif node2.val!=node1.val:
                return False
            return compare(node1.left,node2.right) and compare(node1.right,node2.left)
        return compare(root.left,root.right)
```
