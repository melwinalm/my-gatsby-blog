---
title: Find leap year
date: "2020-03-17"
type: problem-solving
description: Find leap year
tags: csharp
---

### Problem Statement

Find if a given year is a leap year.

### Solution

Following conditions should be met for a leap year

- If the year is a multiple of 400
- If the year is a multiple of 4 and not a multiple of 100

```csharp
public static bool IsLeapYear(int year)
{
    if(year % 400 == 0)
    {
        return true;
    }
    else if(year % 100 == 0)
    {
        return false;
    }
    else if(year % 4 == 0)
    {
        return true;
    }
    else
    {
        return false;
    }
}
```
