---
title: Valid Anagram
date: "2020-02-19"
type: problem-solving
description: Valid Anagram
tags: csharp
---

Note: This problem was taken from LeetCode - [Valid Anagram](https://leetcode.com/problems/valid-anagram/)

### Using Sorting

The naive approach to this problem would be to sort both the strings first and then check if they match by each characters.

This solution has a time complexity of O(nlogn) and space complexity of O(1)

### Using Dictionary

Create a dictionary first. Take one of the string and start adding them to the dictionary along with the count of number of times a specific character has occured. Then take the second string and remove the key one by one. And the end, if the dictionary doesn't have any item then it's a valid anagram.

```csharp
public bool IsAnagram(string s, string t) {
    // Check if both strings are of equal length
    if(s.Length != t.Length){
        return false;
    }
    
    Dictionary<char,int> temp = new Dictionary<char,int>();
    
    // Add all the characters of the string to the dictionary
    foreach(char item in s){
        if(temp.ContainsKey(item)){
            temp[item] += 1;
        }
        else{
            temp[item] = 1;
        }
    }
    
    // Remmoving characters from the string
    foreach(char item in t){
        if(temp.ContainsKey(item)){
            // If value of key is 1 then remvoe the key else reduce the value by 1
            if(temp[item] == 1){
                temp.Remove(item);
            }
            else{
                temp[item] -= 1;
            }
        }
        else{
            return false;
        }
    }
    
    // If the dictionary is empty then it is a valid anagram
    return temp.Count == 0;
}
```

The above solution has a time complexity of O(n) and space complexity of O(n).

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Using Sorting | O(nlogn) | O(1) |
| Using Dictionary | O(n) | O(n) |
