# 5. Longest Palindromic Substring  
https://leetcode-cn.com/problems/longest-palindromic-substring/

Given a string s, return the longest palindromic substring in s.  

Example 1:  
Input: s = "babad"  
Output: "bab"  
Explanation: "aba" is also a valid answer.  

Example 2:  
Input: s = "cbbd"  
Output: "bb"  
 

Constraints:  
1 <= s.length <= 1000  
s consist of only digits and English letters.  


``` python3

class Solution:
    def longestPalindrome(self, s: str) -> str:
        def isPalindrome(center,s0):
            left1,right1=center-1,center
            while left1>=0 and right1<len(s0) and s0[left1]==s0[right1]:
                left1-=1
                right1+=1

            left2,right2=center-1,center+1
            while left2>=0 and right2<len(s0) and s0[left2]==s0[right2]:
                left2-=1
                right2+=1
            
            if right1-left1>right2-left2:
                return s0[left1+1:right1]
            return s0[left2+1:right2]

        ans=''
        for i in range(len(s)):
            word=isPalindrome(i,s)
            if len(word)>len(ans):
                ans=word
        return ans
        
```
