# 22. Generate Parentheses
https://leetcode-cn.com/problems/generate-parentheses  
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.  

Example 1:  
Input: n = 3  
Output: ["((()))","(()())","(())()","()(())","()()()"]  

Example 2:  
Input: n = 1  
Output: ["()"]  

Constraints:  
1 <= n <= 8  

``` python3
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        ans,stk=[],[]
        def backtrack(n,left,right):
            if left+right==n*2:
                ans.append(''.join(stk))
                return
            if left<n:
                stk.append('(')
                backtrack(n,left+1,right)
                stk.pop()
            if right<left:
                stk.append(')')
                backtrack(n,left,right+1)
                stk.pop()
        backtrack(n,0,0)
        return ans
```
