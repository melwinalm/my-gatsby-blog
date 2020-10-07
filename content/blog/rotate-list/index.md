---
title: Rotate List
date: "2020-10-07"
type: problem-solving
description: Rotate List
tags: csharp
---

Note: This problem was taken from LeetCode - [Rotate List](https://leetcode.com/problems/rotate-list/)

### Naive Solution

```csharp
public ListNode RotateRight(ListNode head, int k) {
	if(head == null){
		return head;
	}
	
	int length = this.ListLength(head);
	
	k = k % length;
	
	if(k == 0){
		return head;
	}
	
	k = length - k;
	
	ListNode newHead = head;
	ListNode prevNode = null;
	
	while(k > 0){
		prevNode = newHead;
		newHead = newHead.next;
		k--;
	}
	
	prevNode.next = null;
	
	prevNode = null;
	ListNode tempNode = newHead;
	
	while(tempNode != null){
		prevNode = tempNode;
		tempNode = tempNode.next;
	}
	
	prevNode.next = head;
	
	return newHead;
}

public int ListLength(ListNode root){
	int count = 0;
	
	while(root != null){
		count++;
		root = root.next;
	}
	
	return count;
}
```
