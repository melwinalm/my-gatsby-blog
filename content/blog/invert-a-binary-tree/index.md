---
title: Invert a binary tree
date: "2020-01-09"
type: problem-solving
description: Invert a binary tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)

##### Recursive Approach

One of the approach to invert a binary tree to use Recursive approach. In this approach a function calls itself recursively until a certain condition is met. See the following solution.

```csharp
public TreeNode InvertTree(TreeNode root) {
    // This is the condition used to end recursion    
    if (root == null){
        return null;
    }

    // Recursively call the InvertTree function on left and right nodes
    TreeNode left = this.InvertTree(root.left);
    TreeNode right = this.InvertTree(root.right);
    
    // Assign left node to right and vice versa
    root.left = right;
    root.right = left;
    
    return root;
}
```

The above solution works for a smaller binary tree. What if the tree is really large, there is a possibility of getting stack overflow error. The above solution is not really scalable.

Let's use the iterative approach to solve the above problem.

##### Iterative Approach

Check if the root is null initially. Create a stack to store left and right nodes of a given node. To invert the tree pop an element from stack and exchange the left and right nodes. Also push the left and right nodes of the popped item again into the stack. Keep looping until the stack is empty. At the end you will have an inverted array.

```csharp
public TreeNode InvertTree(TreeNode root) {
    if (root == null){
        return null;
    }
    
    Stack<TreeNode> temp = new Stack<TreeNode>();
    // Push the root element first to start the inversion of binary tree
    temp.Push(root);
    
    // Keep looping until the stack is empty
    while(temp.Count > 0){
        TreeNode current = temp.Pop();
        if(current != null){
            // Push the left and right nodes again to the stack
            temp.Push(current.left);
            temp.Push(current.right);
            // Typical data exchange pattern
            TreeNode temp2 = current.left;
            current.left = current.right;
            current.right = temp2;
        }
    }   
    return root;
}
```

##### Questions to be asked before solving
- Is the binary tree small. Do you want a scalable solution? This is get clarity on stack over flow we get with the first solution.
- Am I allowed to modify the existing binary tree or do you want the original tree as well. Both the approaches above modify the original binary tree. 
