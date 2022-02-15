# 73. Set Matrix Zeroes
https://leetcode-cn.com/problems/set-matrix-zeroes  
Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.  
You must do it in place.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/153980531-72481ae5-37b3-4807-8967-890a97c6585f.png)  
Input: matrix = [[1,1,1],[1,0,1],[1,1,1]]  
Output: [[1,0,1],[0,0,0],[1,0,1]]  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/153980576-ab356ee3-111b-48ff-aa7a-ae3ffe675639.png)  
Input: matrix = [[0,1,2,0],[3,4,5,2],[1,3,1,5]]  
Output: [[0,0,0,0],[0,4,5,0],[0,3,1,0]]  

Constraints:  
m == matrix.length  
n == matrix[0].length  
1 <= m, n <= 200  
-2^31 <= matrix[i][j] <= 2^31 - 1  

Follow up:  
A straightforward solution using O(mn) space is probably a bad idea.  
A simple improvement uses O(m + n) space, but still not the best solution.  
Could you devise a constant space solution?  

``` python3
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        flag_col0,flag_row0=False,False
        m,n=len(matrix),len(matrix[0])
        for i in range(m):
            if matrix[i][0]==0:
                flag_col0=True
                break
        for j in range(n):
            if matrix[0][j]==0:
                flag_row0=True
                break
        for i in range(1,m):
            for j in range(1,n):
                if matrix[i][j]==0:
                    matrix[i][0],matrix[0][j]=0,0
        for i in range(1,m):
            for j in range(1,n):
                if matrix[i][0]==0 or matrix[0][j]==0:
                    matrix[i][j]=0
        if flag_col0:
            for i in range(m):
                matrix[i][0]=0
        if flag_row0:
            for j in range(n):
                matrix[0][j]=0
```
