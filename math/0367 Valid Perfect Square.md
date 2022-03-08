# 367. Valid Perfect Square
https://leetcode-cn.com/problems/valid-perfect-square/  
Given a positive integer num, write a function which returns True if num is a perfect square else False.  
Follow up: Do not use any built-in library function such as sqrt.   


Example 1:  
Input: num = 16  
Output: true  

Example 2:   
Input: num = 14  
Output: false  

Constraints:  
1 <= num <= 2^31 - 1  

``` python3
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        x0=num
        while True:
            x1=0.5*(x0+num/x0)
            if x0-x1<1e-7:
                break
            x0=x1
        return int(x0)*int(x0)==num 
```
