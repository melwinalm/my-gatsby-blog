---
title: String Compression
date: "2020-02-10"
type: problem-solving
description: String Compression
tags: csharp
---

### Problem Statement

Given an input string, find its Run Length Encoded string.

For example, given `AAABBCCCD` return `A3B2C3D1`.

Also, write the function to decode the encoded string.


### Encode Function

Start looping through the string array (starting from 2nd index) and check if current character and the previous character are same. If they are same then increment the `charCounter`. Else append the previous character and the `charCount` to the output string. This should give you the run-length encoded string.

```csharp
public static string Encode(string input){
    string output = "";

    int charCount = 1;
    for(int i = 1; i < input.Length; i++){
        if(input[i] == input[i-1]){
            charCount++;
        }
        else{
            output += input[i-1] + charCount.ToString();
            charCount = 1;
        }
    }
    return output;
}
```

### Decode Function

Every even indexed value is the character and odd indexed value will be its count. Loop through the input and append the character to the output string `count` number of times. This will give you the decoded input. 

```csharp
public static string Decode(string input){
    string output  = "";

    int i = 0;
    while(i < input.Length){
        char value = input[2*i];
        int count = Int32.Parse(input[2*i].ToString());

        for(int j = 0; j < count; j++){
            output += value;
        }

        i++;
    }
}
```

##### Note: The code above for decoding of the string is a basic version. This function will fail if a character repeats more than 9 times. Suppose the input is A10 then the function will throw an error.
