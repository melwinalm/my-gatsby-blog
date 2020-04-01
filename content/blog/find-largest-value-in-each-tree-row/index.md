---
title: Find Largest Value in Each Tree Row
date: "2020-04-1"
type: problem-solving
description: Find Largest Value in Each Tree Row
tags: csharp
---

Note: This problem was taken from LeetCode - [Find Largest Value in Each Tree Row](https://leetcode.com/problems/find-largest-value-in-each-tree-row/)

### Breadth-First Search Approach

Perform a level order traversal on the given tree. As and when each level is traversed push the max value of that level to the list to get the required result.

```csharp
public IList<int> LargestValues(TreeNode root) {
    List<int> output = new List<int>();
    
    if(root == null){
        return output.ToArray();
    }
    
    Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
    bfsQueue.Enqueue(root);
    
    while(bfsQueue.Count > 0){
        int count = bfsQueue.Count;
        
        int max = Int32.MinValue;
        
        for(int i = 0; i < count; i++){
            TreeNode tempNode = bfsQueue.Dequeue();
            
            max = Math.Max(tempNode.val, max);
            
            if(tempNode.left != null){
                bfsQueue.Enqueue(tempNode.left);
            }
            
            if(tempNode.right != null){
                bfsQueue.Enqueue(tempNode.right);
            }
        }
        
        output.Add(max);
    } 
    return output.ToArray();
}
```

### Depth First Search Approach

Create a list that maintains the maximum value of nodes for a level. Recursively call the `FindLargest` function and update the max value to the list for that specific level.

```csharp
public IList<int> LargestValues(TreeNode root) {
    List<int> output = new List<int>();
    
    this.FindLargest(root, output, 0);
    
    return output.ToArray();
}

public void FindLargest(TreeNode root, List<int> output, int count){
    if(root == null){
        return;
    }
    
    if(count < output.Count){
        output[count] = Math.Max(root.val, output[count]);
    }
    else{
        output.Add(root.val);
    }
    
    this.FindLargest(root.left, output, count + 1);
    this.FindLargest(root.right, output, count + 1);
}
```
