---
title: Last Stone Weight
date: "2020-03-31"
type: problem-solving
description: Last Stone Weight
tags: csharp
---

Note: This problem was taken from LeetCode - [Last Stone Weight](https://leetcode.com/problems/last-stone-weight/)

### Using Priority Queue

At first, enqueue all the stone weights into a Priority Queue. Now dequeue twice from the queue (which will return the top two weights from the queue). Find the difference between the two dequeued items and put it back to the queue. If the difference is zero, then it means the weights cancelled each other and that need not be enqueued. Keep iterating on this until the queue count goes below two. Now if the queue has zero items, then it means that all the stones cancelled each other and the result is zero. If not then dequeue the last element from the queue to get the required result.

##### Note: Priority Queue implementation can be found [here](priority-queue-implementation/)

```csharp
public int LastStoneWeight(int[] stones) {
    PriorityQueue queue = new PriorityQueue();
    
    for(int i = 0; i < stones.Length; i++){
        queue.Enqueue(stones[i]);
    }
    
    while(queue.Count > 1){
        int num1 = queue.Dequeue();
        int num2 = queue.Dequeue();
        
        int diff = num1 - num2;
        
        if(diff != 0){
            queue.Enqueue(diff);    
        }
    }
    
    if(queue.Count == 0){
        return 0;
    }
    else{
        return queue.Dequeue();
    }
}
```
