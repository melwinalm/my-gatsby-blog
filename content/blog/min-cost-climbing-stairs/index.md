---
title: Min Cost Climbing Stairs
date: "2020-03-12"
type: problem-solving
description: Min Cost Climbing Stairs
tags: csharp
---

Note: This problem was taken from LeetCode - [Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/)

### Dynamic Programming

```csharp
public int MinCostClimbingStairs(int[] cost) {
    if(cost.Length == 0){
        return 0;
    }
    else if(cost.Length == 1){
        return cost[0];
    }
    
    int step1 = cost[0];
    int step2 = cost[1];
    
    for(int i = 2; i < cost.Length; i++){
        int temp = cost[i] + Math.Min(step1, step2);
        step1 = step2;
        step2 = temp;
    }
    
    return Math.Min(step1, step2);
}
```

### Recursion

```csharp
    public int MinCostClimbingStairs(int[] cost) {
        return Math.Min(MinCost(cost, 0), MinCost(cost, 1)); // It cannot be just MinCost(cost, 0); since that will always take the first element of the array, but the result start with the second element as well.
    }
    
    public int MinCost(int[] cost, int startIndex){
        if(startIndex >= cost.Length || startIndex < 0){
            return 0;
        }
        
        return cost[startIndex] + Math.Min(this.MinCost(cost, startIndex + 1), this.MinCost(cost, startIndex + 2));
    }
```

### Recursion with Memoization

```csharp
public int MinCostClimbingStairs(int[] cost) {
    int[] memo = new int[cost.Length];
    
    return Math.Min(MinCost(cost, 0, memo), MinCost(cost, 1, memo));
}

public int MinCost(int[] cost, int startIndex, int[] memo){
    if(startIndex >= cost.Length || startIndex < 0){
        return 0;
    }
    
    if(memo[startIndex] != 0){
        return memo[startIndex];
    }
    
    memo[startIndex] = cost[startIndex] +  Math.Min(this.MinCost(cost, startIndex + 1, memo), this.MinCost(cost, startIndex + 2, memo));
    
    return memo[startIndex];
}
```

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Dynamic Programming | O(n) | O(1) |
| Recursion | O(n^2) | O(n) (recursive call uses stack memory) |
| Recursion with Memoization | O(n) | O(n) |
