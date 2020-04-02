---
title: Trapping Rain Water
date: "2020-04-02"
type: problem-solving
description: Trapping Rain Water
tags: csharp
---

Note: This problem was taken from LeetCode - [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)

### Dynamic Programming

Scan the given array starting from left by comparing its height with the previous elements. Store these values in an array. Repeat the same process by starting the scan from the right towards the left and store it in another array. Now using both these arrays find the max water that can be trapped. See the below solution.

```csharp
public int Trap(int[] height) {
	int n = height.Length;
	
	if(n == 0){
		return 0;
	}
	
	int[] leftScan = new int[n];
	int[] rightScan = new int[n];
	
	leftScan[0] = height[0];
	rightScan[n-1] = height[n-1];
	
	for(int i = 1; i < n; i++){
		leftScan[i] = Math.Max(height[i], leftScan[i-1]);
	}
	
	for(int i = n-2; i >= 0; i--){
		rightScan[i] = Math.Max(height[i], rightScan[i+1]);
	}
	
	int maxWater = 0;
	
	for(int i = 0; i < n; i++){
		// Min of the two is taken since the water can stored until the level of the smallest wall. It is then subtracted with the height of the wall.
		maxWater += Math.Min(leftScan[i], rightScan[i]) - height[i];
	}
	
	return maxWater;
}
```

### Two Pointer Approach

The previous solution can be improved by using two pointer approach. Start one pointer from 0th index and the other from the last index and move them to the center until the pointers overlap. See the below solution.

```csharp
public int Trap(int[] height) {
	int leftIndex = 0;
	int rightIndex = height.Length - 1;
	
	int leftMax = 0;
	int rightMax = 0;
	
	int maxWater = 0;
	
	while(leftIndex <= rightIndex){
					
		if(height[leftIndex] <= height[rightIndex]){
			if(height[leftIndex] >= leftMax){
				leftMax = height[leftIndex];
			}
			else{
				maxWater += leftMax - height[leftIndex];
			}
			leftIndex++;
		}
		else{
			if(height[rightIndex] >= rightMax){
				rightMax = height[rightIndex];
			}
			else{
				maxWater += rightMax - height[rightIndex];
			}
			rightIndex--;
		}
	}
	return maxWater;
}
```

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Dynamic Programming | O(n) | O(n) |
| Two Pointer Approach | O(n) | O(1) |
