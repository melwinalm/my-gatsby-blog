---
title: Min Cost to Connect All Points
date: "2020-09-15"
type: problem-solving
description: Min Cost to Connect All Points
tags: csharp
---

Note: This problem was taken from LeetCode - [Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/)

### Prim's Algorithm using Priority Queue (Min Heap)

```csharp
public class Solution {
    public int MinCostConnectPoints(int[][] points) {
        int N = points.Length;
        
        HashSet<int> unVisitedNodes = new HashSet<int>();
        
        for(int i = 0; i < N; i++){
            unVisitedNodes.Add(i);
        }
        
        PriorityQueue<Node> pq = new PriorityQueue<Node>();
        pq.Enqueue(0, new Node(0, 0));
        
        int minCost = 0;
        
        while(pq.Count > 0){
            Node tempNode = pq.Dequeue();
            int currNode = tempNode.node;
            int currWeight = tempNode.weight;
            
            if(!unVisitedNodes.Contains(currNode)){
                continue;
            }
            
            minCost += currWeight;
            
            unVisitedNodes.Remove(currNode);
            
            foreach(int nextNode in unVisitedNodes){
                int nextWeight = this.MinCost(points, currNode, nextNode);
                pq.Enqueue(nextWeight, new Node(nextNode, nextWeight));
            }
        }
        
        return minCost;
    }
    
    public int MinCost(int[][] points, int i, int j){
        int min = Math.Abs(points[i][0] - points[j][0]) + Math.Abs(points[i][1] - points[j][1]);
        
        
        return min;
    }
}

public class Node{
    public int node;
    public int weight;
    
    public Node(int _node, int _weight){
        this.node = _node;
        this.weight = _weight;
    }
}

// Implementation of Priority Queue using Min Heaps

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

	private void BuildMinHeap(int i)
    {
        while (i >= 0 && queue[(i - 1) / 2].Key > queue[i].Key)
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
		this.BuildMinHeap(heapSize);
	}

	public T Dequeue()
	{
		if (heapSize > -1)
		{
			T returnVal = queue[0].Value;
			queue[0] = queue[heapSize];
			queue.RemoveAt(heapSize);
			heapSize--;
			this.MinHeapify(0);
			return returnVal;
		}
		else
		{
			throw new Exception("Queue is empty");
		}
	}
}
```
