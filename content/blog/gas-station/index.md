---
title: Gas Station
date: "2020-02-26"
type: problem-solving
description: Gas Station
tags: csharp
---

Note: This problem was taken from LeetCode - [Gas Station](https://leetcode.com/problems/gas-station/)

### Best Approach

In this problem, we need to find two things

- Find if the available gas is greater or equal to the total cost of gas across all the stations
- Finding the starting point of the station which gives us the solution

First one can be found by summing up both the `cost` and `gas` arrays. If the `total cost` is less than `total gas` then it means that there is no solution, so return -1;

For the second one, start from the zeroeth index and check if the tank capacity goes below 0 by finding the difference between `gas` value and `cost` value at a given station. Keep repeating this until the end of the array. If at any point if the tank capacity goes below the 0 then it means the car cannot go to the next station, so update the start pointer by incrementing it by 1. This should give you the required solution.

```csharp
public int CanCompleteCircuit(int[] gas, int[] cost) {
    
    int N = gas.Length;
    int gasSum = 0;
    int costSum = 0;
    int tank = 0;
    int start = 0;
    
    for(int i = 0; i < N; i++){
        gasSum += gas[i];
        costSum += cost[i];
        
        tank += gas[i] - cost[i];
        
        if(tank < 0){
            tank = 0;
            start = i + 1;
        }
    }
    
    if(gasSum >= costSum){
        return start;
    }
    
    return -1;
}
```

This solution has a time complexity of O(n) and space complexity of O(1).
