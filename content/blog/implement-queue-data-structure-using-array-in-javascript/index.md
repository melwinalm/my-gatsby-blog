---
title: Implement Queue Data Structure using array in JavaScript
date: "2020-01-07"
type: problem-solving
description: Implement Queue Data Structure using array in JavaScript
tags: javascript
---

Following are the list of abstract methods associated with Queue Data Structure

- Enqueue - Adds an item to the beginning of Queue
- Dequeue - Returns the item at the beginning of the Queue and removes it from Queue
- Peek - Returns the item at the beginning of the Queue without removing it
- Size - Returns the number of items in a Queue
- IsEmpty - Use it to check if the Queue is empty. It returns a boolean value

Following is the basic structure to create a custom class in JS

```javascript
class Queue {
  constructor() {
    // initialize class variables
  }

  // Class methods are defined here
}
```

We will need an array to store the Queue data, so let's initialize it in the constructor.

```javascript
constructor(){
  this.items = [];
}
```
Let's start building the methods one by one

- Enqueue - This method will take value as input and append that value to the array i.e. create a new item at the end of the array

```javascript
Enqueue(value){
  this.items.push(value);
}
```

```javascript
IsEmpty(){
  if(this.Size() == 0){
    return true;
  }
  return false;
}
```

- Dequeue - This method will return the first item in the array and removes it from the array

```javascript
Dequeue(){
  // Checks if the array is empty or not
  if (this.IsEmpty()){
    return null;
  }
  return this.items.shift();
}
```

- Peek - This method will just return the first item in the array

```javascript
Peek(){
  if (this.IsEmpty()){
    return null;
  }
  return this.items[0];
}
```

- Size - Return the size of the array

```javascript
Size(){
  return this.items.Length;
}
```

- IsEmpty - Check if the length of array is 0 or not and return a boolean value based on that


Let's combine all of these methods and write it as a single class

```javascript
class Queue {
  constructor(){
    this.items = [];
  }

  Enqueue(value){
    this.items.push(value);
  }

  Dequeue(){
    if (this.IsEmpty()){
      return null;
    }
    return this.items.shift();
  }

  Peek(){
    if (this.IsEmpty()){
      return null;
    }
    return this.items[0];
  }

  Size(){
    return this.items.Length;
  }

  IsEmpty(){
    if(this.Size() == 0){
      return true;
    }
    return false;
  }
}
```

Let's test this with some examples

```javascript
let queueObj = new Queue();

queueObj.Enqueue(1); // [1]
queueObj.Enqueue(2); // [2,1]
queueObj.Peek();     // [2,1] returns 1
queueObj.Dequeue()   // [1] returns 1
queueObj.IsEmpty()   // [1] returns false
queueObj.Dequeue()   // [] returns 2
queueObj.IsEmpty()   // [] returns true
```
