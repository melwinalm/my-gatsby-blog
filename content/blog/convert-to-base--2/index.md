---
title: Convert to Base -2
date: "2020-01-13"
type: problem-solving
description: Convert to Base -2
tags: csharp
---

Note: This problem was taken from LeetCode - [Convert to Base -2](https://leetcode.com/problems/convert-to-base-2/submissions/)

The question seems a bit tricky since it's asking to convert the number to base `-2`. Ignore the base `-2` for now, consider the base to be `2`, how do we approach this. Simply divide the number by 2 and store the remainder. The new number will be number divided by 2. Keep repeating this process until the number is 0 or 1. At the end of this process you will have the binary representation of the number. 

Same steps work for base `-2` also. Just keep dividing by `-2` instead of `2` recursively to get the output.

##### Recursive Approach

```csharp
public string BaseNeg2(int N) {
    // the condition has to be N == 0 or N == 1 and not N < 2 since N becomes a negative number when divided by two
    if(N == 0 || N == 1){
        return N.ToString();
    }
    // if mod 2 remainder is 0 then prepend 0 else prepend 1
    if (N % 2 == 0){
        return this.BaseNeg2(N / -2) + "0";
    }
    else{
        return this.BaseNeg2((N - 1) / -2) + "1";
    }
}
```

This can solved using iterative approach also. Loop through the N, store the remainder and divide the number by `-2`. Keep doing this until the number is 0.  

##### Iterative Approach (Fastest Method)

```csharp
public string BaseNeg2(int N) {
    string output = "";
    do{
        if (N % 2 == 0){
            N = N / -2;
            // The remainder has to be prepended since the process starts from least significant bit to most significant bit
            output = "0" + output;
        }
        else{
            N = (N - 1) / -2;
            output = "1" + output;
        }
    } while(N != 0);
    
    return output.ToString();
}
```

In the above code we have used a do-while loop since the loop has to run atleast once. Consider when the input is 0, the output will be null if we use while loop. Using do-while loop will return 0 when the input is 0.

The above code can be used for base `any integer` by just making some minor tweaks. 
