# 59. Spiral Matrix II
https://leetcode-cn.com/problems/spiral-matrix-ii  
Given a positive integer n, generate an n x n matrix filled with elements from 1 to n2 in spiral order.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/153979100-b2e49fd0-230c-4a68-95cb-833af64cf3e3.png)  
Input: n = 3  
Output: [[1,2,3],[8,9,4],[7,6,5]]  

Example 2:  
Input: n = 1  
Output: [[1]]  

Constraints: 
1 <= n <= 20

``` python3
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        ans=[[0 for i in range(n)] for j in range(n)]
        dirs=[(0,1),(1,0),(0,-1),(-1,0)]
        nums=n*n
        row,col,no=0,-1,0
        for i in range(nums):
            ax,ay=dirs[no]
            row+=ax
            col+=ay
            ans[row][col]=i+1
            if row+ax<0 or row+ax>=n or col+ay<0 or col+ay>=n or ans[row+ax][col+ay]!=0:
                no=(no+1)%4
        return ans 
```
