# 7. Reverse Integer
https://leetcode-cn.com/problems/reverse-integer/  
Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-2^31, 2^31 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).


Example 1:
Input: x = 123
Output: 321

Example 2:
Input: x = -123
Output: -321

Example 3:
Input: x = 120
Output: 21  
  
Constraints:  
-2^31 <= x <= 2^31 - 1


``` python3

class Solution:
    def reverse(self, x: int) -> int:
        if x<0:
            ans=-int(str(x)[:0:-1])
        else:
            ans=int(str(x)[::-1])
        if ans<-2**31 or ans>=2**31:
            return 0
        return ans
        
```