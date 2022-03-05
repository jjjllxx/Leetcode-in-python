# 283. Move Zeroes
https://leetcode-cn.com/problems/move-zeroes/  
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.  
Note that you must do this in-place without making a copy of the array.  

Example 1:  
Input: nums = [0,1,0,3,12]  
Output: [1,3,12,0,0]  

Example 2:  
Input: nums = [0]  
Output: [0]  

Constraints:  
1 <= nums.length <= 10^4
-2^31 <= nums[i] <= 2^31 - 1
 

Follow up: Could you minimize the total number of operations done?

``` python3
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        slow,fast,n=0,1,len(nums)
        while fast<n:
            if nums[slow]==0 and nums[fast]!=0:
                nums[slow],nums[fast]=nums[fast],nums[slow]
            if nums[slow]!=0:
                slow+=1
            if nums[fast]==0 or fast<=slow:
                fast+=1
```
