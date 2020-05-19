---
title: Online Stock Span
date: "2020-05-19"
type: problem-solving
description: Online Stock Span
tags: csharp
---

Note: This problem was taken from LeetCode - [Permutation in String](https://leetcode.com/problems/online-stock-span/)

### Using Stack

```csharp
public class StockSpanner {
    Stack<int> prices;
    Stack<int> weights;
    
    public StockSpanner() {
        prices = new Stack<int>();
        weights = new Stack<int>();
    }
    
    public int Next(int price) {
        int weight = 1;
        while(prices.Count != 0 && prices.Peek() <= price){
            prices.Pop();
            weight += weights.Pop();
        }
        
        prices.Push(price);
        weights.Push(weight);
        return weight;
    }
}
```
