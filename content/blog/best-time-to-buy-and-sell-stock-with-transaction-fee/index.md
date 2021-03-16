---
title: Best Time to Buy and Sell Stock with Transaction Fee
date: "2021-03-16"
type: problem-solving
description: Best Time to Buy and Sell Stock with Transaction Fee
tags: csharp
---

Note: This problem was taken from LeetCode - [Best Time to Buy and Sell Stock with Transaction Fee](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/)

### Dynamic Programming

```csharp
public int MaxProfit(int[] prices, int fee) {
	int cash = 0;
	int hold = -prices[0];
	
	for(int i = 1; i < prices.Length; i++){
		cash = Math.Max(cash, hold + prices[i] - fee);
		hold = Math.Max(hold, cash - prices[i]);
	}
	
	return cash;
}
```
