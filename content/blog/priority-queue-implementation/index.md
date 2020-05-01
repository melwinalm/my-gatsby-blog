---
title: Implement Priority Queue
date: "2020-03-30"
type: problem-solving
description: Implement Priority Queue
tags: csharp
---

Following are the list of abstract methods associated with Priority Queue Data Structure

- Enqueue - Adds an item to the Priority Queue
- Dequeue - Removes the item with the highest priority from the Priority Queue

#### Good to Know

###### Max Heap Property

Max Heap property defines that every node should have its value less than or equal to its parent node. This property is the foundation for max heaps. And priority queues use max heaps internally.

### Implementation

This implementation uses an array (internally) to store the items.

#### Finding the left and right children of a node

The left and right child in an array is given by `2i + 1` and `2i + 2` respectively.

```csharp
private int LeftChild(int i)
{
    return (i * 2) + 1;
}

private int RightChild(int i)
{
    return (i * 2) + 2;
}
```

#### Find Max Heapify for a given node

To `Max Heapify` a given node, find the maximum among the left, right and parent nodes. If the node with the maximum value is not the same as root then swap the nodes between the highest and the parent node. Now recursively call this function again on the highest node. For a given node, this function moves the values across the heap (starting from the given node towards the leaf) so that the max-heap property is valid. 

```csharp
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
```

#### Build Max Heap for a given node

Iteratively check if a given node is greater than its root node. If yes, then swap those values and update the pointer to the root node. Repeat this until the root node.

```csharp
private void BuildMaxHeap(int i)
{
    while (i >= 0 && queue[(i - 1) / 2] < queue[i])
    {
        this.Swap(i, (i - 1) / 2);
        i = (i - 1) / 2;
    }
}
```

#### Enqueue

Initially add the new item to the end of the list. Once the new item is added, the max heap property might be violated. So call the `BuildMaxHeap` function, which moves the newly added item to its appropriate place.

```csharp
public void Enqueue(int i)
{
    queue.Add(i);
    heapSize++;
    this.BuildMaxHeap(heapSize);
}
```

#### Dequeue

The item at index `0` will have the highest element in the given Queue, but we cannot remove it straight away from the list since that might violate the max-heap property. So, swap the numbers which are in `0th` index and the last index of the list. Now store the last item (which is the max item from the heap) from the list in a temporary variable. Remove the last item from the list. Now the item at 0th index is violating the max-heap property, so simply call the `MaxHeapify` function on this node to fix that. Return the temporary variable which is the item to be dequeued.

```csharp
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

```

Combine all these functions into a single class to get the Priority Queue. See the below code for the complete implementation.

```csharp
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
}
```


See the following lines of code which uses the above implementation.

```csharp
PriorityQueue queue = new PriorityQueue();
queue.Enqueue(5);
queue.Enqueue(3);
queue.Enqueue(12);
queue.Enqueue(1);
queue.Dequeue(); // 15
queue.Dequeue(); // 5
queue.Dequeue(); // 3
queue.Dequeue(); // 1
```
