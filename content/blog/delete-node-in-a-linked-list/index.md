---
title: Delete Node in a Linked List
date: "2020-06-02"
type: problem-solving
description: Delete Node in a Linked List
tags: csharp
---

Note: This problem was taken from LeetCode - [Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/)

### Updating next pointer

```csharp
public void DeleteNode(ListNode node) {
	node.val = node.next.val;
	node.next = node.next.next;
}
```
