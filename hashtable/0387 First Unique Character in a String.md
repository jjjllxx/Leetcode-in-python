# 387. First Unique Character in a String
https://leetcode-cn.com/problems/first-unique-character-in-a-string/  
Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.

Example 1:  
Input: s = "leetcode"  
Output: 0   

Example 2:  
Input: s = "loveleetcode"  
Output: 2  

Example 3:  
Input: s = "aabb"   
Output: -1  

Constraints:   
1 <= s.length <= 10^5   
s consists of only lowercase English letters.  

``` python3
class Solution:
    def firstUniqChar(self, s: str) -> int:
        char_dict=defaultdict(list)
        n=len(s)
        for i in range(n):
            char_dict[s[i]].append(i)
        ans=n
        for k,v in char_dict.items():
            if len(v)==1:
                ans=min(ans,v[0])
        if ans==n:
            return -1
        else:
            return ans
```
