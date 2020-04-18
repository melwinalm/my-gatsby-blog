---
title: Linked List Cycle
date: "2020-02-06"
type: problem-solving
description: Linked List Cycle
tags: csharp
---

Note: This problem was taken from LeetCode - [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)


### Using HashSet

Recursively add the nodes into a HashSet. But before adding it to the HashSet check if that node already exists in the HashSet. If it already exists then it infers that the given list has a cycle.

```csharp
public bool HasCycle(ListNode head) {
	if(head == null){
		return false;
	}
	
	HashSet<ListNode> temp = new HashSet<ListNode>();
	
	while(head != null){
		if(temp.Contains(head)){
			return true;
		}
		else{
			temp.Add(head);
		}
		head = head.next;
	}
	
	return false;
}
```

### Using Fast and Slow Pointer

Use two pointers. One pointer jumps one node at a time and the other jumps two nodes at a time. If both the pointers intersect at any point in time then it means that it has a cycle.

```csharp
public bool HasCycle(ListNode head) {
	if(head == null){
		return false;
	}
	
	ListNode fast = head;
	ListNode slow = head;
	
	while(fast != null && fast.next != null){
		slow = slow.next;
		fast = fast.next.next;
		
		if(fast == slow){
			return true;
		}
	}
	
	return false;
}
```
