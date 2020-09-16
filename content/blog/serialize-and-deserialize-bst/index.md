---
title: Serialize and Deserialize BST
date: "2020-09-16"
type: problem-solving
description: Serialize and Deserialize BST
tags: csharp
---

Note: This problem was taken from LeetCode - [Serialize and Deserialize BST](https://leetcode.com/problems/serialize-and-deserialize-bst/)

### Using Recursion

```csharp
public class Codec {
    // Encodes a tree to a single string.
    public string serialize(TreeNode root) {
        StringBuilder sb = new StringBuilder();
        
        this.serialize(root, sb);
        
        return sb.ToString();
    }
	
	// Each node is separated by | and empty nodes are represented as #
    
    public void serialize(TreeNode root, StringBuilder sb){
        if(root == null){
            sb.Append("#");
            sb.Append("|");
            return;
        }
        
        sb.Append(root.val);
        sb.Append("|");
        
        this.serialize(root.left, sb);
        this.serialize(root.right, sb);
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(string data) {
        if(data.Length == 0){
            return null;
        }
        
        Queue<string> que = new Queue<string>(data.Split("|"));
        
        return deserialize(que);
    }
    
    public TreeNode deserialize(Queue<string> queue){
        string str = queue.Dequeue();
        
        if(str == "#"){
            return null;
        }
        
        TreeNode root = new TreeNode(Convert.ToInt32(str));
        root.left = this.deserialize(queue);
        root.right = this.deserialize(queue);
        
        return root;
    }
}
```
