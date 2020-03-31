---
title: Reverse Linked List
date: "2020-03-31"
type: problem-solving
description: Reverse Linked List
tags: csharp
---

Note: This problem was taken from LeetCode - [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

### Iterative Approach

Iteratively update the next pointer of all the nodes to the previous node until the end of the list to get the reversed list.

```csharp
public ListNode ReverseList(ListNode head) {
	ListNode prev = null;
	ListNode curr = head;
	ListNode next = null;
	
	while(curr != null){
		next = curr.next;
		curr.next = prev;
		prev = curr;
		curr = next;
	}
	
	return prev;
}
```
