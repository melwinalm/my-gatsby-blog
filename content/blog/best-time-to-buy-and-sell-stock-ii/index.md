---
title: Best Time to Buy and Sell Stock II
date: "2020-04-02"
type: problem-solving
description: Best Time to Buy and Sell Stock II
tags: csharp
---

Note: This problem was taken from LeetCode - [Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

### Peak Valley Approach

For the given array iteratively check until the price goes to the lowest value, that is the valley and it is the buying price. Next, iteratively check until the price goes to the peak value which will be the peak and it is selling price. The difference between the selling price and buying price will be the profit. Keep repeating this process until the end of the array to get the maximum profit.

```csharp
public int MaxProfit(int[] prices) {
	int n = prices.Length;
	
	if(n == 0){
		return 0;
	}
	
	int maxProfit = 0;
	
	int i = 0;
	
	while(i < n - 1){
		while(i < n - 1 && prices[i + 1] <= prices[i]){
			i++;
		}
		int valley = prices[i];
		while(i < n - 1 && prices[i + 1] >= prices[i]){
			i++;
		}
		int peak = prices[i];
		
		maxProfit += peak - valley;
	}
	
	return maxProfit;
}
```
