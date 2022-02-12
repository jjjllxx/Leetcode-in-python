# 547. Number of Provinces
https://leetcode-cn.com/problems/number-of-provinces  
There are n cities. Some of them are connected, while some are not. If city a is connected directly with city b, and city b is connected directly with city c, then city a is connected indirectly with city c.

A province is a group of directly or indirectly connected cities and no other cities outside of the group.

You are given an n x n matrix isConnected where isConnected[i][j] = 1 if the ith city and the jth city are directly connected, and isConnected[i][j] = 0 otherwise.

Return the total number of provinces.


Example 1:  
<img width="237" alt="image" src="https://user-images.githubusercontent.com/60777462/153696564-314ee26f-78a9-4a48-ad08-dc0b5dbfc3f9.png">  
Input: isConnected = [[1,1,0],[1,1,0],[0,0,1]]  
Output: 2  

Example 2:   
<img width="233" alt="image" src="https://user-images.githubusercontent.com/60777462/153696577-1bc96088-2f98-4768-b60a-8681bcb875d3.png">  
Input: isConnected = [[1,0,0],[0,1,0],[0,0,1]]  
Output: 3   

Constraints:  
1 <= n <= 200  
n == isConnected.length  
n == isConnected[i].length  
isConnected[i][j] is 1 or 0.  
isConnected[i][i] == 1  
isConnected[i][j] == isConnected[j][i]   

## BFS
``` python3
class Solution:
    def findCircleNum(self, isConnected: List[List[int]]) -> int:
        n=len(isConnected)
        visited=[0]*n
        ans=0
        for i in range(n):
            if visited[i]==0:
                ans+=1
                q=collections.deque([i])
                visited[i]=1
                while q:
                    now=q.popleft()
                    rel=isConnected[now]
                    for j in range(n):
                        if rel[j]==1 and visited[j]==0:
                            q.append(j)
                            visited[j]=1
        return ans
```
