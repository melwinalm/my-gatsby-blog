---
title: Difference between precision and toFixed in JS
date: "2019-12-24"
type: mini-article
description: Talks about the difference in behaviour between toPrecision and toFixed functions in JS
---

##### toFixed()
toFixed(n) returns a number having n digits after the deciaml point.

##### toPrecision()
toPrecision(n) returns string of length n.

Consider some of the following examples to see how these two functions behave for different inputs.

```javascript
let num = 12.1234;
num.toFixed(); // 12
num.toPrecision(); // 12.1234

let num = 45;
num.toFixed(2); // 45.00
num.toPrecision(2); // 45

let num = 9745;
num.toFixed(3); // 9745.00
num.toPrecision(3); // 9.74e+3 - number is represented in exponential format

let num = 67.2367;
num.toFixed(2); // 67.24 - number is approximated to the nearest decimal point
num.toPrecision(2); // 67
```
