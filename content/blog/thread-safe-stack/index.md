---
title: Thread Safe Stack
date: "2020-09-13"
type: problem-solving
description: Thread Safe Stack
tags: csharp
---

### Problem Statement

Design a Thread Safe Stack Class

### Solution

```csharp
using System;
using System.Collections.Generic;
using System.Threading;
					
public class Program
{
	public static void Main()
	{
		ThreadSafeStack<int> tss = new ThreadSafeStack<int>();
		
		for(int i = 0; i < 50; i++){
			Thread t = new Thread(() => tss.Push(i));
			t.Start();
		}
		
		for(int i = 0; i < 50; i++){
			Thread t = new Thread(() => tss.Push(i));
			t.Start();
		}
		
		for(int i = 0; i < 100; i++){
			Thread t = new Thread(() => {
				int val = tss.Pop();
				Console.WriteLine(val.ToString());
			});
			t.Start();
		}
	}
}

public class ThreadSafeStack<T>{
	
	List<T> list;
	public ThreadSafeStack(){
		list = new List<T>();
	}
	
	public void Push(T val){
		Console.WriteLine(val.ToString());
		lock(list){
			list.Add(val);
		}
	}
	
	public T Pop(){
		lock(list){
			T val = default(T);
			if(list.Count > 0){
				val = list[list.Count-1];
				list.RemoveAt(list.Count-1);
			}

			return val;
		}
	}
}
```
