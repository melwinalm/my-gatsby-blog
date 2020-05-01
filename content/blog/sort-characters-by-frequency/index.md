---
title: Sort Characters By Frequency
date: "2020-05-01"
type: problem-solving
description: Sort Characters By Frequency
tags: csharp
---

Note: This problem was taken from LeetCode - [Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)

### Using Dictionary and Priority Queue

Iterate through the given array and store the count in a dictionary. Now enqueue all the values of the dictionary into a Priority Queue. Now dequeue all the items from the queue and return the output.

#### Note: Priority Queue Implementation can be found [here](/priority-queue-implementation-with-generics/)

```csharp
    public string FrequencySort(string s) {
        Dictionary<char, int> map = new Dictionary<char, int>();
        
        for(int i = 0; i < s.Length; i++){
            if(map.ContainsKey(s[i])){
                map[s[i]] += 1;
            }
            else{
                map[s[i]] = 1;
            }
        }
        
        PriorityQueue<char> pq = new PriorityQueue<char>();
        
        foreach(var item in map){
            pq.Enqueue(item.Value, item.Key);
        }
        
        char[] output = new char[s.Length];
        int pointer = 0;
        
        for(int i = 0; i < map.Count; i++){
            char key = pq.Dequeue();
            int val = map[key];
            
            for(int j = 0; j < val; j++){
                output[pointer] = key;
                pointer++;
            }
        }
        
        return new string(output);
    }
```
