---
title: Fizz Buzz Multithreaded
date: "2020-08-31"
type: problem-solving
description: Fizz Buzz Multithreaded
tags: csharp
---

Note: This problem was taken from LeetCode - [Fizz Buzz Multithreaded](https://leetcode.com/problems/fizz-buzz-multithreaded/)

### Using lock

```csharp
public class FizzBuzz {
    private int n;
    private int i;
    private object sync;
    
    public FizzBuzz(int n) {
        this.n = n;
        i = 1;
        sync = new object();
    }

    // printFizz() outputs "fizz".
    public void Fizz(Action printFizz) {
        while(i<=n){
            lock(sync){
                if(i<=n && i%3==0 && i%5!=0)
                {
                        printFizz();
                        i++;
                } 
            }
        }
    }

    // printBuzzz() outputs "buzz".
    public void Buzz(Action printBuzz) {
        while(i<=n){
            lock(sync){
                if(i<=n && i%3!=0 && i%5==0)
                {
                        printBuzz();
                        i++;
                } 
            }
        }
    }

    // printFizzBuzz() outputs "fizzbuzz".
    public void Fizzbuzz(Action printFizzBuzz) {
        while(i<=n){
            lock(sync){
                if(i<=n && i%3==0 && i%5==0)
                {
                        printFizzBuzz();
                        i++;
                } 
            }
        }
    }

    // printNumber(x) outputs "x", where x is an integer.
    public void Number(Action<int> printNumber) {
        while(i<=n){
            lock(sync){
                if(i<=n && i%3!=0 && i%5!=0)
                {
                        printNumber(i);
                        i++;
                } 
            }
        }
    }
}
```
