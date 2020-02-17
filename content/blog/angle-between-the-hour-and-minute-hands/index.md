---
title: Angle between the hour and minute hands
date: "2020-02-05"
type: problem-solving
description: Angle between the hour and minute hands
tags: csharp
---

Note: This problem was taken from Daily Coding Problem #303

#### Problem Statement

Given a clock time in `hh:mm` format, determine, to the nearest degree, the angle between the hour and the minute hands.

### Solution

The given input is a string so first format the data into an hour and minute hand values. 

To find the hour angle first mod the hour value by 12 (this is to be done to convert the hours into 12-hour format). THe hour hand moves by 30 degrees every hour and 0.5 degrees every minute. Multiply hours and minutes to get the hour angle.

Do the same with hour values as well. Mod the hour value by 60 then multiply it by 6(minute hand moves 6 degrees every minute). This gives you the angle of the minute hand.

Difference between the hour and the minute hand gives you the angle between the two hands. 

The question says `find the nearest degree`, so here what we do is, if the angle is greater than 180 return 360 - angle.

```csharp
public static int FindAngle(string time){
    string[] formattedTime = time.Split(":");
    int hour = Int32.Parse(formattedTime[0]) % 12;
    int min = Int32.Parse(formattedTime[1]) % 60;

    double hourDegrees = ((hour * 30) + (min * 0.5));
    double minDegrees = min * 6;

    double angle = Math.Abs(hourDegrees - minDegrees);

    if(angle > 180){
        return 360 - angle;
    }
    return angle;
}
```
