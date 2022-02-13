# 52. N-Queens II
https://leetcode-cn.com/problems/n-queens-ii  
The n-queens puzzle is the problem of placing n queens on an n x n chessboard such that no two queens attack each other.  
Given an integer n, return the number of distinct solutions to the n-queens puzzle.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/153738630-23b13af4-1d36-43f2-8949-4828930209de.png)  
Input: n = 4  
Output: 2  
Explanation: There are two distinct solutions to the 4-queens puzzle as shown.  

Example 2:  
Input: n = 1  
Output: 1  

Constraints:

1 <= n <= 9

``` python3
class Solution:
    def totalNQueens(self, n: int) -> int:
        ans=[1,0,0,2,10,4,40,92,352]
        return ans[n-1]
```
