---
title: Check If Two String Arrays are Equivalent
date: "2021-01-08"
type: problem-solving
description: Check If Two String Arrays are Equivalent
---

Note: This problem was taken from LeetCode - [Check If Two String Arrays are Equivalent](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/)

### Naive Approach

```csharp
public bool ArrayStringsAreEqual(string[] word1, string[] word2) {
	StringBuilder sb1 = new StringBuilder();
	StringBuilder sb2 = new StringBuilder();
	
	foreach(string word in word1){
		sb1.Append(word);
	}
	
	foreach(string word in word2){
		sb2.Append(word);
	}
	
	return sb1.ToString() == sb2.ToString();
}
```

```javascript
var arrayStringsAreEqual = function(word1, word2) {
    let string1 = "";
    let string2 = "";
    
    word1.forEach(val => string1 += val);
    word2.forEach(val => string2 += val);
    
    return string1 == string2;
};
```
