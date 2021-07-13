---
title: Javascript keyword:'this'
date: "2020-12-14T14:17:11.169Z"
description: Let's discuss the meaning of 'this'.
keyword: "javascript"
---
>'this' is a javascript keyword. It is an object automatically generated inside the function body when the function is running, and can only be used inside the function body.

***this*** has different values depending on where it is used:
* In a method, ***this*** refers to the **owner object**.
* Alone, ***this*** refers to the **global object**.
* In a function, ***this*** refers to the **global object**.
* In a function, in strict mode, ***this*** is **undefined**.
* In an event, ***this*** refers to the element that received the event.
* Methods like call(), and apply() can refer ***this*** to any object.

##### this in a method
In the example ***this*** refers to the **person** object. The person object is the **owner** of the fullName method.
```js
// Create an object:
const person = {
  firstName: "John",
  lastName: "Doe",
  fullName : function() {
    return this.firstName + " " + this.lastName; // this refers to person
  }
};

// Display data from the object:
console.log(person.fullName());
```

##### this alone:
```js
let x = this;
console.log(x) // Window
```
##### this in a Function (default)
>In a JavaScript function, the owner of the function is the default binding for this. Because function could be considered as a method of the object Window. So, in a function, this refers to the Global object [object Window].

```js
function myFunction() {
  return this; //Window
}
```
##### this in a Function (strict)
>JavaScript strict mode does not allow default binding. So, when used in a function, in strict mode, this is undefined.

##### this in a constructor
>When using this inside a constructor, this refers to the object that been created by the constructor
```js
var x = 2;
function Obj() {
  this.x = 1;
}

var obj = new Obj();
console.log(obj.x) // 1
console.log(x)  // 2
```

##### this in Event Handlers
>In HTML event handlers, this refers to the HTML element that received the event

For example, ***this*** refers to the button element below:
```html
<!DOCTYPE html>
<html>
    <body>
        <button onclick="this.style.display='none'">Click to Remove Me!</button> 
    </body>
</html>
```

##### Object Method Binding
>In these examples, this is the person object (The person object is the "owner" of the function):
```js
// Create an object:
const person = {
  firstName  : "John",
  lastName   : "Doe",
  id     : 5566,
  myFunction : function() {
    return this;
  }
};

// Display data from the object:
document.getElementById("demo").innerHTML = person.myFunction(); // [object Object] 
```
##### Explicit Function Binding
>The ***call()*** and ***apply()*** methods are predefined JavaScript methods. They can both be used to call an object method with another object as argument.

In the example below, when calling person1.fullName with person2 as argument, ***this*** will refer to person2, even if it is a method of person1:
```js
const person1 = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
const person2 = {
  firstName:"John",
  lastName: "Doe",
}
let x = person1.fullName.call(person2); 
document.getElementById("demo").innerHTML = x; // John Doe
```

