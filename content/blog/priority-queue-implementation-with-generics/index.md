---
title: Implement Priority Queue with Generics (Max Heap)
date: "2020-05-01"
type: problem-solving
description: Implement Priority Queue with Generics (Max Heap)
tags: csharp
---

This article only has the code to the generic implementation of the Priority Queue using Max Heap. Read this article [here](/priority-queue-implementation/) which explains how the priority queue is implemented from the ground up.

```csharp
public class KeyValuePair<T>
{
	public int Key;
	public T Value;

	public KeyValuePair(int _key, T _value)
	{
		this.Key = _key;
		this.Value = _value;
	}
}

public class PriorityQueue<T>
{
	List<KeyValuePair<T>> queue = null;
	int heapSize = -1;
	public int Count { get { return queue.Count; } }

	public PriorityQueue()
	{
		queue = new List<KeyValuePair<T>>();
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
		KeyValuePair<T> temp = queue[i];
		queue[i] = queue[j];
		queue[j] = temp;
	}

	private void MaxHeapify(int i)
	{
		int left = this.LeftChild(i);
		int right = this.RightChild(i);

		int highest = i;

		if (left <= heapSize && queue[highest].Key < queue[left].Key)
		{
			highest = left;
		}

		if (right <= heapSize && queue[highest].Key < queue[right].Key)
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
		while (i >= 0 && queue[(i - 1) / 2].Key < queue[i].Key)
		{
			this.Swap(i, (i - 1) / 2);
			i = (i - 1) / 2;
		}
	}

	public void Enqueue(int _key, T _value)
	{
		KeyValuePair<T> temp = new KeyValuePair<T>(_key, _value);
		queue.Add(temp);
		heapSize++;
		this.BuildMaxHeap(heapSize);
	}

	public T Dequeue()
	{
		if (heapSize > -1)
		{
			T returnVal = queue[0].Value;
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
PriorityQueue<string> queue = new PriorityQueue<string>();
queue.Enqueue(5, "a");
queue.Enqueue(3, "abcd");
queue.Enqueue(12, "xyz");
queue.Enqueue(1, "q");
queue.Dequeue(); // xyz
queue.Dequeue(); // a
queue.Dequeue(); // abcd
queue.Dequeue(); // q
```

### Additional Notes

The above implemenation is using Max Heap. For Min heap implementation following are the functions that will have to be changed.

#### MinHeapify

```csharp
private void MinHeapify(int i)
{
	int left = this.LeftChild(i);
	int right = this.RightChild(i);

	int lowest = i;

	if (left <= heapSize && queue[lowest].Key > queue[left].Key)
	{
		lowest = left;
	}

	if (right <= heapSize && queue[lowest].Key > queue[right].Key)
	{
		lowest = right;
	}

	if (lowest != i)
	{
		this.Swap(lowest, i);
		this.MinHeapify(lowest);
	}
}
```

#### Build Min Heap

```csharp
private void BuildMinHeap(int i)
{
	while (i >= 0 && queue[(i - 1) / 2].Key > queue[i].Key)
	{
		this.Swap(i, (i - 1) / 2);
		i = (i - 1) / 2;
	}
}
```
