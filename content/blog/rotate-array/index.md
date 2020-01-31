---
title: Rotate Array
date: "2020-01-20"
type: problem-solving
description: Rotate Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Rotate Array](https://leetcode.com/problems/rotate-array/)

This problem can be solved in three different ways. 

### Brute Force Method

The brute force way of solving is to swap all the number in the array k times. The time-complexity for this solution will be O(n * k) (where n is the size of the array). Since the swapping is done in-place the space complexity is linear O(1). See the next approach which reduces the time-complexity significantly.

```csharp
public void Rotate(int[] nums, int k) {
    for(int i = 0; i < k; i++){
        int temp = nums[nums.Length - 1];
        for(int j = nums.Length - 1; j > 0; j--){
            nums[j] = nums[j-1];
        }
        nums[0] = temp;
    }
}
```

### Stack/Queue based approach

In this approach, you could use a stack, queue or a new array. Following code uses the Queue data structure. Start queueing elements from (n-k) till the end of the array. Then enqueue starting from 0 to n-k-1. The resulting queue will have the data rotated k times. Dequeue all the elements into the original array.

#### This approach will fail when the k is greater or equal to n. Setting the k value to k mod n will fix that. This is because rotating k times is same as rotating k mod n times.

```csharp
public void Rotate(int[] nums, int k) {
    Queue<int> temp = new Queue<int>();
    k = k % nums.Length;
    int startIndex = nums.Length - k;
    
    for(int i = startIndex; i < nums.Length; i++){
        temp.Enqueue(nums[i]);
    }
    
    for(int i = 0; i < startIndex; i++){
        temp.Enqueue(nums[i]);
    }
    
    for(int i = 0; i < nums.Length; i++){
        nums[i] = temp.Dequeue();
    }
}
```

This solution has a time complexity of O(n) and space complexity of O(n) (since we need a queue or stack or array of size n). Can we do better than this? See the next method which solves it in O(1) space complexity.

### Best Approach

This approach is the fastest among them all. First, it reverses the whole array then reverses the first k-1 elements then reverses the last k elements which give you the result. There is a separate method called `ArraySwapper` which takes start and end index along with the array. This method reverses the array based on the provided indexes. 

```csharp
public void Rotate(int[] nums, int k) {
    k = k % nums.Length;
    this.ArraySwapper(nums, 0, nums.Length-1);
    this.ArraySwapper(nums, 0, k - 1);
    this.ArraySwapper(nums, k, nums.Length-1);
}

public void ArraySwapper(int[] nums, int startIndex, int endIndex){
    while(startIndex < endIndex){
        int temp = nums[startIndex];
        nums[startIndex] = nums[endIndex];
        nums[endIndex] = temp;
        startIndex++;
        endIndex--;
    }
}
```

The time complexity is O(n) and space complexity is O(1) since everything happens in-memory.
