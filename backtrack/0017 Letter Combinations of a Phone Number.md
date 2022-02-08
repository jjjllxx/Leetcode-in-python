# 17. Letter Combinations of a Phone Number
https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number  

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

<img width="202" alt="image" src="https://user-images.githubusercontent.com/60777462/152929525-171b6c8f-305d-41b7-b5ce-4c1520adf365.png">  

Example 1:  
Input: digits = "23"  
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]  

Example 2:  
Input: digits = ""  
Output: []  

Example 3:  
Input: digits = "2"  
Output: ["a","b","c"]   
 

Constraints:  
0 <= digits.length <= 4  
digits[i] is a digit in the range ['2', '9'].  

``` python3
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits:
            return []
        tele_dict={'1':'','2':'abc','3':'def','4':'ghi','5':'jkl','6':'mno','7':'pqrs','8':'tuv','9':'wxyz'}
        ans=list(tele_dict[digits[0]])
        for i in digits[1::]:
            tmp=[]
            for j in ans:
                for k in tele_dict[i]:
                    tmp.append(j+k)
            ans=tmp
        return ans
```
