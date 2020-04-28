---
title: LRU Cache
date: "2020-04-28"
type: problem-solving
description: LRU Cache
tags: csharp
---

Note: This problem was taken from LeetCode - [LRU Cache](https://leetcode.com/problems/lru-cache/)

### Using Dictionary and Doubly Linked List

```csharp
public class LRUCache {
    Dictionary<int, Node> map;
    DoubleLinkedList dll;
    int totalCapacity;
    int count;
    
    public LRUCache(int capacity) {
        map = new Dictionary<int, Node>();
        dll = new DoubleLinkedList();
        totalCapacity = capacity;
        count = 0;
    }
    
    public int Get(int key) {
        if(map.ContainsKey(key)){
            Node tempNode = map[key];
            dll.RemoveNode(tempNode);
            dll.InsertNode(tempNode);
            return tempNode.val;
        }
        else{
            return -1;
        }
    }
    
    public void Put(int key, int value) {
        if(map.ContainsKey(key)){
            map[key].val = value;
            this.Get(key);
            return;
        }
        
        if(count >= totalCapacity){
            map.Remove(dll.head.key);
            dll.RemoveNode(dll.head);
            count--;
            Console.WriteLine(count.ToString());
        }
        
        Node tempNode = new Node(key, value);
        map[key] = tempNode;
        dll.InsertNode(tempNode);
        count++;
    }
}

public class Node{
    public int key;
    public int val;
    public Node next;
    public Node prev;
    
    public Node(int _key, int _val){
        this.key = _key;
        this.val = _val;
        this.prev = null;
        this.next = null;
    }
}

public class DoubleLinkedList{
    public Node head;
    public Node tail;
    
    public DoubleLinkedList(){
        head = null;
        tail = null;
    }
    
    public void InsertNode(Node newNode){
        if(head == null && tail == null){
            head = newNode;
            tail = newNode;
        }
        else{
            newNode.prev = tail;
            tail.next = newNode;
            tail = newNode;
        }
    }
    
    public void  RemoveNode(Node removeNode){
        if(removeNode == head && removeNode == tail){
            head = null;
            tail = null;
        }
        else if(removeNode == head){
            head = head.next;
        }
        else if(removeNode == tail){
            tail = tail.prev;
        }
        else{
            Node temp1 = removeNode.prev;
            Node temp2 = removeNode.next;
            temp1.next = temp2;
            temp2.prev = temp1;
        }
    }
}
```
