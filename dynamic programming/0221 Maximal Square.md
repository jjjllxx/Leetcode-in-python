# 221. Maximal Square
https://leetcode-cn.com/problems/maximal-square/  
Given an m x n binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/156177179-68c086c2-a98d-4e6f-83c2-dabc0df67be6.png)  
Input: matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]  
Output: 4  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/156177366-eda49678-8c71-4965-9197-4ce7aef917b3.png)  
Input: matrix = [["0","1"],["1","0"]]  
Output: 1  

Example 3:  
Input: matrix = [["0"]]  
Output: 0  

Constraints:  
m == matrix.length  
n == matrix[i].length  
1 <= m, n <= 300  
matrix[i][j] is '0' or '1'.  

``` python3
class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        m,n=len(matrix),len(matrix[0])
        ans=0
        dp=[[0 for i in range(n)] for j in range(m)]
        for i in range(m):
            for j in range(n):
                if matrix[i][j]=='1':
                    if i==0 or j==0:
                        dp[i][j]=1
                    else:
                        dp[i][j]=min(dp[i-1][j-1],dp[i-1][j],dp[i][j-1])+1
                    ans=max(dp[i][j],ans)
        return ans*ans
```
