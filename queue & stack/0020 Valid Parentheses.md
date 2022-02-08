# 20. Valid Parentheses
https://leetcode-cn.com/problems/valid-parentheses  
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.  

An input string is valid if:  
Open brackets must be closed by the same type of brackets.  
Open brackets must be closed in the correct order.  
 
Example 1:  
Input: s = "()"  
Output: true  

Example 2:  
Input: s = "()[]{}"  
Output: true  

Example 3:  
Input: s = "(]"  
Output: false  

Constraints:  
1 <= s.length <= 104  
s consists of parentheses only '()[]{}'.  

``` python3
class Solution:
    def isValid(self, s: str) -> bool:
        stack=[]
        bracket={'(':')','[':']','{':'}'}
        for b in s:
            if b in bracket.keys():
                stack.append(b)
            else:
                if stack and bracket[stack[-1]]==b:
                    stack.pop()
                else:
                    return False
        if stack:
            return False
        return True
```
