---
title: Course Schedule III
date: "2021-05-03"
type: problem-solving
description: Course Schedule III
tags: csharp
---

Note: This problem was taken from LeetCode - [Course Schedule III](https://leetcode.com/problems/course-schedule-iii/)

### Using Priority Queue

```csharp
public class Solution {
    public int ScheduleCourse(int[][] courses) {
        // Sort the courses in the increasing order of last day
        Array.Sort(courses, (a,b) => a[1] - b[1]);
        
        PriorityQueue pq = new PriorityQueue();
        int time = 0;
        
        foreach(int[] c in courses){
            // if current day plus the duration is on or before last day, then that course can be taken. So enqueue to the priority queue
            if(time + c[0] <= c[1]){
                pq.Enqueue(c[0]);
                time += c[0];
            }
            else{
                // if there's a course which has lesser duration than the current course in the priority queue, then replace it and update the time
                if(pq.Count != 0 && pq.Peek() > c[0]){
                    int temp = pq.Dequeue();
                    time = time - temp + c[0];
                    pq.Enqueue(c[0]);
                }
            }
        }
        
        return pq.Count;
    }
}

public class PriorityQueue{
    List<int> queue = null;
    int heapSize = -1;
    public int Count { get { return queue.Count; } }

    public PriorityQueue()
    {
        queue = new List<int>();
    }

    private int LeftChild(int i)
    {
        return (i * 2) + 1;
    }

    private int RightChild(int i)
    {
        return (i * 2) + 2;
    }

    private void Swap(int i, int j)
    {
        int temp = queue[i];
        queue[i] = queue[j];
        queue[j] = temp;
    }

    private void MaxHeapify(int i)
    {
        int left = this.LeftChild(i);
        int right = this.RightChild(i);

        int highest = i;

        if (left <= heapSize && queue[highest] < queue[left])
        {
            highest = left;
        }

        if (right <= heapSize && queue[highest] < queue[right])
        {
            highest = right;
        }

        if (highest != i)
        {
            this.Swap(highest, i);
            this.MaxHeapify(highest);
        }
    }

    private void BuildMaxHeap(int i)
    {
        while (i >= 0 && queue[(i - 1) / 2] < queue[i])
        {
            this.Swap(i, (i - 1) / 2);
            i = (i - 1) / 2;
        }
    }

    public void Enqueue(int i)
    {
        queue.Add(i);
        heapSize++;
        this.BuildMaxHeap(heapSize);
    }

    public int Dequeue()
    {
        if (heapSize > -1)
        {
            int returnVal = queue[0];
            queue[0] = queue[heapSize];
            queue.RemoveAt(heapSize);
            heapSize--;
            this.MaxHeapify(0);
            return returnVal;
        }
        else
        {
            throw new Exception("Queue is empty");
        }
    }
    
    public int Peek()
    {
        if (heapSize > -1)
        {
            return queue[0];
        }
        else
        {
            throw new Exception("Queue is empty");
        }
    }
}
```
