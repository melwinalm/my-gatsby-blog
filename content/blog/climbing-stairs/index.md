---
title: Climbing Stairs
date: "2020-02-03"
type: problem-solving
description: Climbing Stairs
tags: csharp
---

Note: This problem was taken from LeetCode - [Climbing Stairs](https://tspr.netlify.com/sorting-algorithms/)

### Recursion

Recursively call the `ClimbStairs` function to get the result.

```csharp
public int ClimbStairs(int n) {
    // if n is negative integer then return 0
    if(n < 0){
        return 0;
    }
    // if n is 0 or 1 then there is one way to achieve 
    else if (n <= 1){
        return 1;
    }
    else{
        return this.ClimbStairs(n - 1) + this.ClimbStairs(n-2);
    }
}
```

The above solution works but is not feasible for large numbers since the above solution has a space complexity of O(2^n).

### Recursion with Memoization

This is similar to the above solution except we use a dictionary to cache the values whose values are already found.

```csharp
Dictionary<int,int> memoize = new Dictionary<int,int>();

public int ClimbStairs(int n) {
    if(memoize.ContainsKey(n)){
        return memoize[n];
    }

    if(n < 0){
        return 0;
    }
    else if (n <= 1){
        return 1;
    }
    else{
        memoize[n] = this.ClimbStairs(n - 1) + this.ClimbStairs(n-2);
        return memoize[n];
    }
}
```

### Dynamic Programming

Similar to the above solution but using dynamic programming.

```csharp
public int ClimbStairs(int n) {
    if(n <= 1){
        return 1;
    }
    int[] dp = new int[n];
    
    dp[0] = 1; // 0th index is the number of ways for 1 step
    dp[1] = 2; // 1st index is the number of ways for 2 steps
    
    for(int i = 2; i < n; i++){
        dp[i] = dp[i-1] + dp[i-2];
    }
    
    return dp[n-1];
}
```

### Fibonnaci Sequence

The solution to this question is the nth number in the Fibonacci sequence.


| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Recursion | O(n^2) | O(1) |
| Recursion with Memoization | O(n) | O(n) |
| Dynamic Programming | O(n) | O(n) |
| Fibonnaci Sequence | O(n) | O(1) |
