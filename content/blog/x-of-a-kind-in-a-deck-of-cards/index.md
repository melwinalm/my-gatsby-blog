---
title: X of a Kind in a Deck of Cards
date: "2020-01-10"
type: problem-solving
description: X of a Kind in a Deck of Cards
tags: csharp
---

Note: This problem was taken from LeetCode - [X of a Kind in a Deck of Cards](https://leetcode.com/problems/x-of-a-kind-in-a-deck-of-cards/)

##### Dictionary Approach

The easiest and the fastest approach to solve this problem is to use dictionary to store the number of times a specific number has appeared in the array.  So first, loop through the items in the array and put them in a dictionary (key being the number and value being number of times the number has repeated).

Consider an example array `[1,1,2,2,3,3,4]` then dictionary will have `{1: 2, 2:‌2, 3:2: 4:1}`

Now once this is done I could just loop through the items in the dictionary and see if the values are matching, something like the below code

```csharp
foreach(int item in dict.Values){
  if (partitionSize != item){
    return true;
  }
}
return false;
```

The above code works, but it fails some times.

Consider the following input array `[1,1,2,2,2,2]`, the dictionary will be `{1:2, 2:4}`.  This above piece of code will return false since partition sizes are different. But it should have returned true since it can partitioned in to `[1,1] [2,2] [2,2]`.

To pass the above scenario, we should avoid checking the partition size and check the GCD of all the values (combined GCD) in the dictionary. So we loop through the dictionary and find their combined GCD.

Also the problem statement has mentioned that the partition size has to be greater than 1. So just put a check at the end and see if the combined GCD is greater than one and return a boolean value based on that.

See the below code for the whole solution in C#.

```csharp
public bool HasGroupsSizeX(int[] deck) {
        Dictionary<int, int> dict = new Dictionary<int, int>();
        
        for (int i = 0 ; i < deck.Length; i++){
            if (dict.ContainsKey(deck[i])){
                dict[deck[i]]++;
            }
            else{
                dict[deck[i]] = 1;
            }
        }
        
        int combinedGcd = -1;
        
        foreach(int item in dict.Values){
            if (combinedGcd == -1){
                combinedGcd = item;
            }
            combinedGcd = this.Gcd(combinedGcd, item);
        }
        
        if (combinedGcd < 2){
            return false;
        }
        return true;
    }
    
    public int Gcd(int a, int b){
        if (a == 0){
            return b;
        }
        return this.Gcd(b%a, a);
    }
```
