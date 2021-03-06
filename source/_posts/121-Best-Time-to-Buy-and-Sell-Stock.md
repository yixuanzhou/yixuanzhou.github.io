---
title: 121. Best Time to Buy and Sell Stock
date: 2018-03-03 16:14:00
tags: LeetCode
categories: LeetCode
---

### Problem Description:
Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

    Example 1:
    Input: [7, 1, 5, 3, 6, 4]
    Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
    
    Example 2:
    Input: [7, 6, 4, 3, 1]
    Output: 0

In this case, no transaction is done, i.e. max profit = 0.

### Note
Since we are only allowed to make exactly one transaction,what we should do is to buy at the lowest price and sell at the highest price. And note that we must first buy stock and then sell it. So this is actually a time sequential list.

### Code
    public int maxProfit(int[] prices) {
        if (prices.length == 0) { return 0; }
        int min_price = prices[0];
        int max_profit = 0;
        for (int i = 0; i < prices.length; ++i) {
            if (prices[i] > min_price) {
                max_profit = Math.max(max_profit, prices[i] - min_price);
            } else {
                min_price = prices[i];
            }
        }
        return max_profit;
    }
