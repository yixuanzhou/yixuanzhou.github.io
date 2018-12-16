---
title: 122. Best Time to Buy and Sell Stock II
date: 2018-03-03 16:14:16
tags: LeetCode
categories: LeetCode
---
### Problem Description:
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

### Note
This problem is kind like a real stock transaction. Given a sequence of the price of a stock in a period of time, and calculate the maximum profit one can make in such period.

If you know something about stock market, this problem is quite easy. Imaging a Candlestick chart, the key idea of the solution is in every increasing trend, buy the stock at the bottom and sell it at the top. And just waiting for the next increasing trend when there is a decreasing trend.

To do this, first we need to set a boolean variable "position" which tells us whether we have already buy a stock and not sold yet.
 
If we haven't bought any stock, then we should only concern about the bid price, if the next price is higher than the current price (which means an increasing trend), we buy the stock. If not, we wait.

If we have already bought a stock and not sold yet, if the price is increasing, we hold. Otherwise, we sell it and calculate our profit.

### Code
     public int maxProfit(int[] prices) {
        if (prices.length == 0) { return 0; }
        int bid_price = prices[0];
        int ask_price = prices[0];
        boolean position = false;
        int profit = 0;
        for (int price : prices) {
            if (!position) {
                if (price <= bid_price) {
                    bid_price = price;
                } else {
                    ask_price = price;
                    position = true;
                }
            } else {
                if (price > ask_price) {
                    ask_price = price;
                } else {
                    profit += ask_price - bid_price;
                    bid_price = price;
                    position = false;
                }
            }
        }
        if (position) { profit += ask_price - bid_price; }
        return profit;
    }