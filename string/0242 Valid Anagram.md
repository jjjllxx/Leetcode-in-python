# 242. Valid Anagram
https://leetcode-cn.com/problems/valid-anagram/  
Given two strings s and t, return true if t is an anagram of s, and false otherwise.  
An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.  

Example 1:    
Input: s = "anagram", t = "nagaram"   
Output: true  

Example 2:  
Input: s = "rat", t = "car"  
Output: false  

Constraints:  
1 <= s.length, t.length <= 5 * 10^4  
s and t consist of lowercase English letters.  

Follow up: What if the inputs contain Unicode characters? How would you adapt your solution to such a case?  

``` python3
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s)!=len(t):
            return False
        s_dict=Counter(s)
        t_dict=Counter(t)
        for k,v in s_dict.items():
            if k not in t_dict.keys() or t_dict[k]!=v:
                return False
        return True
```
