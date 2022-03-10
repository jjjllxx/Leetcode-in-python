# 409. Longest Palindrome
https://leetcode-cn.com/problems/longest-palindrome/  
Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.  
Letters are case sensitive, for example, "Aa" is not considered a palindrome here.   

Example 1:  
Input: s = "abccccdd"  
Output: 7  
Explanation:  
One longest palindrome that can be built is "dccaccd", whose length is 7.  

Example 2:  
Input: s = "a"  
Output: 1  

Example 3:  
Input: s = "bb"  
Output: 2  

Constraints:  
1 <= s.length <= 2000  
s consists of lowercase and/or uppercase English letters only.  

``` python3
class Solution:
    def longestPalindrome(self, s: str) -> int:
        d=collections.Counter(s)
        ans=0
        for k in d:
            ans+=d[k]//2*2
        if ans<len(s):
            ans+=1
        return ans
```
