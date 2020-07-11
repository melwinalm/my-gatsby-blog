---
title: Reformat Date
date: "2020-07-11"
type: problem-solving
description: Reformat Date
tags: csharp
---

Note: This problem was taken from LeetCode - [Reformat Date](https://leetcode.com/problems/reformat-date/)

### Using Dictionary

```csharp
public string ReformatDate(string date) {
	string[]splits = date.Split(" ");
	return splits[2] + "-" + this.GetMonth(splits[1]) + "-" + this.GetDate(splits[0]);
}

public string GetDate(string input){
	string num = "";
	if(input.Length == 3){
		return "0" + input.Substring(0,1);
	}
	else{
		return input.Substring(0,2);
	}
}

public string GetMonth(string input){
	Dictionary<string, string> map = new Dictionary<string, string>();
	map["Jan"] = "01";
	map["Feb"] = "02";
	map["Mar"] = "03";
	map["Apr"] = "04";
	map["May"] = "05";
	map["Jun"] = "06";
	map["Jul"] = "07";
	map["Aug"] = "08";
	map["Sep"] = "09";
	map["Oct"] = "10";
	map["Nov"] = "11";
	map["Dec"] = "12";
	
	return map[input];
}
```
