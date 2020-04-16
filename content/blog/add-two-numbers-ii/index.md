---
title: Add Two Numbers II
date: "2020-04-16"
type: problem-solving
description: Add Two Numbers II
tags: csharp
---

Note: This problem was taken from LeetCode - [Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii/)

### Using Stacks

First, traverse through the list and push all the values into the stacks. Then, pop the elements from both the stacks and add them. If there's a carry push it to the next node. Repeat this until both the stacks go empty to get the desired result.

```csharp
public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
	Stack<int> s1 = new Stack<int>();
	Stack<int> s2 = new Stack<int>();
	
	while(l1 != null){
		s1.Push(l1.val);
		l1 = l1.next;
	}
	
	while(l2 != null){
		s2.Push(l2.val);
		l2 = l2.next;
	}
	
	ListNode list = new ListNode(0);
	int sum = 0;
	while(s1.Count > 0 || s2.Count > 0){
		if(s1.Count > 0){
			sum += s1.Pop();
		}
		if(s2.Count > 0){
			sum += s2.Pop();
		}
		
		list.val = sum % 10;
		ListNode head = new ListNode(sum / 10);
		head.next = list;
		list = head;
		sum /= 10;        
	}
	
	if(list.val == 0){
		return list.next;
	}
	else{
		return list;
	}
}
```
