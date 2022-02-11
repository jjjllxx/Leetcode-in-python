# 38. Count and Say
https://leetcode-cn.com/problems/count-and-say  
The count-and-say sequence is a sequence of digit strings defined by the recursive formula:

countAndSay(1) = "1"
countAndSay(n) is the way you would "say" the digit string from countAndSay(n-1), which is then converted into a different digit string.
To determine how you "say" a digit string, split it into the minimal number of groups so that each group is a contiguous section all of the same character. Then for each group, say the number of characters, then say the character. To convert the saying into a digit string, replace the counts with a number and concatenate every saying.

For example, the saying and conversion for digit string "3322251":  
![image](https://user-images.githubusercontent.com/60777462/153570662-53a20369-aa51-44a4-858e-d6a51a464795.png)  
Given a positive integer n, return the nth term of the count-and-say sequence.  

Example 1:  
Input: n = 1  
Output: "1"  
Explanation: This is the base case.  

Example 2:
Input: n = 4  
Output: "1211"  
Explanation:  
countAndSay(1) = "1"  
countAndSay(2) = say "1" = one 1 = "11"  
countAndSay(3) = say "11" = two 1's = "21"  
countAndSay(4) = say "21" = one 2 + one 1 = "12" + "11" = "1211"  

Constraints:   
1 <= n <= 30  

``` python3
class Solution:
    def countAndSay(self, n: int) -> str:
        if n==1:
            return '1'
        else:
            str_pre='1'
            for i in range(n-1):
                str_now=''
                count=0
                num_now=str_pre[0]
                for j in str_pre:
                    if j==num_now:
                        count+=1
                    else:
                        str_now+=(str(count)+num_now)
                        count=1
                        num_now=j
                str_now+=(str(count)+num_now)
                str_pre=str_now
            return str_now
```
