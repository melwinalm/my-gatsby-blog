---
title: Find the Duplicate Number
date: "2020-01-28"
type: problem-solving
description: Find the Duplicate Number
tags: csharp
---

Note: This problem was taken from LeetCode - [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)

### Using Dictionary Approach (could use Set also)

This method uses a dictionary to store the numbers. Every time a new key/value pair is to be added, check if the key already exists. If the key already exists then that itself is the duplicate number.

```csharp
public int FindDuplicate(int[] nums) {
    Dictionary<int,Boolean> temp = new Dictionary<int,Boolean>();
    
    for(int i = 0; i < nums.Length; i++){
        if(temp.ContainsKey(nums[i])){
            return nums[i];
        }
        else{
            temp[nums[i]] = true;
        }
    }
    return -1;
}
```

The above method had a time complexity of O(n) and space complexity of O(n).

### Using Sorting Approach

In this approach, the given number array is first sorted and then check if two adjacent items are the same.

```csharp
public int FindDuplicate(int[] nums) {
    Array.Sort(nums);
    
    for(int i = 1; i < nums.Length; i++){
        if(nums[i] == nums[i-1]){
            return nums[i];
        }
    }
    
    return -1;
}
```

The above method has a time complexity of O(nlogn) and space complexity of O(1).

### Tortoise and Hare Approach

Here we use two pointers, one moves one step at a time and the other at 2 steps at a time. Keep doing this until the values match. 

```csharp
public int FindDuplicate(int[] nums) {
    int slow = nums[0];
    int fast = nums[0];
    
    do {
        slow = nums[slow];
        fast = nums[nums[fast]];
    } while(slow != fast);
    
    int pt1 = nums[0];
    int pt2 = slow;
    
    while(pt1 != pt2){
        pt1 = nums[pt1];
        pt2 = nums[pt2];
    }
    
    return pt1;
}
```

This method has a time complexity of O(n) and space complexity of O(1).

### Time and Space Complexities 

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Dictionary Approach | O(n) | O(n) |
| Sorting Approach | O(nlogn) | O(1) |
| Tortoise and Hare Approach | O(n) | O(1) |
