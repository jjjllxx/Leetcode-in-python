# 997. Find the Town Judge
https://leetcode-cn.com/problems/find-the-town-judge  
In a town, there are n people labeled from 1 to n. There is a rumor that one of these people is secretly the town judge.  
If the town judge exists, then:The town judge trusts nobody.  
Everybody (except for the town judge) trusts the town judge.  
There is exactly one person that satisfies properties 1 and 2.  
You are given an array trust where trust[i] = [ai, bi] representing that the person labeled ai trusts the person labeled bi.  
Return the label of the town judge if the town judge exists and can be identified, or return -1 otherwise.  


Example 1:  
Input: n = 2, trust = [[1,2]]  
Output: 2  

Example 2:  
Input: n = 3, trust = [[1,3],[2,3]]  
Output: 3  

Example 3:  
Input: n = 3, trust = [[1,3],[2,3],[3,1]]  
Output: -1  

Constraints:  
1 <= n <= 1000  
0 <= trust.length <= 10^4  
trust[i].length == 2  
All the pairs of trust are unique.  
ai != bi  
1 <= ai, bi <= n  

``` python3
class Solution:
    def findJudge(self, n: int, trust: List[List[int]]) -> int:
        inedge,outedge=[0]*n,[0]*n
        for t in trust:
            inedge[t[1]-1]+=1
            outedge[t[0]-1]+=1
        for i in range(n):
            if inedge[i]==n-1 and outedge[i]==0:
                return i+1
        return -1

```
