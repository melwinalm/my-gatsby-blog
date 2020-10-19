---
title: Sort List
date: "2020-10-19"
type: problem-solving
description: Sort List
tags: csharp
---

Note: This problem was taken from LeetCode - [Sort List](https://leetcode.com/problems/sort-list/)

### Using Merge Sort

```csharp
public ListNode SortList(ListNode head) {
	if(head == null || head.next == null){
		return head;
	}
	
	ListNode slow = head;
	ListNode fast = head;
	
	while(fast.next != null && fast.next.next != null){
		slow = slow.next;
		fast = fast.next.next;
	}
	
	ListNode mid = slow.next;
	slow.next = null;
	
	ListNode left = SortList(head);
	ListNode right = SortList(mid);
	ListNode dummy = new ListNode();
	ListNode current = dummy;
	while(left != null && right != null)
	{
		if(left.val < right.val)
		{
			current.next = left;
			current = current.next;
			left = left.next;
		}
		else
		{
			current.next = right;
			current = current.next;
			right = right.next;
		}
	}
	
	if(left != null)
		current.next = left;

	if(right != null)
		current.next = right;

	return dummy.next;
}
```
