# 189. Rotate Array
https://leetcode-cn.com/problems/rotate-array/  
Given an array, rotate the array to the right by k steps, where k is non-negative.  

Example 1:  
Input: nums = [1,2,3,4,5,6,7], k = 3  
Output: [5,6,7,1,2,3,4]  
Explanation:  
rotate 1 steps to the right: [7,1,2,3,4,5,6]  
rotate 2 steps to the right: [6,7,1,2,3,4,5]  
rotate 3 steps to the right: [5,6,7,1,2,3,4]  

Example 2:  
Input: nums = [-1,-100,3,99], k = 2  
Output: [3,99,-1,-100]  
Explanation:   
rotate 1 steps to the right: [99,-1,-100,3]  
rotate 2 steps to the right: [3,99,-1,-100]  

Constraints:  
1 <= nums.length <= 10^5  
-2^31 <= nums[i] <= 2^31 - 1  
0 <= k <= 10^5  

Follow up:  
Try to come up with as many solutions as you can. There are at least three different ways to solve this problem.  
Could you do it in-place with O(1) extra space?  

``` python3
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n=len(nums)
        k=k % n
        def reverse(l,left,right):
            while left<right:
                nums[left],nums[right]=nums[right],nums[left]
                left+=1
                right-=1
        reverse(nums,0,n-1)
        reverse(nums,0,k-1)
        reverse(nums,k,n-1)
```
