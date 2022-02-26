# 207. Course Schedule
https://leetcode-cn.com/problems/course-schedule/  
There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.
For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.  
Return true if you can finish all courses. Otherwise, return false.  

Example 1:  
Input: numCourses = 2, prerequisites = [[1,0]]  
Output: true  
Explanation: There are a total of 2 courses to take.   
To take course 1 you should have finished course 0. So it is possible.  

Example 2:  
Input: numCourses = 2, prerequisites = [[1,0],[0,1]]  
Output: false  
Explanation: There are a total of 2 courses to take.   
To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.  

Constraints:  
1 <= numCourses <= 10^5  
0 <= prerequisites.length <= 5000  
prerequisites[i].length == 2  
0 <= ai, bi < numCourses  
All the pairs prerequisites[i] are unique.  

## topological sort
``` python3
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        if len(prerequisites)==0:
            return True
        pre=collections.defaultdict(list)
        inedge=[0]*numCourses
        for k,v in prerequisites:
            pre[v].append(k)
            inedge[k]+=1
        que=collections.deque([i for i in range(numCourses) if inedge[i]==0])
        learned=len(que)
        while que:
            x=que.popleft()
            for i in pre[x]:
                inedge[i]-=1
                if inedge[i]==0:
                    que.append(i)
                    learned+=1
        return learned==numCourses           
```
