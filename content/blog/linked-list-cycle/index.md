---
title: Linked List Cycle
date: "2020-02-06"
type: problem-solving
description: Linked List Cycle
tags: csharp
---

Note: This problem was taken from LeetCode - [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

### Two Pointer Approach (Rabbit & HAre Method)

Initialize two pointers slow and fast and point them to head of the linked list. Move the slow pointer by one step and fast pointer by two steps. If the next points to null then it is not a cyclic linked list. If the fast and slow pointer refers to the same node at one point in time then it means there is a cycle.

```csharp
public bool HasCycle(ListNode head) {
    // Edge case to check if the head is null
    if(head == null){
        return false;
    }
      
    ListNode slow = head;
    ListNode fast = head;
    
    while(fast.next != null && fast.next.next != null){
        slow = slow.next;
        fast = fast.next.next;
        if(slow == fast){
            return true;
        }
    }
    return false;
}
```

This solution has a time complexity of O(n) and space complexity of O(1).
