---
title: Merge Two Sorted Lists
date: "2020-03-17"
type: problem-solving
description: Merge Two Sorted Lists
tags: csharp
---

Note: This problem was taken from LeetCode - [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

### Naive Approach

Traverse through both the lists and store the numbers in two different lists. Then merge them into a single list using the two-pointer technique. Now push this list into a linked list form.

### Recursive Approach

Create a dummy node and make it as the head node for the resulting solution (This is done to handle certain edge cases where any of the input lists are empty). Call the merge function with the dummy node along with both the lists. The merge function compares the value of both the lists and sets the next pointer of the head based on the comparison. Then call the merge function recursively to get the desired result.

Note: This solution performs the operation in-place, so the space requirement is constant, but since the stack is involved in recursive calls the space complexity for this solution will be O(m + n) where m and n is the size of both the lists.

```csharp
public ListNode MergeTwoLists(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(Int32.MinValue);
    
    this.Merge(dummy, l1, l2);
    
    return dummy.next;
}

public void Merge(ListNode head, ListNode l1, ListNode l2){
    // If anyone of the lists has reached the end then all the remaining nodes of the other list are greater than the first list.
    if(l1 == null){
        head.next = l2;
        return;
    }
    else if(l2 == null){
        head.next = l1;
        return;
    }
    
    if(l1.val < l2.val){
        head.next = l1;
        head = head.next;
        this.Merge(head, l1.next, l2);
    }
    else{
        head.next = l2;
        head = head.next;
        this.Merge(head, l1, l2.next);
    }
}   
```

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Naive Approach | O(m + n) | O(m + n) |
| Recursive Approach | O(m + n) | O(m + n) (since stack memory will be used for recursive function call) |
