# 63. Unique Paths II
https://leetcode-cn.com/problems/unique-paths-ii/  
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).
The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).
Now consider if some obstacles are added to the grids. How many unique paths would there be?
An obstacle and space is marked as 1 and 0 respectively in the grid.

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/152140947-d2117169-7be2-4b26-9147-fdad6b01f9d2.png)  
Input: obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]  
Output: 2  
Explanation: There is one obstacle in the middle of the 3x3 grid above.  
There are two ways to reach the bottom-right corner:  
1. Right -> Right -> Down -> Down  
2. Down -> Down -> Right -> Right  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/152141006-67768b35-af37-411c-aeea-ccbbb3775aac.png)  
Input: obstacleGrid = [[0,1],[0,0]]  
Output: 1  

Constraints:  
m == obstacleGrid.length  
n == obstacleGrid[i].length  
1 <= m, n <= 100  
obstacleGrid[i][j] is 0 or 1.  

``` python3

class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m,n=len(obstacleGrid),len(obstacleGrid[0])
        dp=[0 for i in range(n)]
        for i in range(n):
            if obstacleGrid[0][i]!=1:
                dp[i]=1
            else:
                break
        for i in range(1,m):
            if obstacleGrid[i][0]==1:
                dp[0]=0
            for j in range(1,n):
                if obstacleGrid[i][j]!=1:
                    dp[j]+=dp[j-1]
                else:
                    dp[j]=0
        return dp[-1]

```
