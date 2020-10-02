---
title: Maximum Profit of Operating a Centennial Wheel
date: "2020-10-27"
type: problem-solving
description: Maximum Profit of Operating a Centennial Wheel
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Profit of Operating a Centennial Wheel](https://leetcode.com/problems/maximum-profit-of-operating-a-centennial-wheel/)

### Greedy Approach

```csharp
public int MinOperationsMaxProfit(int[] customers, int boardingCost, int runningCost) {
	int N = customers.Length;
	
	int roundCount = 1;
	int maxProfit = 0;
	int result = -1;
	
	int remCustomers = 0;
	int totalCustomers = 0;
	
	foreach(int cust in customers){
		remCustomers += cust;
		
		int currCustomer = Math.Min(remCustomers, 4);
		
		remCustomers -= currCustomer;
		totalCustomers += currCustomer;
		
		int currProfit = (boardingCost * totalCustomers) - (runningCost * roundCount);
		
		if(currProfit > maxProfit){
			maxProfit = currProfit;
			result = roundCount;
		}
		
		roundCount++;
	}
	
	while(remCustomers > 0){
		int currCustomer = Math.Min(remCustomers, 4);
		
		remCustomers -= currCustomer;
		totalCustomers += currCustomer;
		
		int currProfit = (boardingCost * totalCustomers) - (runningCost * roundCount);
		
		if(currProfit > maxProfit){
			maxProfit = currProfit;
			result = roundCount;
		}
		
		roundCount++;
	}
	
	return result;
}
```

### Greddy Approach (Improved Code)

```csharp
public int MinOperationsMaxProfit(int[] customers, int boardingCost, int runningCost) {
	int N = customers.Length;
	
	int roundCount = 1;
	int maxProfit = 0;
	int result = -1;
	
	int remCustomers = 0;
	int totalCustomers = 0;
	
	int i = 0;
	
	while(i < N || remCustomers > 0){
		if(i < N){
			remCustomers += customers[i];
			i++;
		}
		
		int currCustomer = Math.Min(remCustomers, 4);
		
		remCustomers -= currCustomer;
		totalCustomers += currCustomer;
		
		int currProfit = (boardingCost * totalCustomers) - (runningCost * roundCount);
		
		if(currProfit > maxProfit){
			maxProfit = currProfit;
			result = roundCount;
		}
		
		roundCount++;
	}
	
	return result;
}
```
