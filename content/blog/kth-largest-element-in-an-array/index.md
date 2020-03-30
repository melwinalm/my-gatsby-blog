---
title: Kth Largest Element in an Array
date: "2020-03-30"
type: problem-solving
description: Kth Largest Element in an Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)

### Using Sorting

Sort the given array in-place. Now the Kth element from the last will have the Kth largest element in the given array.

```csharp
public int FindKthLargest(int[] nums, int k) {
    Array.Sort(nums);
    int n = nums.Length;       
    return nums[n - k];
}
```

### Using Priority Queue

Enqueue all the items in the array to a Priority Queue. Now, dequeue items from the priority queue `K` number of times to get the desired result. 

##### Note: Priority Queue implementation can be found [here](priority-queue-implementation/)

```csharp
public int FindKthLargest(int[] nums, int k) {
    PriorityQueue items = new PriorityQueue();
    
    for(int i = 0; i < nums.Length; i++){
        items.Enqueue(nums[i]);
    }
    
    int j = 1;
    while(j < k){
        items.Dequeue();
        j++;
    }
    
    return items.Dequeue();
}
```

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Using Sorting | O(nlogn) | O(1) |
| Using Priority Queue | O(nlogn + nlogk) | O(n) |

Looking at the above time complexities we can see that the sorting technique has better time and space complexities. Seems like that, butn ot really. In the above code solution I am creating a new list and pushing all the items and building max heap. But ideally I can use the given input array and build max heap on it `in-place`. This will give us constant space complexity. Even the time complextiy is bad in case of priority queues, as per the above table. But consider a sitaution where you have a stream (large amounts of data that cannot be stored in memory at one point in time) of data coming in. In that case, sorting technique cannot be used, but the priority queue implementation will have a time complexity of nlogk.
