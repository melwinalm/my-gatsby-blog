---
title: Two Sum
date: "2020-02-07"
type: problem-solving
description: Two Sum
tags: csharp
---

Note: This problem was taken from LeetCode - [Two Sum](https://leetcode.com/problems/two-sum/)

### Brute Force Method

Loop through every element in the array and check if the `target - num` number exists.

This solution has a time complexity of O(n^2) and space complexity of O(1). This solution has quadratic time complexity. See the next approach which solves it in linear time.

### Dictionary Approach

Loop through the array and add the number and its index to a dictionary. Before you add it to the dictionary check if `target - current number` already exists in the dictionary. If it exists, then that's the solution.

```csharp
public int[] TwoSum(int[] nums, int target) {
    Dictionary<int,int> temp = new Dictionary<int,int>();
    
    for(int i = 0; i < nums.Length; i++){
        if(temp.ContainsKey(target - nums[i])){
            return new int[]{i, temp[target - nums[i]]};
        }
        temp[nums[i]] = i;
    }

    return new int[]{};
}
```

The above solution has a time complexity of O(n) and space complexity of O(n).

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Brute Force | O(n^2) | O(1) |
| Dictionary Approach | O(n) | O(n) |
