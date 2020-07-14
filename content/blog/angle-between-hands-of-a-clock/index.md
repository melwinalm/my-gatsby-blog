---
title: Angle Between Hands of a Clock
date: "2020-07-14"
type: problem-solving
description: Angle Between Hands of a Clock
tags: csharp
---

Note: This problem was taken from LeetCode - [Angle Between Hands of a Clock](https://leetcode.com/problems/angle-between-hands-of-a-clock/)

### Using Recursion

```csharp
public double AngleClock(int hour, int minutes) {
	hour = hour % 12;
	minutes = minutes % 60;

	double hourDegrees = ((hour * 30) + (minutes * 0.5));
	double minDegrees = minutes * 6;

	double angle = Math.Abs(hourDegrees - minDegrees);

	if(angle > 180){
		return 360 - angle;
	}
	return angle;
}
```
