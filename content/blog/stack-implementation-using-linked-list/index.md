---
title: Implement Stack using Linked List (using Generics)
date: "2020-05-11"
type: problem-solving
description: Implement Stack using Linked List (using Generics)
tags: csharp
---

Following are the list of abstract methods and properties associated with Stack Data Structure

- Push() - Adds an item to the stack
- Peek() - Returns the item at the top of the stack without removing it from the stack
- Pop() - Returns the item at the top of the stack and removes it from the stack
- Count - Returns the number of items in the stack

### Implementation

This implementation uses the inbuilt LinkedList class available in .NET framework

#### Push

Adds the item at the last of the linked list

```charp
public void Push(T value)
{
	list.AddLast(value);
	stackSize++;
}
```

#### Peek

Last property of LinkedList class returns the last element in the list

```csharp
public T Peek()
{
	return list.Last.Value;
}
```

#### Pop

Removes the last item in the list and returns it

```csharp
public T Pop()
{
	if(stackSize != 0)
	{
		T temp = list.Last.Value;
		list.RemoveLast();
		stackSize--;

		return temp;
	}
	else
	{
		throw new Exception("Stack is Empty");
	}
}
```

Combine all these functions into a single class to get Stack. See the below code for the complete implementation.

```csharp
public class CustomStack<T>
{
	private LinkedList<T> list;
	private int stackSize;

	public int Count { get { return stackSize; } }

	public CustomStack()
	{
		list = new LinkedList<T>();
		stackSize = 0;
	}

	public void Push(T value)
	{
		list.AddLast(value);
		stackSize++;
	}

	public T Peek()
	{
		return list.Last.Value;
	}

	public T Pop()
	{
		if(stackSize != 0)
		{
			T temp = list.Last.Value;
			list.RemoveLast();
			stackSize--;

			return temp;
		}
		else
		{
			throw new Exception("Stack is Empty");
		}
	}
}
```

See the following lines of code which uses the above implementation.

```csharp
CustomStack<int> stack = new CustomStack<int>();

stack.Push(1);
stack.Push(2);
stack.Push(3);
stack.Pop();    // 3
stack.Peek();   // 2
stack.Pop();    // 2
stack.Pop();    // 1
```
