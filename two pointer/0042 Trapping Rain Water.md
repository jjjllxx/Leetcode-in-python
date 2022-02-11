# 42. Trapping Rain Water
https://leetcode-cn.com/problems/trapping-rain-water  
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

Example 1:  
![image](https://user-images.githubusercontent.com/60777462/153572047-5dd74d26-ccf4-4fd4-9ab0-9da0c4349d64.png)  
Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]  
Output: 6    
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.  

Example 2:  
Input: height = [4,2,0,3,2,5]  
Output: 9  

Constraints:  
n == height.length  
1 <= n <= 2 * 10^4  
0 <= height[i] <= 10^5  

``` python3
class Solution:
    def trap(self, height: List[int]) -> int:
        left,right=0,len(height)-1
        left_max,right_max=height[left],height[right]
        ans=0
        while left !=right:
            if left_max<=right_max:
                left+=1
                if height[left]<left_max:
                    ans+=left_max-height[left]
                else:
                    left_max=height[left]
            else:
                right-=1
                if height[right]<right_max:
                    ans+=right_max-height[right]
                else:
                    right_max=height[right]
        return ans

```
