# 400. Nth Digit
https://leetcode-cn.com/problems/nth-digit/  
Given an integer n, return the nth digit of the infinite integer sequence [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ...].   

Example 1:  
Input: n = 3  
Output: 3  

Example 2:  
Input: n = 11  
Output: 0  
Explanation: The 11th digit of the sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... is a 0, which is part of the number 10.  

Constraints:   
1 <= n <= 2^31 - 1  

``` python3
class Solution:
    def findNthDigit(self, n: int) -> int:
        pos=0
        while True:
            if n>9*10**pos*(pos+1):
                n=n-9*10**pos*(pos+1)
                pos+=1
            else:
                ans=str(10**pos+(n-1)//(pos+1))
                return int(ans[(n-1)%(pos+1)])
```
