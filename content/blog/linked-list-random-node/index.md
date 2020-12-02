---
title: Linked List Random Node
date: "2020-12-02"
type: problem-solving
description: Linked List Random Node
tags: csharp
---

Note: This problem was taken from LeetCode - [Linked List Random Node](https://leetcode.com/problems/linked-list-random-node/)

### Fixed Range Sampling

```csharp
List<int> array = new List<int>();
Random rnd = new Random();

public Solution(ListNode head) {
	while(head != null){
		array.Add(head.val);
		head = head.next;
	}
}

/** Returns a random node's value. */
public int GetRandom() {
	int index = rnd.Next(array.Count);
	return array[index];
}
```

### Reservoir Sampling

```csharp
ListNode head;
Random rnd = new Random();

public Solution(ListNode head) {
	this.head = head;
}

/** Returns a random node's value. */
public int GetRandom() {
	int size = 1;
	int returnVal = 0;
	
	ListNode curr = head;
	
	while(curr != null){
		int index = rnd.Next(size);
		
		if(index == 0){
			returnVal = curr.val;
		}
		
		curr = curr.next;
		size++;
	}
	
	return returnVal;
}
```
