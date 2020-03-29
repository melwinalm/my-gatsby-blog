---
title: Reorder List
date: "2020-03-29"
type: problem-solving
description: Reorder List
tags: csharp
---

Note: This problem was taken from LeetCode - [Reorder List](https://leetcode.com/problems/reorder-list/)

### Efficient Approach

Initially perform Rabbit and Hare approach to find the middle of the list. Once the middle node is found, reverse the list starting from that middle node. Now update the next pointers of both the head and the last node to get the required result.

```csharp
public void ReorderList(ListNode head) {
	if(head == null || head.next == null){
		return;
	}
	
	ListNode slow = head;
	ListNode fast = head;
	ListNode prev = null;
	
	while(fast != null && fast.next != null){
		prev = slow;
		slow = slow.next;
		fast = fast.next.next;
	}
	
	prev.next = null;
	
	ListNode l2 = this.Reverse(slow);
	
	this.Merge(head, l2);

}

public ListNode Reverse(ListNode head){
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

public void Merge(ListNode l1, ListNode l2){
	while(l1 != null){
		ListNode temp1 = l1.next;
		ListNode temp2 = l2.next;

		l1.next = l2;

		if(temp1 == null){
			break;
		}

		l2.next = temp1;
		l1 = temp1;
		l2 = temp2;
	}
}
```

### Using Stack

This problem can also be solved using Stack. Simply perform the Rabbit and Hare approach first. Once you have the fast pointer at the end of the list, take the slow pointer and move all the nodes after that to a `Stack` until the end of the list. Now update the next pointer of the nodes of both the head and the popped item from the stack. Keep repeating this until the Stack is empty.

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Efficient Approach | O(n) | O(1) |
| Using Stack | O(n) | O(n) |
