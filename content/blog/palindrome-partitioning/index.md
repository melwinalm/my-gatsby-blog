---
title: Palindrome Partitioning
date: "2020-12-14"
type: problem-solving
description: Palindrome Partitioning
---

Note: This problem was taken from LeetCode - [Palindrome Partitioning](hhttps://leetcode.com/problems/palindrome-partitioning/)

### Depth First Search

```csharp
public IList<IList<string>> Partition(string s) {
	IList<IList<string>> output = new List<IList<string>>();
	
	this.DFS(0, output, new List<string>(), s);
	
	return output;
}

private void DFS(int start, IList<IList<string>> output, List<string> temp, string s){
	if(start >= s.Length){
		List<string> tempList = new List<string>(temp);
		output.Add(tempList);
		return;
	}

	for(int end = start; end < s.Length; end++){
		if(this.IsPalindrome(s, start, end)){
			temp.Add(s.Substring(start, end-start+1));
			this.DFS(end+1, output, temp, s);
			temp.RemoveAt(temp.Count-1);
		}
	}
}

private bool IsPalindrome(string s, int low, int high){
	while(low < high){
		
		if(s[low] != s[high]){
			return false;
		}
		low++;
		high--;
	}
	
	return true;
}
```
