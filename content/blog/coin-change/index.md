---
title: Coin Change
date: "2020-06-09"
type: problem-solving
description: Coin Change
tags: csharp
---

Note: This problem was taken from LeetCode - [Coin Change](https://leetcode.com/problems/coin-change/)

### Using Top Down Approach (Time Limit Exceeded)

##### Considering amount is less than 10000

```csharp
public int CoinChange(int[] coins, int amount) {
	int val = this.Change(coins, amount, 0);
	
	if(val == 10000 || val == 10001){
		return -1;
	}
	else{
		return val;
	}
}

public int Change(int[] coins, int amount, int index){
	if(amount < 0){
		return 10000;
	}
	
	if(index == coins.Length){
		return 10000;
	}
	
	if(amount == 0){
		return 0;
	}
	
	
	int val = Math.Min(1 + this.Change(coins, amount - coins[index], index),this.Change(coins, amount, index + 1));
	return val;
}
```

### Using Top Down Approach using Memoization (Time Limit Exceeded)

```csharp
public int CoinChange(int[] coins, int amount) {
	Dictionary<string, int> map = new Dictionary<string, int>();
	
	int val = this.Change(coins, amount, 0, map);
	
	if(val == 10000 || val == 10001){
		return -1;
	}
	else{
		return val;
	}
}

public int Change(int[] coins, int amount, int index, Dictionary<string, int> map){
	if(amount < 0){
		return 10000;
	}
	
	if(index == coins.Length){
		return 10000;
	}
	
	if(amount == 0){
		return 0;
	}
	
	string key = amount.ToString() + "$" + index.ToString();
	if(map.ContainsKey(key)){
		return map[key];
	}

	map[key] = Math.Min(1 + this.Change(coins, amount - coins[index], index, map),this.Change(coins, amount, index + 1, map));
	return map[key];
}
```

### Using Bottom Up Approach

```csharp
public int CoinChange(int[] coins, int amount) {
	int[] dp = new int[amount + 1];
	
	for(int i = 0; i <= amount; i++){
		dp[i] = amount + 1;
	}
	
	dp[0] = 0;
	
	for(int i = 1; i <= amount; i++){
		for(int j = 0; j < coins.Length; j++){
			if(coins[j] <= i){
				dp[i] = Math.Min(dp[i], 1 + dp[i - coins[j]]);
			}
		}
	}
	
	return dp[amount] > amount ? -1 : dp[amount];
}
```
