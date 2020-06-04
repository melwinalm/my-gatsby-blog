---
title: Count Primes
date: "2020-06-04"
type: problem-solving
description: Count Primes
tags: csharp
---

Note: This problem was taken from LeetCode - [Count Primes](https://leetcode.com/problems/count-primes/)

### Naive Approach

```csharp
public int CountPrimes(int n) {
	if(n <= 2){
		return 0;
	}

	int count = 1;
	
	for(int i = 3; i < n; i++){
		count += this.IsPrime(i) ? 1 : 0;
	}
	
	return count;
}

public bool IsPrime(int n){
	// The range to be cheked will be from 2 to sqrt(n) + 1
	for(int i = 2; i * i <= n; i++){
		if(n % i == 0){
			return false;
		}
	}
	
	return true;
}
```

### Using Sieve of Erasthotenes

```csharp
public int CountPrimes(int n) {
	bool[] arr = new bool[n];
	
	int count = 0;
	
	for(int i = 2; i < n; i++){
		if(arr[i] == false){
			count++;
			
			// Update all the multiples of a number to true, so that those numbers are not picked in the next sieve since they are not prime numbers
			int j = i + i;
			while(j < n){
				arr[j] = true;
				j += i;
			}
		}
	}
	
	return count;
}
```
