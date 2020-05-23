---
title: Find the range of a logical expression
date: "2020-05-23"
type: problem-solving
description: Find the range of a logical expression
tags: csharp
---

### Problem Statement

Given an expression containing only '<', '>' comparison operators and 'and' and 'or' logical operators. Find the range of numbers that are valid for the given logical expression.

### Solution

```csharp
public class Program
{
	static void Main(string[] args)
	{
		// Given input expression that is to be solved
		string input = "x>0 and x<5";

		string[] inputSplits = input.Split(' ');

		List<Range> expressions = new List<Range>();
		List<string> operations = new List<string>();

		// Even indexes will have the expression and odd indices will have the operand type
		for(int i = 0; i < inputSplits.Length; i++)
		{
			if(i%2 == 0)
			{
				expressions.Add(new Range(inputSplits[i]));
			}
			else
			{
				operations.Add(inputSplits[i]);
			}
		}

		Range currentRange = expressions[0];

		for(int i = 0; i < operations.Count; i++)
		{
			if(operations[i] == "and")
			{
				currentRange = SolveExpression.OperationAND(currentRange, expressions[i + 1]);
			}
			else if(operations[i] == "or")
			{
				currentRange = SolveExpression.OperationOR(currentRange, expressions[i + 1]);
			}
		}

		Console.WriteLine(currentRange.RangeStart.ToString() + " to " + currentRange.RangeEnd.ToString());
	}
}

public class Range
{
	int rangeStart;
	int rangeEnd;

	public int RangeStart {
		get { return rangeStart; } 
	}
	public int RangeEnd 
	{ 
		get { return rangeEnd; }
	}

	public Range(string expression)
	{
		// Extracting operand type and the number
		int indexOfLogicalOperator = Math.Max(expression.IndexOf('<'), expression.IndexOf('>'));
		char expType = expression[indexOfLogicalOperator];
		int num = Convert.ToInt32(expression.Substring(indexOfLogicalOperator + 1, expression.Length - indexOfLogicalOperator - 1));

		if(expType == '<')
		{
			this.rangeStart = Int32.MinValue;
			this.rangeEnd = num - 1;

		}
		else if (expType == '>')
		{
			this.rangeStart = num + 1;
			this.rangeEnd = Int32.MaxValue;
		}
	}

	public Range(int start, int end)
	{
		this.rangeStart = start;
		this.rangeEnd = end;
	}
}

public static class SolveExpression
{
	public static Range OperationAND(Range range1, Range range2)
	{
		int tempStart = Math.Max(range1.RangeStart, range2.RangeStart);
		int tempEnd = Math.Min(range1.RangeEnd, range2.RangeEnd);

		if(tempStart <= tempEnd)
		{
			return new Range(tempStart, tempEnd);
		}

		return new Range(0,0);
	}

	public static Range OperationOR(Range range1, Range range2)
	{
		int tempStart = Math.Min(range1.RangeStart, range2.RangeStart);
		int tempEnd = Math.Max(range1.RangeEnd, range2.RangeEnd);

		if (tempStart <= tempEnd)
		{
			return new Range(tempStart, tempEnd);
		}

		return new Range(0, 0);
	}
}
```
