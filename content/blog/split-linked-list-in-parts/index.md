---
title: Split Linked List in Parts
date: "2020-08-27"
type: problem-solving
description: Split Linked List in Parts
tags: csharp
---

Note: This problem was taken from LeetCode - [Split Linked List in Parts](https://leetcode.com/problems/split-linked-list-in-parts/)

```csharp
public ListNode[] SplitListToParts(ListNode root, int k) {
	ListNode[] output = new ListNode[k];
	
	if(root == null){
		return output;
	}
	
	ListNode temp = root;
	int length = this.Length(temp);
	
	int i = 0;
	
	ListNode prevNode = new ListNode(0);
	
	while(k > 0){
		int currSize = (int)Math.Ceiling(length / (double)k);
		length = length - currSize;
		k--;
		
		output[i] = root;
		
		for(int a = 0; a < currSize; a++){
			prevNode = root;
			root = root.next;
		}
		
		prevNode.next = null;
		
		i++;
	}
	
	return output;
}

public int Length(ListNode head){
	int count = 0;
	
	while(head != null){
		head = head.next;
		count++;
	}
	
	return count;
}
```
