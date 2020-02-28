---
title: Best Time to Buy and Sell Stock
date: "2020-02-28"
type: problem-solving
description: Best Time to Buy and Sell Stock
tags: csharp
---

Note: This problem was taken from LeetCode - [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

### Brute Force Method

In this approach try all the combinations and check which one returns you the maximum profit.

```csharp
public int MaxProfit(int[] prices) {
    int maxProfit = 0;
    
    for(int i = 0; i < prices.Length; i++){
        for(int j = i+1; j < prices.Length; j++){
            if(prices[j] - prices[i] > maxProfit){
                maxProfit = prices[j] - prices[i];
            }
        }
    }
    return maxProfit;
}
```

This solution has a time complexity of O(n^2) and space complexity of O(1).

### Better Solution

Create two variables `min price` and `max profit`. Start looping through the array, whenever a price lower than the current min price is found, update the `min price`. Else find the difference between the `current price` and the `min price` and update the `max profit` variable if the difference is greater than the current `max profit`. This will give you the maximum profit from the given stock info.

```csharp
public int MaxProfit(int[] prices) {
    int minPrice = Int32.MaxValue;
    int maxProfit = 0;
    
    for(int i = 0; i < prices.Length; i++){
        if(prices[i] < minPrice){
            minPrice = prices[i];
        }
        else if(prices[i] - minPrice > maxProfit){
            maxProfit = prices[i] - minPrice;
        }
    }
    
    return maxProfit;
}
```

The above solution has a time complexity of O(n) and space complexity of O(1).

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Brute Force | O(n^2) | O(1) |
| Better Solution | O(n) | O(1) |
