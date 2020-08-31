---
title: Print FooBar Alternately
date: "2020-08-31"
type: problem-solving
description: Print FooBar Alternately
tags: csharp
---

Note: This problem was taken from LeetCode - [Print FooBar Alternately](https://leetcode.com/problems/print-foobar-alternately/)

### Using AutoResetEvent

```csharp
using System.Threading;

public class FooBar {
    private int n;

    AutoResetEvent event1;
    AutoResetEvent event2;
    
    public FooBar(int n) {
        this.n = n;
        
        event1 = new AutoResetEvent(true);
        event2 = new AutoResetEvent(false);
    }

    public void Foo(Action printFoo) {
        for (int i = 0; i < n; i++) {
            event1.WaitOne();
        	printFoo();
            event2.Set();
        }
    }

    public void Bar(Action printBar) {        
        for (int i = 0; i < n; i++) {
            event2.WaitOne();
        	printBar();
            event1.Set();
        }
    }
}
```
