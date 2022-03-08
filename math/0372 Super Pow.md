# 372. Super Pow
https://leetcode-cn.com/problems/super-pow/  
Your task is to calculate ab mod 1337 where a is a positive integer and b is an extremely large positive integer given in the form of an array.  

Example 1:  
Input: a = 2, b = [3]  
Output: 8  

Example 2:  
Input: a = 2, b = [1,0]  
Output: 1024  

Example 3:  
Input: a = 1, b = [4,3,3,8,5,2]  
Output: 1  

Constraints:  
1 <= a <= 2^31 - 1  
1 <= b.length <= 2000  
0 <= b[i] <= 9  
b does not contain leading zeros.  

``` python3
class Solution:
    def superPow(self, a: int, b: List[int]) -> int:
        base = 1337
        ans = 1
        for e in b:
            ans = pow(ans, 10, base) * pow(a, e, base) % base
        return ans
```
