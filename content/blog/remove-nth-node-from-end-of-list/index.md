---
title: Remove Nth Node From End of List
date: "2020-01-24"
type: problem-solving
description: Remove Nth Node From End of List
tags: csharp
---

Note: This problem was taken from LeetCode - [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

### Two-Pass Approach

One way to solve this problem would be, finding the length of the Linked list first. Once you get the length traverse through the linked list again `length - n` times. Then change the next pointer of that node to point to the `next to next` node. This will return you the required result. See the below code for the solution.

```csharp
public ListNode RemoveNthFromEnd(ListNode head, int n) {
    int length = this.Count(head) - n;
    
    ListNode dummy = new ListNode(0);
    dummy.next = head;
    head = dummy;
    int i = 0;
    while(i < length){
        head = head.next;
        i++;
    }
    
    head.next = head.next.next;
    return dummy.next;
}

public int Count(ListNode head){
    int count = 1;
    while(head.next != null){
        head = head.next;
        count++;
    }
    return count;
}
```

##### You might have seen I am using a dummy node and then pointing the dummy node to the head. This is done to prevent certain edge cases where the linked list has only 1 node.

The time complexity if O(1) and space complexity if O(1) for the above approach.

The above solution traverses through the linked list twice. Can we solve it in one pass? See the next approach to see how it can be done.

### One Pass Solution (2 Pointer Approach)

In this approach, we move the first pointer n steps ahead. Then we move both the pointers until the first pointer reaches the end. At this point the first pointer is pointing to the node that has to be removed, so change the next pointer of the second pointer to point to the `next to next` node. This will give you the required result.

```csharp
public ListNode RemoveNthFromEnd(ListNode head, int n) {
    ListNode dummy = new ListNode(0);
    dummy.next = head;
    
    ListNode fPointer = dummy;
    ListNode sPointer = dummy;
    
    for(int i = 0; i < n; i++){
        fPointer = fPointer.next;
    }
    
    while(fPointer.next != null){
        fPointer = fPointer.next;
        sPointer = sPointer.next;
    }
    
    sPointer.next = sPointer.next.next;
    
    return dummy.next;
}
```

Space and time complexity of this approach is the same as the previous method. The only benefit with this approach is that the list will be traversed only once.
