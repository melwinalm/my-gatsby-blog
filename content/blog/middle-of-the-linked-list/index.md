---
title: Middle of the Linked List
date: "2020-03-17"
type: problem-solving
description: Middle of the Linked List
tags: csharp
---

Note: This problem was taken from LeetCode - [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)


### Two-Pass Approach

First, find the length of the list by traversing through the list. Now find the midpoint of the list based on this length. Now traverse the list starting from the head until the midpoint.

```csharp
public ListNode MiddleNode(ListNode head) {
    if(head == null){
        return head;
    }
    
    int count = this.Length(head);
    int mid = count / 2;
    
    for(int i = 0; i < mid; i++){
        head = head.next;
    }
    
    return head;
}

public int Length(ListNode head){
    ListNode dummy = new ListNode(0);
    dummy.next = head;
    
    int count = 0;
    
    while(dummy.next != null){
        count++;
        dummy = dummy.next;
    }
    
    return count;
}
```

### Slow and Fast Pointer Approach (Tortoise and Hare Approach)

This is a slow and pointer problem where you maintain two pointers. The slow pointer jumps one node at a time while the fast pointer jumps two nodes at a time. Keep doing this until the fast pointer reaches the end. When the fast pointer reaches the end, the slow pointer will be pointing to the centre node of the list.

```csharp
public ListNode MiddleNode(ListNode head) {
    if(head == null){
        return head;
    }
    
    ListNode slow = head;
    ListNode fast = head;
    
    while(fast != null && fast.next != null){
        slow = slow.next;
        fast = fast.next.next;
    }
    
    return slow;
}
```
