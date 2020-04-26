---
title: Merge k Sorted Lists
date: "2020-04-26"
type: problem-solving
description: Merge k Sorted Lists
tags: csharp
---

Note: This problem was taken from LeetCode - [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

### Using Recursion

```csharp
public ListNode MergeKLists(ListNode[] lists) {
	ListNode dummy = new ListNode(0);
	
	this.Merge(lists, dummy);
	
	return dummy.next;
}

public void Merge(ListNode[] lists, ListNode output){
	ListNode minNode = new ListNode(Int32.MaxValue);
	
	int listIndex = -1;
	for(int i = 0; i < lists.Length; i++){
		if(lists[i] != null && lists[i].val < minNode.val){
			minNode = lists[i];
			listIndex = i;
		}
	}
	
	if(minNode.val == Int32.MaxValue){
		return;
	}

	output.next = minNode;
	output = output.next;
	
	lists[listIndex] = lists[listIndex].next;
	
	this.Merge(lists, output);
	return;
}
```
