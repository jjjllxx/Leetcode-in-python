# 264. Ugly Number II
https://leetcode-cn.com/problems/ugly-number-ii/
An ugly number is a positive integer whose prime factors are limited to 2, 3, and 5.  
Given an integer n, return the nth ugly number.  

Example 1:  
Input: n = 10  
Output: 12  
Explanation: [1, 2, 3, 4, 5, 6, 8, 9, 10, 12] is the sequence of the first 10 ugly numbers.  

Example 2:  
Input: n = 1  
Output: 1  
Explanation: 1 has no prime factors, therefore all of its prime factors are limited to 2, 3, and 5.  

Constraints:
1 <= n <= 1690

``` python3
class Solution:
    def nthUglyNumber(self, n: int) -> int:
        dp=[0]*(n+1)
        dp[1]=1
        p2,p3,p5=1,1,1
        for i in range(2,n+1):
            num2,num3,num5=dp[p2]*2,dp[p3]*3,dp[p5]*5
            dp[i]=min(num2,num3,num5)
            if dp[i]==num2:
                p2+=1
            if dp[i]==num3:
                p3+=1
            if dp[i]==num5:
                p5+=1
        return dp[n]
```
