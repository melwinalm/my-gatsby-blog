---
title: Remove Linked List Elements
date: "2020-02-24"
type: problem-solving
description: Remove Linked List Elements
tags: csharp
---

Note: This problem was taken from LeetCode - [Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)

### Iterative Approach

Initially create a dummy node and then assign the next pointer of the dummy node to the head. This is done to avoid issues during certain edge cases (Suppose a case where the head value matches the target number, then you will need a pointer to maintain another head). Create two pointers previous and current. These two pointers are required whenever a matching node is found. When a matching node is found in the current node simply update the next pointer of the previous node to point to the next pointer of the current node. Keep repeating this iteratively to get the required result.

```csharp
public ListNode RemoveElements(ListNode head, int val) {
    ListNode dummy = new ListNode(0);
    dummy.next = head;
    
    ListNode prev = dummy;
    ListNode curr = head;
    
    while(curr != null){
        if(curr.val == val){
            prev.next = curr.next;
        }
        else{
            prev = curr;
        }

        curr = curr.next;
    }
    
    return dummy.next;
}
```

This solution has a time complexity of O(n) and space complexity of O(1).

