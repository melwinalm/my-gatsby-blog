---
title: Final Prices With a Special Discount in a Shop
date: "2020-06-15"
type: problem-solving
description: Final Prices With a Special Discount in a Shop
tags: csharp
---

Note: This problem was taken from LeetCode - [Final Prices With a Special Discount in a Shop](https://leetcode.com/problems/final-prices-with-a-special-discount-in-a-shop/)

### Using Brute Force Solution

```csharp
public int[] FinalPrices(int[] prices) {
	int N = prices.Length;
	
	int[] output = new int[N];
	
	for(int i = 0; i < N; i++){
		output[i] = prices[i];
	}
	
	for(int i = 0; i < N; i++){
		for(int j = i+1; j < N; j++){
			if(prices[j] <= prices[i]){
				output[i] = prices[i] - prices[j];
				break;
			}
		}
	}
	
	return output;
}
```

### Using Monotone Stack

```csharp
public int[] FinalPrices(int[] prices) {
	int N = prices.Length;
	
	int[] output = new int[N];
	
	Stack<int> st = new Stack<int>();
	
	for(int i = N - 1; i >= 0; i--){
		while(st.Count > 0 && prices[i] < st.Peek()){
			st.Pop();
		}
		
		if(st.Count == 0){
			output[i] = prices[i];
		}
		else{
			output[i] = prices[i] - st.Peek();
		}
		
		st.Push(prices[i]);
	}
	
	return output;
}
```

This solution has a time complexity of O(n) and space complexity of O(1).

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Using Brute Force | O(n^2) | O(1) |
| Using Monotone Stack | O(n) | O(n) |
