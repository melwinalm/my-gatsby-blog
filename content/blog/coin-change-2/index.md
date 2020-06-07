---
title: Coin Change 2
date: "2020-06-07"
type: problem-solving
description: Coin Change 2
tags: csharp
---

Note: This problem was taken from LeetCode - [Coin Change 2](https://leetcode.com/problems/coin-change-2/)

### Top Down Appraoch

```csharp
public int Change(int amount, int[] coins) {
	return this.Recursion(amount, coins, 0);
}

public int Recursion(int amount, int[] coins, int index){
	if(amount < 0){
		return 0;
	}
	
	if(amount == 0){
		return 1;
	}
	
	if(index == coins.Length){
		return 0;
	}
	
	return this.Recursion(amount, coins, index + 1, map) + this.Recursion(amount - coins[index], coins, index, map);
}
```

### Top Down Approach with Memoization

```csharp
public int Change(int amount, int[] coins) {
	Dictionary<string, int> map = new Dictionary<string, int>();
	return this.Recursion(amount, coins, 0, map);
}

public int Recursion(int amount, int[] coins, int index, Dictionary<string, int> map){
	if(amount < 0){
		return 0;
	}
	
	if(amount == 0){
		return 1;
	}
	
	if(index == coins.Length){
		return 0;
	}
	
	string key = amount.ToString() + "$" + index.ToString();
	
	if(map.ContainsKey(key)){
		return map[key];
	}
	
	map[key] = this.Recursion(amount, coins, index + 1, map) + this.Recursion(amount - coins[index], coins, index, map);
	
	return map[key];
}
```

### Bottom Up Approach

##### To be updated
