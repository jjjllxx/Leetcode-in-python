# 118. Pascal's Triangle
Given an integer numRows, return the first numRows of Pascal's triangle.  
In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:  

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/154854747-c5eab2ca-754a-47b8-ae1a-87eafce84012.png)  
Input: numRows = 5  
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]  

Example 2:  
Input: numRows = 1  
Output: [[1]]  

Constraints:  
1 <= numRows <= 30  

``` python3
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        if numRows==1:
            return [[1]]
        triangle=[[1]]
        for i in range(1,numRows):
            former=triangle[i-1]
            new=[1]
            for j in range(i-1):
                new.append(former[j]+former[j+1])
            new.append(1)
            triangle.append(new)
        return triangle
```
