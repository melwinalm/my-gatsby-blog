---
title: Odd Even Linked List
date: "2020-02-20"
type: problem-solving
description: Odd Even Linked List
tags: csharp
---

Note: This problem was taken from LeetCode - [Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/)

Use odd and even pointers starting from the head node, and update the `next` pointers of these nodes until the end of the list. This will give you the required result.

```csharp
public ListNode OddEvenList(ListNode head) {
    if(head == null){
        return head;
    }
    if(head.next == null){
        return head;
    }
    
    ListNode oddHead = head;
    ListNode evenHead = head.next;
    ListNode even = head.next;
    
    while(evenHead != null && evenHead.next != null){
        oddHead.next = evenHead.next;
        oddHead = oddHead.next;
        evenHead.next = oddHead.next;
        evenHead = evenHead.next;
    }
    oddHead.next = even;

    return head;
}
```

This solution has a time complexity of O(n) and space complexity of O(1).
