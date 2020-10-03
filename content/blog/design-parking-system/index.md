---
title: Design Parking System
date: "2020-10-04"
type: problem-solving
description: Design Parking System
tags: csharp
---

Note: This problem was taken from LeetCode - [Design Parking System](https://leetcode.com/problems/design-parking-system/)

### Top Down Approach (Time Limit Exceeded)

```csharp
public class ParkingSystem {
    
    int big = 0;
    int medium = 0;
    int small = 0;
    
    public ParkingSystem(int big, int medium, int small) {
        this.big = big;
        this.medium = medium;
        this.small = small;
    }
    
    public bool AddCar(int carType) {
        if(carType == 1){
            big--;
            return big < 0 ? false : true;
        }
        else if(carType == 2){
            medium--;
            return medium < 0 ? false : true;
        }
        else if(carType == 3){
            small--;
            return small < 0 ? false : true;
        }
        
        return false;
    }
}
```
