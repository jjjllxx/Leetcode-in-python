# 45. Jump Game II
https://leetcode-cn.com/problems/jump-game-ii  
Given an array of non-negative integers nums, you are initially positioned at the first index of the array.
Each element in the array represents your maximum jump length at that position.
Your goal is to reach the last index in the minimum number of jumps.
You can assume that you can always reach the last index.

Example 1:  
Input: nums = [2,3,1,1,4]  
Output: 2  
Explanation: The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.  

Example 2:  
Input: nums = [2,3,0,1,4]  
Output: 2  
 

Constraints:    
1 <= nums.length <= 10^4  
0 <= nums[i] <= 1000  

## dynamic programming
``` python3
class Solution:
    def jump(self, nums: List[int]) -> int:
        first,second,n,step=0,0,len(nums)-1,1
        for i in range(n):
            if i>first:
                first,second=second,nums[second]+second
                step+=1 
            second=max(second,i+nums[i])
            if second>=n:
                return step
        return 0
```

## violence
``` python3
class Solution:
    def jump(self, nums: List[int]) -> int:
        n=len(nums)
        dp=[n]*n
        dp[0]=0
        for i in range(n-1):
            for j in range(1,nums[i]+1):
                if i+j<n:
                    if dp[i+j]>dp[i]+1:
                        dp[i+j]=dp[i]+1
        return dp[-1]
```
