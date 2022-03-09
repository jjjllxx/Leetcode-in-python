# 383. Ransom Note
https://leetcode-cn.com/problems/ransom-note/  
Given two strings ransomNote and magazine, return true if ransomNote can be constructed from magazine and false otherwise.  
Each letter in magazine can only be used once in ransomNote.  

Example 1:  
Input: ransomNote = "a", magazine = "b"  
Output: false  

Example 2:  
Input: ransomNote = "aa", magazine = "ab"  
Output: false  

Example 3:   
Input: ransomNote = "aa", magazine = "aab"  
Output: true  

Constraints:   
1 <= ransomNote.length, magazine.length <= 10^5  
ransomNote and magazine consist of lowercase English letters.  

## hashtable
``` python3
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        note_dict=Counter(ransomNote)
        maga_dict=Counter(magazine)
        for k,v in note_dict.items():
            if k not in maga_dict.keys() or maga_dict[k]<v:
                return False
        return True
```

## bucket
``` python3
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        note_dict=defaultdict(int)
        for i in ransomNote:
            note_dict[i]+=1
        maga_dict=defaultdict(int)
        for i in magazine:
            maga_dict[i]+=1
        for i in ransomNote:
            if i not in maga_dict or note_dict[i]>maga_dict[i]:
                return False
        return True
```

