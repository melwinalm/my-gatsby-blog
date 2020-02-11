---
title: Palindrome Linked List
date: "2020-01-28"
type: problem-solving
description: Palindrome Linked List
tags: csharp
---

Note: This problem was taken from LeetCode - [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)

### Naive Approach

In this approach, you go through all the nodes of the linked list and put the values in a new array. Then use the two-pointer technique one at the start and the other at the end to see if the numbers match.

```csharp
public bool IsPalindrome(ListNode head) {
    List<int> temp = new List<int>();
    
    while(head != null){
        temp.Add(head.val);
        head = head.next;
    }
    
    for(int i = 0; i < temp.Count / 2; i++){
        if(temp[i] != temp[temp.Count - i - 1]){
            return false;
        }
    }
    return true;
}
```

This solution has a time complexity of O(n) and space complexity of O(n) (since an array of size n is used to store all the values).

See the next solution which solves this using lesser space.

### Best Approach (Tortoise and Hare method)

Here we use two pointers, one pointer jumps one node at a time and the other jumps 2 nodes at a time. In the end, you will have a slow pointer in the middle of the list and the fast pointer at the end of the list. Now reverse the linked list starting from the slow pointer. Consider the following example

Input ```1 -> 2 -> 3 -> 3 -> 2 -> 1``` will turn into

```1 <- 2 <- 3 (start pointer) <- 3 (end pointer) -> 2 -> 1```

Start checking if the start and end pointer values are the same until the end of the list. This gives you the required result.

```csharp
public bool IsPalindrome(ListNode head) {
    ListNode fast = head;
    ListNode slow = head;
    
    while(fast != null && fast.next != null){
        slow = slow.next;
        fast = fast.next.next;
    }
    
    // If there are an odd number of nodes in the list then move the slow pointer to the center of the list
    if(fast != null){
        slow = slow.next;
    }
    
    ListNode start = head;
    ListNode end = this.Reverse(slow);
    
    while(end != null){
        if(start.val != end.val){
            return false;
        }
        
        start = start.next;
        end = end.next;
    }
    return true;
}

public ListNode Reverse(ListNode head){
    ListNode prev = null;
    while(head != null){
        ListNode next = head.next;
        head.next = prev;
        prev = head;
        head = next;
    }
    return prev;
}
```

This solution has the same time complexity but has a O(1) space complexity since we all the operations are done in-place.
