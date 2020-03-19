---
title: Add Binary
date: "2020-03-19"
type: problem-solving
description: Add Binary
tags: csharp
---

Note: This problem was taken from LeetCode - [Add Binary](https://leetcode.com/problems/add-binary/)

Firstly make the lengths of the both input string equal by prepending `0` to them. Now loop through the given strings starting from the last bit and perform `XOR` operation for sum and `AND` operation for the carry flag. Keep doing this to get the desired result.

```csharp
public string AddBinary(string a, string b) {   
    int aLen = a.Length;
    int bLen = b.Length;
    
    // Make the lengths of both the inputs equal
    if(aLen > bLen){
        for(int i = 0; i < aLen-bLen; i++){
            b = "0" + b;
        }
    }
    else if(bLen > aLen){
        for(int i = 0; i < bLen-aLen; i++){
            a = "0" + a;
        }
    }
    
    char[] output = new char[a.Length]; 
    char carry = '0';
    
    Dictionary<char, bool> MAP = new Dictionary<char, bool>();
    MAP['1'] = true;
    MAP['0'] = false;
    
    Dictionary<bool, char> REVERSEMAP = new Dictionary<bool, char>();
    REVERSEMAP[true] = '1';
    REVERSEMAP[false] = '0';
    
    for(int i = a.Length - 1; i >= 0; i--){
        Console.WriteLine(i.ToString());
        output[i] = REVERSEMAP[MAP[a[i]] ^ MAP[b[i]] ^ MAP[carry]];
        carry = REVERSEMAP[(MAP[a[i]] && MAP[b[i]]) || (MAP[b[i]] && MAP[carry]) || (MAP[carry] && MAP[a[i]])];
    }
    
    if(carry == '1'){
        return '1' + new string(output);
    }
    else{
        return new string(output);
    }
}
```
