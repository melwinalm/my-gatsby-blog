---
title: Lemonade Change
date: "2020-08-25"
type: problem-solving
description: Lemonade Change
tags: csharp
---

Note: This problem was taken from LeetCode - [Lemonade Change](https://leetcode.com/problems/lemonade-change/)

### Greedy Approach (Naive Solution)

```csharp
public bool LemonadeChange(int[] bills) {
	int bill5 = 0;
	int bill10 = 0;
	
	foreach(int item in bills){
		if(item == 5){
			bill5++;
		}
		else if(item == 10){
			bill10++;
			if(bill5 >= 1){
				bill5--;    
			}
			else{
				return false;
			}
		}
		else{
			if(bill5 >= 1 && bill10 >= 1){
				bill5--;
				bill10--;
			}
			else if(bill5 >= 3){
				bill5 -= 3;
			}
			else{
				return false;
			}
		}
	}
	
	return true;
}
```
