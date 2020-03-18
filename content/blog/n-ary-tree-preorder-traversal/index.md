---
title: N-ary Tree Preorder Traversal
date: "2020-03-18"
type: problem-solving
description: N-ary Tree Preorder Traversal
tags: csharp
---

Note: This problem was taken from LeetCode - [N-ary Tree Preorder Traversal](https://leetcode.com/problems/n-ary-tree-preorder-traversal/)

### Recursive Approach

```csharp
public IList<int> Preorder(Node root) {
    List<int> output = new List<int>();
    
    this.Traverse(root, output);
    
    return output;
}

public void Traverse(Node root, List<int> output){
    if(root != null){
        output.Add(root.val);
        
        foreach(Node temp in root.children){
            this.Traverse(temp, output);
        }
    }
    return;
}
```
