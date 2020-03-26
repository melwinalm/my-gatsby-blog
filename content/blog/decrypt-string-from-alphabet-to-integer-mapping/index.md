---
title: Decrypt String from Alphabet to Integer Mapping
date: "2020-03-24"
type: problem-solving
description: Decrypt String from Alphabet to Integer Mapping
tags: csharp
---

Note: This problem was taken from LeetCode - [Decrypt String from Alphabet to Integer Mapping](https://leetcode.com/problems/decrypt-string-from-alphabet-to-integer-mapping/)

Loop through each of the elements of the array and check if `i+2`th index is `#`. If yes then find the corresponding character for the value using the `map` dictionary. If not then it means that the character is lower than 10, so use the `map` dictionary to find the corresponding character. Repeat this until the end of the array to get the desired result. 

```csharp
public string FreqAlphabets(string s) {
    string output = "";
    
    Dictionary<string, string> map = new Dictionary<string, string>();
    map["1"] = "a";
    map["2"] = "b";
    map["3"] = "c";
    map["4"] = "d";
    map["5"] = "e";
    map["6"] = "f";
    map["7"] = "g";
    map["8"] = "h";
    map["9"] = "i";
    map["10"] = "j";
    map["11"] = "k";
    map["12"] = "l";
    map["13"] = "m";
    map["14"] = "n";
    map["15"] = "o";
    map["16"] = "p";
    map["17"] = "q";
    map["18"] = "r";
    map["19"] = "s";
    map["20"] = "t";
    map["21"] = "u";
    map["22"] = "v";
    map["23"] = "w";
    map["24"] = "x";
    map["25"] = "y";
    map["26"] = "z";
    
    int i = 0;
    
    while(i < s.Length){
        if(i+2 < s.Length && s[i+2] == '#'){
            output += map[s[i].ToString() + s[i+1].ToString()];
            i += 3;
        }
        else{
            output += map[s[i].ToString()];
            i += 1;
        }
    }
    
    return output;
}
```
