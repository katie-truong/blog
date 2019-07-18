---
layout: single
permalink: /stocks/
title: "Best time to buy and sell stocks"
---

## Best time to buy and sell stocks

[Best time to buy and sell stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) is a problem that gets asked a lot in mock and real technical interviews. The problem is very straightforward, however has an optimal solutions and many variations that needs to be paid attention to.

The problem goes like this (courtesy Leetcode):

> Say you have an array for which the ith element is the price of a given stock on day i.
> If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.
> Note that you cannot sell a stock before you buy one.

```
Example 1:
Input: [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Not 7-1 = 6, as selling price needs to be larger than buying price.
```
```
Example 2:

Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

A simple brute force solution is to compare the profits that we make by buying every stock and selling them every day afterwards to find the maximum:

```
def maxProfit(prices):
    maxProfit = 0
    for i in range(len(prices) - 1):
        for j in range(i + 1, len(prices)):
            profit = prices[j] - prices[i]
            if profit > maxProfit:
                maxProfit = profit
    return maxProfit
```

Time complexity: O(n^2) (nested loop)

Space complexity: O(1) 

### Optimizing:

What is a way to optimize this solution?

Looking at the problem, my initial thought was that we needed to find the minimum price and the maximum price within the array, and find their difference. However, this approach doesn't take into account the order of the days (e.g. when the maximum price appears before the minimum prices). 

A better approach is to keep track of the minimum price, and the max profit. We would only need to go through the array once, to update the minimum price if we find a price lower the minimum price, and update the max profit, if we find a price that, if substracted by the minimum profit, yeilds a profit higher the maximum profit.

This approach brings the time complexity down to O(n) (since we only need to pass through the array once), and solve the index problem (since it's guaranteed that the price that we consider also comes after the minimum price).


```
def maxProfit(self, prices):
    min_price = sys.maxsize
    max_profit = 0
    for price in prices:
        if price < min_price:
            min_price = price
        elif price - min_price > max_profit:
            max_profit = price - min_price
return max_profit
```

Time complexity: O(n) 

Space complexity: O(1) 

## Best time to buy and sell stocks II:

A variant, more realistic version of this problem is that, instead of only buying and selling one stock, we can buy and sell multiple ones. 

The rules are:

- We also need to buy one stock before selling it.

- We can only hold on one stock at once (needs to sell a stock before buying another one).

```
Input: [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
             Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
```

```
Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying again.
```

```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```
