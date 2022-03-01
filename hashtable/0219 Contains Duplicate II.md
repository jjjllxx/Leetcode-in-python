# 219. Contains Duplicate II
https://leetcode-cn.com/problems/contains-duplicate-ii/  
Given an integer array nums and an integer k, return true if there are two distinct indices i and j in the array such that nums[i] == nums[j] and abs(i - j) <= k.  

Example 1:  
Input: nums = [1,2,3,1], k = 3  
Output: true  

Example 2:  
Input: nums = [1,0,1,1], k = 1  
Output: true  

Example 3:   
Input: nums = [1,2,3,1,2,3], k = 2  
Output: false  

Constraints:  
1 <= nums.length <= 10^5  
-10^9 <= nums[i] <= 10^9  
0 <= k <= 10^5  

``` python3
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        pos_dict,n={},len(nums)
        for i in range(n):
            if nums[i] in pos_dict and i-pos_dict[nums[i]]<=k:
                return True
            pos_dict[nums[i]]=i
        return False
```
