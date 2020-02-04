---
title: Add Two Numbers
date: "2020-01-22"
type: problem-solving
description: Add Two Numbers
tags: csharp
---

Note: This problem was taken from LeetCode - [Add Two Numbers](https://leetcode.com/problems/valid-parentheses/)

### Basic Approach

In this approach we find both the numbers using the `FindNum` method. This method iteratively loops through the linkedlist until the end and forms the number. Then find the sum of both the numbers. Now take this sum and put it in a new linked list by finding the mod of the sum and then dividing it by 10. Repeat this process until the sum is 0. 

```csharp
public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
    ListNode output = new ListNode(0);
    ListNode temp = output;
    
    int sum = this.FindNum(l1) + this.FindNum(l2);

    do{
        temp.next = new ListNode(sum % 10);
        sum = sum / 10;
        temp = temp.next;
    } while(sum != 0);
    
    return output.next;
}

public int FindNum(ListNode node){
    int num = node.val;
    int power = 1;
    
    while(node.next != null){
        node = node.next;
        power *= 10;
        num += (node.val * power);
    }
    return num;
}
```

The time and space complexity of this approach is O(n).

The above method works, but fails when the linked list is very long i.e. if the number crosses the `Int32` overflow. To overcome this problem use the next appraoach.

### Best Approach

This approach takes the sum of both the heads of the linked lists, takes out the carry value and then puts it in a new linked list. Move the pointer to the next node and repeat this process. Keep doing this to get the sum. See the below code for the solution. 

```csharp
public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
    ListNode output = new ListNode(0);
    ListNode temp = output;
    
    int carry = 0;
    
    while(l1 != null || l2 != null){
        int firstNum = 0;
        int secondNum = 0;
        
        if(l1 != null){
            firstNum = l1.val;
            l1 = l1.next;
        }
        
        if(l2 != null){
            secondNum = l2.val;
            l2 = l2.next;
        }
        
        int sum = firstNum + secondNum;
        
        // Puts only the least significant number into the ListNode
        temp.next = new ListNode((carry + sum) % 10);
        // This will get the new carry that will be used in the next iteration
        carry = (carry + sum) / 10;
        temp = temp.next;
    }
    
    // If there is a carry from the last iteration of the loop then create a new node with the carry as the value
    if (carry != 0){
        temp.next = new ListNode(carry);
    }
    
    return output.next;
}
```

Even this approach has the same time and space complexitites.
