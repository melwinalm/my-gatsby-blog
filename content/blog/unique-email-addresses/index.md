---
title: Unique Email Addresses
date: "2020-03-16"
type: problem-solving
description: Unique Email Addresses
tags: csharp
---

Note: This problem was taken from LeetCode - [Unique Email Addresses](https://leetcode.com/problems/unique-email-addresses/)

For a given email split it by `@` character. The second part of the split will give you the domain name. Now again split first part of the previous split by `+` character. Now the first part of the split will have the name of the email address. Now replace the `.` character of this substring with an empty character. This will give you the required email. Now push this name along with the domain to a `HashSet`. Repeat this process on all the emails. Now the size of the HashSet is the required solution.

```csharp
    public int NumUniqueEmails(string[] emails) {
        HashSet<string> output = new HashSet<string>();
        
        foreach(string email in emails){
            string[] split = email.Split('@');
            string[] name = split[0].Split('+');
            string subname = name[0].Replace(".", "");
            string domain = split[1];
            output.Add(subname + '@'+ domain);
        }
        
        return output.Count;
    }
```
