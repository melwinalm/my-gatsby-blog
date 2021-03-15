---
title: Encode and Decode TinyURL
date: "2021-03-15"
type: problem-solving
description: Encode and Decode TinyURL
tags: csharp
---

Note: This problem was taken from LeetCode - [Encode and Decode TinyURL](https://leetcode.com/problems/encode-and-decode-tinyurl/)

### Using Dictionary

```csharp
Dictionary<string, string> map;
int index = 0;
public Codec(){
	map = new Dictionary<string, string>();
}

// Encodes a URL to a shortened URL
public string encode(string longUrl) {
	map[index.ToString()] = longUrl;
	index++;
	return (index-1).ToString();
}

// Decodes a shortened URL to its original URL.
public string decode(string shortUrl) {
	if(map.ContainsKey(shortUrl)){
		return map[shortUrl];
	}
	else{
		return "";
	}
}
```
