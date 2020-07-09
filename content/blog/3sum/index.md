---
title: 3Sum
date: "2020-07-09"
type: problem-solving
description: 3Sum
tags: csharp
---

Note: This problem was taken from LeetCode - [3Sum](https://leetcode.com/problems/3sum/)

### Using Sorting & Binary Search

```csharp
public IList<IList<int>> ThreeSum(int[] nums) {
	IList<IList<int>> output = new List<IList<int>>();
	
	Array.Sort(nums);
	
	int N = nums.Length;
	
	for(int i = 0; i < N-2; i++){
		int target = -nums[i];
		
		int low = i+1;
		int high = N - 1;
		
		// Perform a binary search to get the target sum
		while(low < high){
			int sum = nums[low] + nums[high];
			
			if(sum < target){
				low++;
			}
			else if(sum > target){
				high--;
			}
			else{
				int num1 = nums[i];
				int num2 = nums[low];
				int num3 = nums[high];
				
				output.Add(new List<int>(){num1, num2, num3});
				
				// This skips the numbers so that duplicate triplets groups are prevented
				while(low < high && nums[low] == num2){
					low++;
				}
				
				while(low < high && nums[high] == num3){
					high--;
				}
				
			}
			
			// This skips the numbers so that duplicate triplets groups are prevented
			while(i+1 < N && nums[i+1] == nums[i]){
				i++;
			}
		}
	}
	
	return output;
}
```
