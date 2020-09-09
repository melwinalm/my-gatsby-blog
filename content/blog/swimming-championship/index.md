---
title: Swimming Championship 
date: "2020-09-09"
type: problem-solving
description: Swimming Championship 
tags: csharp
---

### Problem Statement

The World Swimming Championship this year has been very exciting with frequent shifts in the positions of the swimmers on the leader board. There are N Swimmers participating in the multi-race Championship. They are all assigned points after each race. The winner of the race is awarded N points, the runner-up gets N - 1 points, and so on until the last swimmer, who gets 1 point. Two swimmers cannot finish a race in the same spot. The Champion is the swimmer who has the highest points after all the races are over. If more than one swimmer has the same highest point total, they are all awarded the World Champion title. 
The time for the final race has now come. Some swimmers may have missed some earlier races, but all the swimmers are now present for the final race. Based on the total number of points that each swimmer has just before the final race, can you estimate how many swimmers still have a chance of being the Champion? 

##### Examples

8,10,9 -> 3

15,14,15,12,14 -> 4

13,14,6,7 -> 2

2,8,6,4 -> 3

### Using Greedy Approach

```csharp
public static int SwimChamp(int[] arr){
	int N = arr.Length;
	
	// Sort the array in descending order
	Array.Sort(arr);
	Array.Reverse(arr);
	
	int lps = 1; // Lowest Possible Score
	int hps = N; // Higher Possible Score
	int count = 1;
	
	int maxSoFar = 0;
	
	for(int i = 1; i < arr.Length; i++){
		maxSoFar = Math.Max(maxSoFar, arr[i-1] + lps);
		lps++;
		
		if(arr[i] + hps >= maxSoFar){
			count++;
		}
		else{
			break;
		}
	}
	
	return count;
}
```
