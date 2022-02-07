# 14. Longest Common Prefix
https://leetcode-cn.com/problems/longest-common-prefix  

Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string "".


Example 1:  
Input: strs = ["flower","flow","flight"]  
Output: "fl"  

Example 2:  
Input: strs = ["dog","racecar","car"]  
Output: ""  
Explanation: There is no common prefix among the input strings.  
 

Constraints:  
1 <= strs.length <= 200  
0 <= strs[i].length <= 200  
strs[i] consists of only lower-case English letters.  

``` python3
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        n=len(strs[0])
        for i in range(n):
            now=strs[0][i]
            for word in strs:
                if i>=len(word) or word[i]!=now:
                    return strs[0][:i:]
        return strs[0]
```
