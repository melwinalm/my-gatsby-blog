---
title: Creating a polyfill for filter method
date: "2020-01-06"
type: mini-article
description: Learn how to write a custom polyfill for filter method
---

What is a `filter` method used for? It loops through an array of items and returns you the items which satisfy a specific condition. Consider the simple example given below.

```javascript
let nums = [1,2,3,4];
let filterItems = nums.filter(val => val > 2); // [3,4]
```

Now, how do I build a custom filter function to do this same activity. Use `Array.prototype.methodName` to create a extension method for array.

```javascript
Array.prototype.customFilter = function(){
  // your implementation goes here
}
```

The above piece of code will create a `customFilter` method associated with Array objects.

Now coming to the internal implementation of filter function, it takes a callback function as input and returns the new array.

```javascript
Array.prototype.customFilter = function(callback){
  let newArray = [];
  for (let i = 0 ; i < this.length ; i++){
    if (callback(this[i]) === true){
      newArray.push(this[i]);
    }
  }
  return newArray;
}
```

In the above code snippet `this` refers to the current `Array` object passed to the filter function.

The above implemenation is the basic version of filter function, but the actual filter method takes a callback function which has three things - `currentValue`, `index` and `input array`.

So on adding these parameters to the callback the code looks something as shown below.

```javascript
Array.prototype.customFilter = function(callback){
  let newArray = [];
  for (let i = 0 ; i < this.length ; i++){
    if (callback(this[i], i, this) === true){
      newArray.push(this[i]);
    }
  }
  return newArray;
}
```

The overall snippet with error checking added looks something as shown below

```javascript
Array.prototype.customFilter = function(callback){
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
    if (callback(this[i], i, this) === true){
      newArray.push(this[i]);
    }
  }
  return newArray;
}
```

This is a very basic version of filter function. You could go through the complete polyfill code [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter#Polyfill) at MDN.
