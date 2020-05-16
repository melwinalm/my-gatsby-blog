---
title: Simplified Fractions
date: "2020-05-16"
type: problem-solving
description: Simplified Fractions
tags: csharp
---

Note: This problem was taken from LeetCode - [Simplified Fractions](https://leetcode.com/problems/simplified-fractions/)

### Using HashSet Data Structure

```csharp
public IList<string> SimplifiedFractions(int n) {
	List<string> output = new List<string>();
	
	HashSet<double> set = new HashSet<double>();
	
	if(n < 2){
		return output;
	}
	
	for(int i = 2; i <= n; i++){
		for(int j = 1; j < i; j++){
			if(!set.Contains((double)j/(double)i)){
				set.Add((double)j/(double)i);
				output.Add(j.ToString() + "/" + i.ToString());
			}
		}
	}
	
	return output;
}
```

### Usin GCD (Faster Approach)

```csharp
public IList<string> SimplifiedFractions(int n) {
	List<string> output = new List<string>();
	
	for(int i = 2; i <= n; i++){
		for(int j = 1; j < i; j++){
			if(this.GCD(j,i) == 1){
				output.Add(j.ToString() + "/" + i.ToString());
			}
		}
	}
	
	return output;
}

public int GCD(int x, int y){
	if(x == 0){
		return y;
	}
	else{
		return this.GCD(y % x, x);
	}
}
```
