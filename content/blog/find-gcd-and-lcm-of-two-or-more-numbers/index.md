---
title: Find GCD and LCM of two or more numbers
date: "2020-01-14"
type: problem-solving
description: Find GCD and LCM of two or more numbers
tags: csharp
---

### Finding GCD (Greatest Common Divisor)

GCD is also called as HCF (Highest Common Factor). It's the largest number that divides both of them. See the following code to find the GCD of two numbers.

```csharp
public int GCD(int a, int b){
    if (a == 0){
      return b;
    }
    this.GCD(b, a % b);
}
```

### Finding LCM (Least Common Multiple)

It is the smallest positive integer that is divisible by both the numbers. LCM can be found by using the following formula.

LCM = (a * b) / GCD

```csharp
public int LCM(int a, int b){
    return (a*b) / this.GCD(a,b);
}
```

### Finding LCM without using GCD

In this method first find the maximum of two numbers. Then start looping through the large number until both the numbers return 0 remainder. See the following code

```csharp
public static int LCM(int a, int b){
    int maxNum = Math.Max(a,b);

    while(true){
        if(maxNum % a == 0 && maxNum % b == 0){
            return maxNum;
        }
        maxNum++;
    }
    return maxNum;
}
```

### Finding GCD of more than 2 numbers

Recursively call the GCD function (for 2 numbers) to get the GCD of N numbers.

```csharp
public static int GCD(int numbers){
    int output = numbers[0];

    for(int i = 1; i < numbers.Length; i++){
        output = this.GCD(output, numbers[i]);
    }
    return output;
}
```

### Finding LCM of more than 2 numbers

Use the same formula that we used earlier recursively to get the LCM

```csharp
public static int LCM(int numbers){
    int output = numbers[0];

    for(int i = 1; i < numbers.Length; i++){
        output = (output * numbers[i]) / (this.GCD(output, numbers[i]));
    }
    return output;
}
```
