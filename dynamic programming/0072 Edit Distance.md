# 72. Edit Distance
https://leetcode-cn.com/problems/edit-distance  
Given two strings word1 and word2, return the minimum number of operations required to convert word1 to word2.  
You have the following three operations permitted on a word:  
Insert a character  
Delete a character  
Replace a character  

Example 1:  
Input: word1 = "horse", word2 = "ros"  
Output: 3  
Explanation:   
horse -> rorse (replace 'h' with 'r')  
rorse -> rose (remove 'r')  
rose -> ros (remove 'e')  

Example 2:  
Input: word1 = "intention", word2 = "execution"  
Output: 5  
Explanation:   
intention -> inention (remove 't')  
inention -> enention (replace 'i' with 'e')  
enention -> exention (replace 'n' with 'x')  
exention -> exection (replace 'n' with 'c')  
exection -> execution (insert 'u')  

Constraints:  
0 <= word1.length, word2.length <= 500  
word1 and word2 consist of lowercase English letters.  

``` python3
class Solution:
    def minDistance(self, word1: str, word2: str) -> int:
        m,n=len(word1),len(word2)
        dp=[i for i in range(n+1)]
        for i in range(m):
            tmp,dp[0]=dp[0],i+1
            for j in range(n):
                if word1[i]==word2[j]:
                    tmp,dp[j+1]=dp[j+1],tmp
                else:
                    tmp,dp[j+1]=dp[j+1],min(tmp,dp[j],dp[j+1])+1
        return dp[-1]

```
