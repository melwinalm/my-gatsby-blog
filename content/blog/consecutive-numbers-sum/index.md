---
title: Consecutive Numbers Sum
date: "2020-03-13"
type: problem-solving
description: Consecutive Numbers Sum
tags: csharp
---

Note: This problem was taken from LeetCode - [Consecutive Numbers Sum](https://leetcode.com/problems/consecutive-numbers-sum/)

Consecutive number is of the form,
```
x + (x + 1) + (x + 2) + .... + k terms = N
```
where N is the given number.

This series leads to,
```
kx + k(k-1)/2 = N
```
which can be written as,
```
kx = (N - k(k-1)/2)
```
So, for a solution to exist x must be an integer which can be found using the condition
```
(N - k(k-1)/2) % k == 0
```

To find the range up to which the above condition has to be checked, the condition, `N - k(k-1)/2` has to be positive since we want the sum of positive consecutive integers.

```
N - k(k-1)/2 > 0
```
```
2N > k(k-1)
```
```
2N > k^2
```
This gives us,
```
sqrt(2N) > k
```

Use these equations to get the desired result.

```csharp
public int ConsecutiveNumbersSum(int N) {
    int count = 1; // It is started with one since the given number itself is a consecutive number
    
    for(int k = 2; k < Math.Sqrt(2 * N); k++){
        if((N - ((k * (k - 1))/ 2)) % k == 0){
            count++;
        }
    }
    
    return count;
}
```
