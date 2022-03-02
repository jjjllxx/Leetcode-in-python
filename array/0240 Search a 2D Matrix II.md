# 240. Search a 2D Matrix II
https://leetcode-cn.com/problems/search-a-2d-matrix-ii/  
Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:  
Integers in each row are sorted in ascending from left to right.  
Integers in each column are sorted in ascending from top to bottom.  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/156414714-e3b19bd8-0cad-4e40-b3d6-afd07cf9156d.png)  
Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5  
Output: true  

Example 2:  
![image](https://user-images.githubusercontent.com/60777462/156414794-7618be61-c653-4010-ac66-92fcc3ef30c7.png)  
Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 20  
Output: false  

Constraints:  
m == matrix.length  
n == matrix[i].length  
1 <= n, m <= 300  
-109 <= matrix[i][j] <= 10^9  
All the integers in each row are sorted in ascending order.  
All the integers in each column are sorted in ascending order.  
-10^9 <= target <= 10^9  

``` python3
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        m,n=len(matrix),len(matrix[0])
        x,y=0,n-1
        while x<m and y>=0:
            if matrix[x][y]==target:
                return True
            if matrix[x][y]>target:
                y-=1
            else:
                x+=1
        return False
```
