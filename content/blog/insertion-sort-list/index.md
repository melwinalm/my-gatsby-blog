---
title: Insertion Sort List
date: "2020-06-24"
type: problem-solving
description: Insertion Sort List
tags: csharp
---

Note: This problem was taken from LeetCode - [Insertion Sort List](https://leetcode.com/problems/insertion-sort-list/)

### Using Insertion Sort

```csharp
public ListNode InsertionSortList(ListNode head) {
	if(head == null){
		return head;
	}
	
	ListNode dummy = new ListNode(0);
	
	ListNode prev = dummy;
	ListNode curr = head;
	ListNode next = null;
	
	while(curr != null){
		next = curr.next;
		
		while(prev.next != null && prev.next.val < curr.val){
			prev = prev.next;
		}
		
		curr.next = prev.next;
		prev.next = curr;
		prev = dummy;
		curr = next;
	}
	
	return dummy.next;
}
```
