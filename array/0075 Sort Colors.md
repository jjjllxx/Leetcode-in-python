# 75. Sort Colors
https://leetcode-cn.com/problems/sort-colors
Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.  
We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.  
You must solve this problem without using the library's sort function.  

Example 1:  
Input: nums = [2,0,2,1,1,0]  
Output: [0,0,1,1,2,2]  

Example 2:  
Input: nums = [2,0,1]  
Output: [0,1,2]  

Constraints:  
n == nums.length  
1 <= n <= 300  
nums[i] is either 0, 1, or 2.  

Follow up: Could you come up with a one-pass algorithm using only constant extra space?

## pointer
``` python3
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n=len(nums)
        ptr=0
        for i in range(n):
            if nums[i]==0:
                nums[ptr],nums[i]=nums[i],nums[ptr]
                ptr+=1
        
        for i in range(n):
            if nums[i]==1:
                nums[ptr],nums[i]=nums[i],nums[ptr]
                ptr+=1    
```

## quick sort
``` python3
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n=len(nums)
        for i in range(1,n):
            j=i
            color=nums[i]
            while color<nums[j-1] and j>0:
                nums[j]=nums[j-1]
                j-=1
            nums[j]=color
```
