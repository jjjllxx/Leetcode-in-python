# 120. Triangle
https://leetcode-cn.com/problems/triangle/   
Given a triangle array, return the minimum path sum from top to bottom.

For each step, you may move to an adjacent number of the row below. More formally, if you are on index i on the current row, you may move to either index i or index i + 1 on the next row.

Example 1:  
Input: triangle = [[2],[3,4],[6,5,7],[4,1,8,3]]  
Output: 11  
Explanation: The triangle looks like:  
   2  
  3 4  
 6 5 7  
4 1 8 3  
The minimum path sum from top to bottom is 2 + 3 + 5 + 1 = 11.  

Example 2:  
Input: triangle = [[-10]]  
Output: -10  

Constraints:  
1 <= triangle.length <= 200  
triangle[0].length == 1  
triangle[i].length == triangle[i - 1].length + 1  
-10^4 <= triangle[i][j] <= 10^4  

Follow up: Could you do this using only O(n) extra space, where n is the total number of rows in the triangle?  

``` python3
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        n=len(triangle)
        for i in range(1,n):
            last,now=triangle[i-1],triangle[i]
            m=len(now)
            for j in range(1,m-1):
                now[j]+=min(last[j],last[j-1])
            now[0]+=last[0]
            now[-1]+=last[-1]
        return min(triangle[-1])
```
