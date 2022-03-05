# 309. Best Time to Buy and Sell Stock with Cooldown
https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/  
You are given an array prices where prices[i] is the price of a given stock on the ith day.  
Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times) with the following restrictions:  
After you sell your stock, you cannot buy stock on the next day (i.e., cooldown one day).  
Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).  

Example 1:  
Input: prices = [1,2,3,0,2]  
Output: 3  
Explanation: transactions = [buy, sell, cooldown, buy, sell]  

Example 2:  
Input: prices = [1]  
Output: 0  

Constraints:  
1 <= prices.length <= 5000  
0 <= prices[i] <= 1000  

``` python3
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if not prices:
            return 0
        
        n = len(prices)
        f0, f1, f2 = -prices[0], 0, 0
        for i in range(1, n):
            newf0 = max(f0, f2 - prices[i])
            newf1 = f0 + prices[i]
            newf2 = max(f1, f2)
            f0, f1, f2 = newf0, newf1, newf2
        
        return max(f1, f2)
```
