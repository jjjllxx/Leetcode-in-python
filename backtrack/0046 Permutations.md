# 46. Permutations
https://leetcode-cn.com/problems/permutations   
Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.  

Example 1:  
Input: nums = [1,2,3]  
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]  

Example 2:  
Input: nums = [0,1]  
Output: [[0,1],[1,0]]  

Example 3:  
Input: nums = [1]  
Output: [[1]]  
 

Constraints:  
1 <= nums.length <= 6  
-10 <= nums[i] <= 10  
All the integers of nums are unique.  

``` python3
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res=[]
        n=len(nums)
        def trackback(start):
            if start==n:
                res.append(nums[:])
            for i in range(start,n):
                nums[i],nums[start]=nums[start],nums[i]
                trackback(start+1)
                nums[i],nums[start]=nums[start],nums[i]
        trackback(0)
        return res
```
