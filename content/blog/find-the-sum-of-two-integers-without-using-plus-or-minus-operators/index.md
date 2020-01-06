---
title: Find the sum of two integers without using + or - operators
date: "2020-01-06"
type: problem-solving
description: Find the sum of two integers without using + or - operators
tags: javascript
---

We could use bitwise operators to find the sum of two numbers.

How does bitwise addition work. Let's see how bitwise addition works using an example.

Consider the numbers 5 and 6 which can be represented as 0101 and 0110 in binary

```
0 1 0 1
0 1 1 0
-------
1 0 1 1
-------
```
So in the above example we are performing XOR operation on the two bits from right to left. If there is a carry (when it is 1 and 1) then 1 is added to the next significant bit.

To find sum we can used XOR operation. Similarly, to add the carry bit, perform AND operation first and then right rotate it by one bit. In the above example AND operation of two numbers would give us 0100 and after right rotating it, it will be 1000. Keep repeating this process recursively until the AND operation returns 0 i.e. there are no carry bits.This will give us the sum of two numbers.

Below is the JavaScript code to do this.

```javascript
function GetSum(a, b){
  let sum = a ^ b;
  let carry = (a & b) << 1;

  if (sum & carry){
    return GetSum(sum, carry);
  }
  return sum ^ carry
}

GetSum(5,6); // 11
GetSum(-5,6); // 1
```
