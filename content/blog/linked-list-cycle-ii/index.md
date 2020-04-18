---
title: Linked List Cycle II
date: "2020-04-18"
type: problem-solving
description: Linked List Cycle II
tags: csharp
---

Note: This problem was taken from LeetCode - [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)

### Using Fast and Slow (Floyd's Cycle Detection Algorithm)

Watch this [video](https://www.youtube.com/watch?v=LUm2ABqAs1w) which explains how to find the starting point of a cycle in a linked list
```csharp
public ListNode DetectCycle(ListNode head) {
	ListNode slow = head;
	ListNode fast = head;
	
	while(fast != null && fast.next != null){
		slow = slow.next;
		fast = fast.next.next;
		
		if(fast == slow){
			ListNode slow2 = head;
			
			while(slow != slow2){
				slow = slow.next;
				slow2 = slow2.next;
			}
			
			return slow;
		}
	}
	
	return null;
}
```
