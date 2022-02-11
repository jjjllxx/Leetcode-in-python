# 35. Search Insert Position
https://leetcode-cn.com/problems/search-insert-position  
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.  
You must write an algorithm with O(log n) runtime complexity.

Example 1:  
Input: nums = [1,3,5,6], target = 5  
Output: 2  

Example 2:  
Input: nums = [1,3,5,6], target = 2  
Output: 1  

Example 3:  
Input: nums = [1,3,5,6], target = 7  
Output: 4  

Constraints:  
1 <= nums.length <= 10^4  
-10^4 <= nums[i] <= 10^4  
nums contains distinct values sorted in ascending order.  
-10^4 <= target <= 10^4  

``` python3
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        if target<=nums[0]:
            return 0
        if target>nums[-1]:
            return len(nums)
        left,right=1,len(nums)-1
        while left<=right:
            middle=(left+right)//2
            if nums[middle-1]<target<=nums[middle]:
                return middle
            if nums[middle]<target:
                left=middle+1
            else:
                right=middle-1
            


```
