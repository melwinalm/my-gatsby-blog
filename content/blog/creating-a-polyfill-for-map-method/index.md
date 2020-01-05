---
title: Creating a polyfill for map method
date: "2020-01-02"
type: mini-article
description: Learn how to write a custom polyfill for map method
---

What is a `map` method used for? It loops through an array of items and returns you a new array. The simplest example would be squaring the numbers in an array.

```javascript
let nums = [1,2,3,4];
let squares = nums.map(val => val * val); // [1,4,9,16]
```

Now, how do I build a custom map function to do this same activity. Use `Array.prototype.methodName` to create a extension method for array.

```javascript
Array.prototype.customMap = function(){
  // your implementation goes here
}
```

The above piece of code will create a `customMap` method associated with Array objects.

Now coming to the internal implementation of map function, it takes a callback function as input and returns the new array.

```javascript
Array.prototype.customMap = function(callback){
  let newArray = [];
  for (let i = 0 ; i < this.length ; i++){
    newArray.push(callback(this[i]));
  }
  return newArray;
}
```

In the above code snippet `this` refers to the current `Array` object passed to the map function.

The above implemenation is the basic version of map function, but the actual map method takes a callback function which has three things - `currentValue`, `index` and `input array`.

So on adding these parameters to the callback the code looks something as shown below.

```javascript
Array.prototype.customMap = function(callback){
  let newArray = [];
  for (let i = 0 ; i < this.length ; i++){
    newArray.push(callback(this[i], i, this));
  }
  return newArray;
}
```

The overall snippet with error checking added looks something as shown below

```javascript
Array.prototype.customMap = function(callback){
  // Validating if this is null
  if (this == null) {
    throw new TypeError('this is null');
  }

  // Validating if callback is a function
  if (typeof callback !== 'function'){
    throw new TypeError(callback + ' is not a function');
  }

  let newArray = [];
  for (let i = 0 ; i < this.length ; i++){
    newArray.push(callback(this[i], i, this));
  }
  return newArray;
}
```

This is a very basic version of map function. You could go through the complete polyfill code [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map#Polyfill) at MDN.
