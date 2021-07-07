---
title: Reduce Array Size to The Half
date: "2020-08-25"
updated: "2021-08-07"
type: problem-solving
description: Reduce Array Size to The Half
tags: csharp, cpp
---

Note: This problem was taken from LeetCode - [Reduce Array Size to The Half](https://leetcode.com/problems/reduce-array-size-to-the-half/)

### Greedy Approach

```csharp
public int MinSetSize(int[] arr) {
	Dictionary<int, int> freq = new Dictionary<int,int>();
	
	foreach(int item in arr){
		if(!freq.ContainsKey(item)){
			freq[item] = 0;
		}
		
		freq[item] += 1;
	}
	
	int[] counts = new int[freq.Count];
	
	int i = 0;
	foreach(var item in freq){
		counts[i] = item.Value;
		i++;
	}
	
	Array.Sort(counts, (a,b) => b-a);
	
	int reqWeight = arr.Length / 2;
	int count = 0;
	
	while(reqWeight > 0){
		reqWeight -= counts[count];
		count++;
	}
	
	return count;
 }
```

### Using Priority Queue

- Find the frequency of numbers in the given input array and store it in map.
- Put these frequencies in a priority queue.
- Pop the frequencies in the order of highest to lowest from the priority queue. Repeat it until reaching half the size of the input array size.

```cpp
class Solution {
public:
    int minSetSize(vector<int>& arr) {
        int N = arr.size();
        
        unordered_map<int, int> freq;
        priority_queue<int> pq;
        
        for(int i : arr){
            freq[i]++;
        }
        
        for(auto i : freq){
            pq.push(i.second);
        }
        
        int output = 0;
        int removed = 0;
        
        while(removed < N/2){
            removed += pq.top();
            pq.pop();
            output++;
        }
        
        return output;
    }
};
```
