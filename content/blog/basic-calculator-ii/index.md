---
title: Basic Calculator II
date: "2020-11-25"
type: problem-solving
description: Basic Calculator II
tags: csharp
---

Note: This problem was taken from LeetCode - [Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/)

### Using Stack

```csharp
public int Calculate(string s) {
	Stack<int> st = new Stack<int>();
	
	int currNum = 0;
	char operation = '+';
	
	for(int i = 0; i < s.Length; i++){
		if(char.IsDigit(s[i])){
			Console.WriteLine(Convert.ToInt32(s[i] - '0'));
			currNum = (currNum * 10) + Convert.ToInt32(s[i] - '0');
		}
		
		if((!char.IsDigit(s[i]) && s[i] != ' ') || i == s.Length - 1){
			if(operation == '+'){
				st.Push(currNum);
			}
			else if(operation == '-'){
				st.Push(-currNum);
			}
			else if(operation == '*'){
				int prev = st.Pop();
				st.Push(prev * currNum);
			}
			else if(operation == '/'){
				int prev = st.Pop();
				st.Push(prev / currNum);
			}
			
			operation = s[i];
			currNum = 0;
		}
	}

	int output = 0;
	
	while(st.Count > 0){
		output += st.Pop();
	}
	
	return output;
}
```
