---
title: Remove Duplicates from Sorted List II
date: "2021-01-05"
type: problem-solving
description: Remove Duplicates from Sorted List II
---

Note: This problem was taken from LeetCode - [Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)

### Iterative Approach

```csharp
public ListNode DeleteDuplicates(ListNode head) {
	if(head == null){
		return head;
	}
	ListNode dummy = new ListNode(0);
	ListNode prevNode = dummy;
	ListNode currNode = head;
	prevNode.next = currNode;
	
	while(currNode != null){
		while(currNode.next != null && currNode.val == currNode.next.val){
			currNode = currNode.next;
		}
		
		if(prevNode.next == currNode){
			prevNode = prevNode.next;
		}
		else{
			prevNode.next = currNode.next;
		}
		currNode = currNode.next;
	}
	
	return dummy.next;
}
```
