---
title: Generate Random Point in a Circle
date: "2021-03-18"
type: problem-solving
description: Generate Random Point in a Circle
tags: csharp
---

Note: This problem was taken from LeetCode - [Generate Random Point in a Circle](https://leetcode.com/problems/generate-random-point-in-a-circle/)

```csharp
public class Solution {
    double radius;
    double x_center;
    double y_center;
    Random rnd;
    
    public Solution(double radius, double x_center, double y_center) {
        this.radius = radius;
        this.x_center = x_center;
        this.y_center = y_center;
        
        rnd = new Random();
    }
    
    public double[] RandPoint() {
        double length = Math.Sqrt(rnd.NextDouble()) * this.radius;
        double degree = 2 * Math.PI * rnd.NextDouble();
        
        double newX = this.x_center + (length * Math.Cos(degree));
        double newY = this.y_center + (length * Math.Sin(degree));
        
        return new double[] {newX, newY};
    }
}
```
