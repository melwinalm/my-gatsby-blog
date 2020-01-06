---
title: Creating a polyfill for reduce method
date: "2020-01-03"
type: mini-article
description: Learn how to write a custom polyfill for reduce method
---

What is a `reduce` method used for? It loops through an array of items and returns you a single value. It's basically used for aggregation. A simple example would be finding the average of the items in an array. Consider the simple example given below.

```javascript
let nums = [1,2,3,4];
let sum = nums.reduce((total, current) => total + current, 0); // 10
let average = sum / nums.length;
```

Now, how do I build a custom reduce function to do this same activity. Use `Array.prototype.methodName` to create a extension method for array.

```javascript
Array.prototype.customReduce = function(){
  // your implementation goes here
}
```

The above piece of code will create a `customReduce` method associated with Array objects.

Now coming to the internal implementation of reduce function, it takes a callback function, and initial value as input and returns a single value.

```javascript
Array.prototype.customReduce = function(callback, initialValue){
  let aggregator = initialValue;
  for (let i = 0 ; i < this.length ; i++){
    aggregator = callback(aggregator, this[i]);
  }
  return aggregator;
}
```

In the above code snippet `this` refers to the current `Array` object passed to the reduce function.

The above implemenation is the basic version of reduce function, but the actual reduce method takes a callback function which has four things - `total`, `currentValue`, `index` and `input array`.

So on adding these parameters to the callback the code looks something as shown below.

```javascript
Array.prototype.customReduce = function(callback, initialValue){
  let aggregator = initialValue;
  for (let i = 0 ; i < this.length ; i++){
    aggregator = callback(aggregator, this[i], i, this);
  }
  return aggregator;
}
```

The overall snippet with error checking added looks something as shown below

```javascript
Array.prototype.customReduce = function(callback){
  // Validating if this is null
  if (this == null) {
    throw new TypeError('this is null');
  }

  // Validating if callback is a function
  if (typeof callback !== 'function'){
    throw new TypeError(callback + ' is not a function');
  }

  let aggregator = initialValue;
  for (let i = 0 ; i < this.length ; i++){
    aggregator = callback(aggregator, this[i], i, this);
  }
  return aggregator;
}
```

This is a very basic version of reduce function. You could go through the complete polyfill code [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#Polyfill) at MDN.
