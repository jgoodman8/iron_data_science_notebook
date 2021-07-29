# Best time to by and sell stock

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        return self.maxProfitOptimized(prices)
        
    def maxProfitBruteForce(self, prices: List[int]) -> int:
        """
        Time complexity: O(Nˆ2)
        Space complexity: O(1)
        """
        
        if len(prices) < 2:
            return 0
        
        highest_profit = 0
        for i in range(len(prices)):
            for j in range(i+1, len(prices)):
                profit = prices[j] - prices[i]
                if profit > highest_profit:
                    highest_profit = profit
                    
        return highest_profit
    
    
    def maxProfitOptimized(self, prices: List[int]) -> int:
        """
        Time complexity: O(N)
        Space complexity: O(1)
        """
        
        if len(prices) < 2:
            return 0
        
        highest = prices[0]
        lowest = prices[0]
        highest_profit = 0
        
        
        for price in prices[1:]:
            if price < lowest:
                lowest = price
                highest = price
            elif price > highest:
                highest = price
                profit = highest - lowest
                if highest_profit < profit: 
                    highest_profit = highest - lowest
        
        return highest_profit
    
```

