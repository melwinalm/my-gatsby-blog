---
title: All Elements in Two Binary Search Trees
date: "2020-03-12"
type: problem-solving
description: All Elements in Two Binary Search Trees
tags: csharp
---

Note: This problem was taken from LeetCode - [All Elements in Two Binary Search Trees](https://leetcode.com/problems/all-elements-in-two-binary-search-trees/)

### Using Queue

Perform In Order traversal on both the BST's and add it to Queue. Now dequeue the values from both the Queues based on the values and push it to a new list.

```csharp
public IList<int> GetAllElements(TreeNode root1, TreeNode root2) {
    Queue<int> list1 = new Queue<int>();
    Queue<int> list2 = new Queue<int>();
    
    this.InOrderTraversal(root1, list1);
    this.InOrderTraversal(root2, list2);
    
    List<int> output = new List<int>();
    
    while(list1.Count != 0 || list2.Count != 0){
        if(list1.Count == 0){
            output.Add(list2.Dequeue());
        }
        else if(list2.Count == 0){
            output.Add(list1.Dequeue());
        }
        else{
            if(list1.Peek() < list2.Peek()){
                output.Add(list1.Dequeue());
            }
            else{
                output.Add(list2.Dequeue());
            }
        }
    }
    
    return output;
}

public void InOrderTraversal(TreeNode root, Queue<int> output){
    if(root == null){
        return;
    }
    
    this.InOrderTraversal(root.left, output);
    output.Enqueue(root.val);
    this.InOrderTraversal(root.right, output);
}
```

### Using Stack

Better space complexity can be achieved using Stack data structure.
