---
title: Can Make Arithmetic Progression From Sequence
date: "2020-07-05"
type: problem-solving
description: Can Make Arithmetic Progression From Sequence
tags: csharp
---

Note: This problem was taken from LeetCode - [Can Make Arithmetic Progression From Sequence](https://leetcode.com/problems/can-make-arithmetic-progression-from-sequence/)

### Using Sorting (nlogn time)

```csharp
    public bool CanMakeArithmeticProgression(int[] arr) {
        Array.Sort(arr);
        
        if(arr.Length <= 2){
            return true;
        }
        
        int diff = arr[1] - arr[0];
        
        for(int i = 1; i < arr.Length; i++){
            if(diff != arr[i] - arr[i-1]){
                return false;
            }
        }
        
        return true;
    }
```

### Using Min and Max (linear time and space)

```csharp
public bool CanMakeArithmeticProgression(int[] arr) {
	int N = arr.Length;
	
	if(N <= 2){
		return true;
	}
	
	int min = Int32.MaxValue;
	int max = Int32.MinValue;
	
	foreach(int item in arr){
		min = Math.Min(item, min);
		max = Math.Max(item, max);
	}
	
	// When all the numbers in the progression are same
	if(max == min){
		return true;
	}
	
	if((max-min) % (N-1) != 0){
		return false;
	}
	
	int d = (max - min) / (N-1);
	
	HashSet<int> set = new HashSet<int>();
	
	foreach(int item in arr){
		if(set.Contains(item) || (item-min)%d != 0){
			return false;
		}
		set.Add(item);
	}
	
	return true;
}
```
