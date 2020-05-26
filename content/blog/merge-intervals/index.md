---
title: Merge Intervals
date: "2020-05-26"
type: problem-solving
description: Merge Intervals
tags: csharp
---

Note: This problem was taken from LeetCode - [Merge Intervals](https://leetcode.com/problems/merge-intervals/)

### Using Sorting (Uses extra space. Using IComparable interface)

```csharp
public int[][] Merge(int[][] intervals) {
	if(intervals.Length <= 1){
		return intervals;
	}
	
	List<Range> input = new List<Range>();
	for(int i = 0; i < intervals.Length; i++){
		input.Add(new Range(intervals[i][0], intervals[i][1]));
	}
	
	input.Sort();
	
	List<int[]> output = new List<int[]>();
	
	int start = input[0].start;
	int end = input[0].end;
	
	foreach(Range item in input){
		if(item.start <= end){
			end = Math.Max(item.end, end);
		}
		else{
			output.Add(new int[]{start, end});
			start = item.start;
			end = item.end;
		}
	}
	
	output.Add(new int[]{start, end});
	
	return output.ToArray();
}

public class Range: IComparable<Range>{
	public int start;
	public int end;

	public Range(int _start, int _end){
		this.start = _start;
		this.end = _end;
	}

	public int CompareTo(Range other){
		if(this.start < other.start){
			return -1;
		}
		else if(this.start > other.start){
			return 1;
		}
		else{
			return 0;
		}
	}
}
```

### Using Sorting (Without extra space. Using IComparer interface)

```csharp
public int[][] Merge(int[][] intervals) {
	if(intervals.Length <= 1){
		return intervals;
	}

	Array.Sort(intervals, new IntervalSort());
	
	List<int[]> output = new List<int[]>();
	
	int start = intervals[0][0];
	int end = intervals[0][1];
	
	foreach(int[] item in intervals){
		if(item[0] <= end){
			end = Math.Max(item[1], end);
		}
		else{
			output.Add(new int[]{start, end});
			start = item[0];
			end = item[1];
		}
	}
	
	output.Add(new int[]{start, end});
	
	return output.ToArray();
}

public class IntervalSort: IComparer<int[]>{
	public int Compare(int[] interval1, int[] interval2){
		if(interval1[0] < interval2[0]){
			return -1;
		}
		else if(interval1[0] > interval2[0]){
			return 1;
		}
		else{
			return 0;
		}
	}
}
```
