---
title: To Lower Case
date: "2020-03-04"
type: problem-solving
description: To Lower Case
tags: csharp
---

Note: This problem was taken from LeetCode - [To Lower Case](https://leetcode.com/problems/to-lower-case/)

### Using OR operation

Setting the 5th bit of all the characters in the string will give you the required result.

```csharp
public string ToLowerCase(string str) {
		string output = "";
		
		for(int i = 0; i < str.Length; i++){
				output += (char)(str[i] | (1 << 5));
		}
		
		return output;
}
```

We could improve the time complexity by using `StringBuilder` instead of `string` if the input strings are long.

### Using ASCII code conversion

Convert each character to lowercase by subtracting 'A' and then adding 'a'.

```csharp
public string ToLowerCase(string str) {
		char[] temp = str.ToCharArray();
		
		for(int i = 0; i < temp.Length; i++){
				if(temp[i] >= 'A' && temp[i] <= 'Z'){
						temp[i] = (char)(temp[i] - 'A' + 'a');
				}
		}
		
		return new string(temp);
}
```
