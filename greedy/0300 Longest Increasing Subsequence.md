# 300. Longest Increasing Subsequence
https://leetcode-cn.com/problems/longest-increasing-subsequence/  
Given an integer array nums, return the length of the longest strictly increasing subsequence.  
A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, [3,6,2,7] is a subsequence of the array [0,3,1,6,2,2,7].

Example 1:  
Input: nums = [10,9,2,5,3,7,101,18]  
Output: 4  
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.  

Example 2:  
Input: nums = [0,1,0,3,2,3]  
Output: 4  

Example 3:  
Input: nums = [7,7,7,7,7,7,7]  
Output: 1  

Constraints:  
1 <= nums.length <= 2500  
-10^4 <= nums[i] <= 10^4  

Follow up: Can you come up with an algorithm that runs in O(n log(n)) time complexity?    

``` python3
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        bucket=[]
        ans=0
        for num in nums:
            if not bucket or bucket[-1]<num:
                bucket.append(num)
                ans+=1
            else:
                i=ans-1
                while i>=0 and num<=bucket[i]:
                    i-=1
                bucket[i+1]=num
        return ans
```
