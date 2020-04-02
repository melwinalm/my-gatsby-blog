---
title: Uncommon Words from Two Sentences
date: "2020-04-02"
type: problem-solving
description: Uncommon Words from Two Sentences
tags: csharp
---

Note: This problem was taken from LeetCode - [Uncommon Words from Two Sentences](https://leetcode.com/problems/uncommon-words-from-two-sentences/)

### Using Dictionary

Split both the strings based on `space`. And then add it to the dictionary. This dictionary will have the required result.

```csharp
public string[] UncommonFromSentences(string A, string B) {
	string[] splitA = A.Split(' ');
	string[] splitB = B.Split(' ');
	
	Dictionary<string, bool> output = new Dictionary<string, bool>();
	
	for(int i = 0; i < splitA.Length; i++){
		if(output.ContainsKey(splitA[i])){
			output[splitA[i]] = false;
		}
		else{
			output[splitA[i]] = true;
		}
	}
	
	for(int i = 0; i < splitB.Length; i++){
		if(output.ContainsKey(splitB[i])){
			output[splitB[i]] = false;
		}
		else{
			output[splitB[i]] = true;
		}
	}
	
	List<string> output2 = new List<string>();
	
	foreach(var item  in output){
		if(item.Value == true){
			output2.Add(item.Key);
		}
	}
	
	return output2.ToArray();
}
```
