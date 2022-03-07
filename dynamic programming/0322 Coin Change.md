# 322. Coin Change
https://leetcode-cn.com/problems/coin-change/  
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.  
Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.  
You may assume that you have an infinite number of each kind of coin.  

Example 1:  
Input: coins = [1,2,5], amount = 11  
Output: 3  
Explanation: 11 = 5 + 5 + 1  

Example 2:  
Input: coins = [2], amount = 3  
Output: -1  

Example 3:  
Input: coins = [1], amount = 0  
Output: 0  

Constraints:  
1 <= coins.length <= 12  
1 <= coins[i] <= 2^31 - 1  
0 <= amount <= 10^4  

``` python3
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp=[-1]*(amount+1)
        dp[0]=0
        for i in coins:
            if i<=amount:
                dp[i]=1
        for i in range(1,amount+1):
            coin_num=[]
            for coin in coins:
                if i-coin>=0 and dp[i-coin]!=-1:
                    coin_num.append(dp[i-coin])
            if coin_num:
                dp[i]=min(coin_num)+1
        return dp[amount]
```
