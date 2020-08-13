---
title: Partition List
date: "2020-08-13"
type: problem-solving
description: Partition List
tags: csharp
---

Note: This problem was taken from LeetCode - [Partition List](https://leetcode.com/problems/partition-list/)

### One Pass Solution

```csharp
public ListNode Partition(ListNode head, int x) {
	if(head == null){
		return head;
	}
	
	ListNode first = new ListNode(0);
	ListNode second = new ListNode(0);
	
	ListNode rootFirst = first;
	ListNode rootSecond = second;
	
	while(head != null){
		if(head.val < x){
			first.next = head;
			first = first.next;
		}
		else{
			second.next = head;
			second = second.next;
		}
		
		head = head.next;
	}
	
	second.next = null; // Not setting this to null will to TLE error
	first.next = rootSecond.next;
	
	return rootFirst.next;
}
```
