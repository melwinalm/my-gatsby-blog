---
title: Swap Nodes in Pairs
date: "2020-12-25"
type: problem-solving
description: Swap Nodes in Pairs
---

Note: This problem was taken from LeetCode - [Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)

### Recursion

```csharp
public ListNode SwapPairs(ListNode head) {
	if(head == null || head.next == null){
		return head;
	}
	
	ListNode newHead = head.next;
	head.next = this.SwapPairs(head.next.next);
	newHead.next = head;
	return newHead;
}
```
