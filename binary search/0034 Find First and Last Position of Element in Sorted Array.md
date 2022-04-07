# 34. Find First and Last Position of Element in Sorted Array
https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array  
Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.  

If target is not found in the array, return [-1, -1].  

You must write an algorithm with O(log n) runtime complexity.  


Example 1:  
Input: nums = [5,7,7,8,8,10], target = 8  
Output: [3,4]  

Example 2:  
Input: nums = [5,7,7,8,8,10], target = 6  
Output: [-1,-1]  

Example 3:  
Input: nums = [], target = 0  
Output: [-1,-1]  

Constraints:
0 <= nums.length <= 10^5  
-10^9 <= nums[i] <= 10^9  
nums is a non-decreasing array.  
-10^9 <= target <= 10^9  

``` python3
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        def biSearch(nums, target):
            left, right = 0, len(nums) - 1
            while left <= right:
                mid = (left + right) // 2
                if nums[mid] >= target:
                    right = mid - 1
                else:
                    left = mid + 1
            return left
        a = biSearch(nums, target)
        b = biSearch(nums, target + 1)
        if a == len(nums) or nums[a] != target:
            return [-1, -1]
        else:
            return [a, b - 1]
```
