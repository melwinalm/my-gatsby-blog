---
title: Subdomain Visit Count
date: "2020-02-28"
type: problem-solving
description: Subdomain Visit Count
tags: csharp
---

Note: This problem was taken from LeetCode - [Subdomain Visit Count](https://leetcode.com/problems/subdomain-visit-count/)

### Dictionary Approach

Simply split the given input into two parts. Take the domain part of it and pass it through a `string splitter` function which will return all the subdomains in that string. Now loop through all the subdomains and put it in the dictionary along with the count. Repeat this across all the domains. Once done, loop through the dictionary and return the values in the desired format.

```csharp
public IList<string> SubdomainVisits(string[] cpdomains) {
    Dictionary<string, int> dict = new Dictionary<string, int>();
    List<string> output = new List<string>();
    
    for(int i = 0; i < cpdomains.Length; i++){
        string[] split = cpdomains[i].Split(' ');
        int num = Int32.Parse(split[0]);
        List<string> domains = this.StringSplitter(split[1]);
        
        for(int j = 0 ; j < domains.Count; j++){
            if(dict.ContainsKey(domains[j])){
                dict[domains[j]] += num;
            }
            else{
                dict[domains[j]] = num;
            }
        }
    }
    
    foreach(var item in dict){
        output.Add(item.Value + " " + item.Key);
    }
    return output;
}

public List<string> StringSplitter(string input){
    List<string> temp = new List<string>();
    temp.Add(input);
    while(true){
        int index = input.IndexOf(".");
        if(index == -1){
            break;
        }
        input = input.Substring(index+1);
        temp.Add(input);
    }
    return temp;
}
```
