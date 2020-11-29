---
title: Sliding Window Maximum
date: "2020-11-29"
type: problem-solving
description: Sliding Window Maximum
tags: csharp
---

Note: This problem was taken from LeetCode - [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)

### Using Deque (Linked List)

```csharp
public int[] MaxSlidingWindow(int[] nums, int k) {
	int[] output = new int[nums.Length - k + 1];
	
	LinkedList<int> deque = new LinkedList<int>(); // Stores the indices of the nums array
	
	for(int i = 0; i < nums.Length; i++){
		
		// Remove if deque contains an index which is not part of the window
		if(deque.Count > 0 && deque.First.Value + k <= i){
			deque.RemoveFirst();
		}
		
		// Remove indices whose value is less than the current number
		while(deque.Count > 0 && nums[deque.Last.Value] <= nums[i]){
			deque.RemoveLast();
		}
		
		// Adds the new index as the window slides
		deque.AddLast(i);
		
		if(i + 1 - k >= 0){
			output[i + 1 - k] = nums[deque.First.Value];
		}
	}
	
	return output;
}
```
