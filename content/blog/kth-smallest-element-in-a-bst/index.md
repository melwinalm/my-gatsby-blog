---
title: Kth Smallest Element in a BST
date: "2020-03-17"
type: problem-solving
description: Kth Smallest Element in a BST
tags: csharp
---

Note: This problem was taken from LeetCode - [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

### In Order Traversal

Simply perform in-order traversal on the given tree and store it in a list. The kth element of that list in the required solution.

```csharp
    public int KthSmallest(TreeNode root, int k) {        
        List<int> temp = new List<int>();
        
        this.InOrderTraversal(root, temp);
        return temp[k-1];
    }
    
    public void InOrderTraversal(TreeNode root, List<int> temp){    
        if(root.left != null){
            this.InOrderTraversal(root.left, temp);
        }
        
        temp.Add(root.val);
        
        if(root.right != null){
            this.InOrderTraversal(root.right, temp);
        }
    }
```

This solution has a time complexity of O(n) and space complexity of O(n).

We need not traverse the whole tree to get the result. Just traverse through k nodes of the tree to get better time and space complexity. See the next solution for this approach.

### In Order Traversal (Better)

This approach is similar to the previous one, except that we need two reference variables `count` and `output`. Increment the `count` variable on each traversal and whenever the `count` matches the value `k`, set the value of that node to the `output` variable and return.

```csharp
public int KthSmallest(TreeNode root, int k) {        
    int count = 0;
    int output = 0;
    
    this.InOrderTraversal(root, ref count, ref output, k);
    return output;
}

public void InOrderTraversal(TreeNode root, ref int count, ref int output, int k){    
    if(root.left != null){
        this.InOrderTraversal(root.left, ref count, ref output, k);
    }
    
    count++;
    if(count == k){
        output = root.val;
        return;
    }
    
    if(root.right != null){
        this.InOrderTraversal(root.right, ref count, ref output, k);
    }
}
```

This solution has a time complexity of O(k) and space complexity of O(k).

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| In Order Traversal | O(n) | O(n) |
| In Order Traversal (Better) | O(k) | O(k) |
