---
title: Longest Substring Without Repeating Characters
date: "2020-05-31"
type: problem-solving
description: Longest Substring Without Repeating Characters
tags: csharp
---

Note: This problem was taken from LeetCode - [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

### Using Sliding Window

```csharp
public int LengthOfLongestSubstring(string s) {
	int n = s.Length;
	
	if(n <= 1){
		return n;
	}
	
	HashSet<char> set = new HashSet<char>();
	
	int startIndex = 0;
	int endIndex = 0;
	int count = 0;

	while(startIndex < n && endIndex < n){
		// If the set doesn't contain the character then add it to the set and update the end index. Update the count as well.
		if(!set.Contains(s[endIndex])){
			set.Add(s[endIndex]);
			endIndex++;
			count = Math.Max(count, set.Count);
		}
		// If set already contains the character then remove all the characters from the set until the first appearance of that repeated character.
		else{
			while(s[startIndex] != s[endIndex]){
				set.Remove(s[startIndex]);
				startIndex++;
			}
			set.Remove(s[startIndex]);
			startIndex++;
		}
	}
	
	return count;
}
```

```js
var lengthOfLongestSubstring = function(s) {
    let N = s.length;
    
    if(N < 2){
        return N;
    }
    
    let sIndex = 0;
    let eIndex = 0;

    let set = new Set();
    
    let output = 0;
    
    while(sIndex < N && eIndex < N){
        if(set.has(s[eIndex])){
            set.delete(s[sIndex]);
            sIndex++;
        }
        else{
            set.add(s[eIndex]);
            output = Math.max(output, set.size);
            eIndex++;
        }
    }
    
    return output;
};
```
