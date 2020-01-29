---
title: Backspace String Compare
date: "2020-01-16"
type: problem-solving
description: Backspace String Compare
tags: csharp
---

Note: This problem was taken from LeetCode - [Backspace String Compare](https://leetcode.com/problems/backspace-string-compare/)

The first thing that comes to mind when you read the question is to use the Stack data structure. Read the below explanation.

### Stack-based approach

Loop through string array, and `Push` it to the stack. Whenever you find a `#` character, check if the stack is empty and if not then `Pop` one element from the stack. Keep doing this until the end of the array. Repeat this same process on the second string array as well. Now take these two Stacks and Pop elements from both and check if they are same if they do not then return false.

```csharp
public bool BackspaceCompare(string S, string T) {
    Stack<char> first = new Stack<char>();
    Stack<char> second = new Stack<char>();
    
    for(int i = 0; i < S.Length; i++){
        if(S[i] == '#'){
            if(first.Count != 0)
                first.Pop();
        }
        else{
            first.Push(S[i]);
        }
    }
    
    for(int i = 0; i < T.Length; i++){
        if(T[i] == '#'){
            if(second.Count != 0)
                second.Pop();
        }
        else{
            second.Push(T[i]);
        }
    }
    
    if(first.Count != second.Count){
        return false;
    }
    
    while(first.Count != 0){
        if(first.Pop() != second.Pop()){
            return false;
        }
    }
    
    return true;
}
```

The time-complexity of the above approach is O(S + T) (where S and T are the lengths of the strings) since we are looping through all the elements of both the arrays. The space-complexity will be O(S + T) since we need to stacks to store the characters of the string.

Can we do better than this? See the next solution which solves it in linear time-complexity.

### Two Pointer Approach

Start looping from the end of the array, whenever `#` is found, increase the skip count. When a non `#` character is found, decrease the skip count. Keep decrementing the pointer during this process. Repeat the same for the second array also. Keep checking if the character pointed by both the arrays are matching. If they aren't matching then return. Keep doing this until one of the pointers reaches 0. See the below code for this approach. 

```csharp
public bool BackspaceCompare(string S, string T) {
    int skipS = 0;
    int skipT = 0;
    
    int i = S.Length-1;
    int j = T.Length-1;
    
    while(i >= 0 || j >= 0){
        while(i >= 0){
            if(S[i] == '#'){
                skipS++;
                i--;
            }
            else if(skipS > 0){
                skipS--;
                i--;
            }
            else{
                break;
            }
        }
        
        while(j >= 0){
            if(T[j] == '#'){
                skipT++;
                j--;
            }
            else if(skipT > 0){
                skipT--;
                j--;
            }
            else{
                break;
            }
        }
        
        if (i >=0 && j>= 0 && S[i] != T[j] || ((i >= 0) != (j >= 0))){
            return false;
        }
        i--;
        j--;
    }
    return true;
}
```

The time-complexity is the same as the previous method, but the space-complexity has reduced to O(1).
