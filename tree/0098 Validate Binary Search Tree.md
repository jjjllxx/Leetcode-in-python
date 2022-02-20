# 98. Validate Binary Search Tree
https://leetcode-cn.com/problems/validate-binary-search-tree/  
Given the root of a binary tree, determine if it is a valid binary search tree (BST).  
A valid BST is defined as follows:   
The left subtree of a node contains only nodes with keys less than the node's key.  
The right subtree of a node contains only nodes with keys greater than the node's key.  
Both the left and right subtrees must also be binary search trees.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/154845799-7454ea26-e88d-4402-ba39-c95b2ef88e96.png)  
Input: root = [2,1,3]  
Output: true  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/154845822-c6db0fe3-7a3e-4e68-b8e6-84613a3012a2.png)  
Input: root = [5,1,4,null,null,3,6]  
Output: false  
Explanation: The root node's value is 5 but its right child's value is 4.  

Constraints:
The number of nodes in the tree is in the range [1, 10^4].  
-2^31 <= Node.val <= 2^31 - 1  

``` python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        stack,inorder=[],float('-inf')
        while stack or root:
            while root:
                stack.append(root)
                root=root.left
            root=stack.pop()
            if root.val<=inorder:
                return False
            inorder=root.val
            root=root.right
        return True    
```
