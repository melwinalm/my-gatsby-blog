---
title: Intersection of Two Linked Lists
date: "2021-03-05"
type: problem-solving
description: Intersection of Two Linked Lists
tags: csharp
---

Note: This problem was taken from LeetCode - [Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)

### Naive Approach

```csharp
public ListNode GetIntersectionNode(ListNode headA, ListNode headB) {
	int sizeA = this.Size(headA);
	int sizeB = this.Size(headB);
	
	while(sizeA > sizeB){
		headA = headA.next;
		sizeA--;
	}
	
	while(sizeA < sizeB){
		headB = headB.next;
		sizeB--;
	}
	
	while(headA != headB){
		headA = headA.next;
		headB = headB.next;
	}
	
	return headA;
}

public int Size(ListNode root){
	int count = 0;
	
	while(root != null){
		root = root.next;
		count++;
	}
	
	return count;
}
```
