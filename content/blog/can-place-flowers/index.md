---
title: Can Place Flowers
date: "2020-08-21"
type: problem-solving
description: Can Place Flowers
tags: csharp
---

Note: This problem was taken from LeetCode - [Can Place Flowers](https://leetcode.com/problems/can-place-flowers/)

### Greedy Solution

```csharp
public bool CanPlaceFlowers(int[] flowerbed, int n) {
	// dge cases
	if(flowerbed.Length == 1){
		if(flowerbed[0] == 0 && n <= 1){
			return true;
		}
		else if(flowerbed[0] == 1 && n == 0){
			return true;
		}
		else{
			return false;
		}
	}
	
	for(int i = 0; i < flowerbed.Length; i++){
		if(this.CanBePlaced(flowerbed, i)){
			n--;
			flowerbed[i] = 1;
		}
	}
	
	return n <= 0;
}

private bool CanBePlaced(int[] flowerbed, int i){
	if(flowerbed[i] == 1){
		return false;
	}
	
	if(i == 0){
		return flowerbed[i+1] == 0 ? true : false;
	}
	else if (i == flowerbed.Length -1){
		return flowerbed[i-1] == 0 ? true : false;
	}
	else{
		return flowerbed[i-1] == 0 && flowerbed[i+1] == 0 ? true : false;
	}
}
```
