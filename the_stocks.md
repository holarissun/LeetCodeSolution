### [Q121: Buy and Sell Stock (1 transaction)](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock/description/?envType=study-plan-v2&envId=top-interview-150)

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

 

### Q121: Solution:

```python3
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        buy_in_price = prices[0]
        profit = 0
        for price in prices:
            profit = max(profit,price - buy_in_price)
            buy_in_price = min(buy_in_price, price)
        return profit
```



### [Q122: Buy and Sell Stock (arbitrary number of transactions)](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock/solutions/139559/gu-piao-wen-ti-python3-c-by-z1m/?envType=study-plan-v2&envId=top-interview-150)

You are given an integer array prices where prices[i] is the price of a given stock on the ith day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day.

Find and return the maximum profit you can achieve.

### Q122: Solution:

```python3
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        tot_profit = 0
        for idx, price in enumerate(prices):
            if idx < len(prices) - 1:
                gap = prices[idx+1] - price
                if gap >=0:
                    tot_profit += gap
        return tot_profit
```


### [Q123: Buy and Sell Stock (2 transactions):](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-iii/)

You are given an array prices where prices[i] is the price of a given stock on the ith day.

Find the maximum profit you can achieve. You may complete at most two transactions.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

### Q123: Solution:

```python3
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        f1, f2, f3, f4 = -prices[0], 0, -prices[0], 0
        for price in prices[1:]:
            f1 = max(f1, -price)
            f2 = max(f2, f1 + price)
            f3 = max(f3, f2 - price)
            f4 = max(f4, f3 + price)
        return f4
```

### [Q188: Buy and Sell Stock (k transactions):](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-iv/description/)


You are given an integer array prices where prices[i] is the price of a given stock on the ith day, and an integer k.

Find the maximum profit you can achieve. You may complete at most k transactions: i.e. you may buy at most k times and sell at most k times.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

### Q188: Solution

```python3
class Solution:
    def maxProfit(self, k: int, prices: List[int]) -> int:
        f = [-prices[0], 0] * k
        for price in prices[1:]:
            for j in range(k):
                if j == 0:
                    f[2*j] = max(-price,f[2*j])
                    f[2*j+1] = max(f[2*j]+price, f[2*j+1])
                else:
                    f[2*j] = max(f[2*j-1]-price,f[2*j])
                    f[2*j+1] = max(f[2*j]+price, f[2*j+1])
        return f[-1]
```
