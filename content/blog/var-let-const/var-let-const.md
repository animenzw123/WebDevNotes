---
title: Difference between var, const and let?
date: "2020-12-12T20:23:32.169Z"
description: Let's discuss the difference between var, const and let.
keyword: "javascript"
---
In the process of learning JavaScript, I found it difficult to distinguish between var, let and const. So let's discuss the difference between them.

First, **let** and **const** are additional feature that came with **ES6**, both of them are used for **variable declaration**. Before the advent of ES6, **var** declarations ruled. There are issues associated with variables declared with var, though. That is why it was necessary for new ways to declare variables to emerge.
## var
>var declarations are **globally scoped** or **function/locally scoped**. 

The scope is **global** when a var variable is declared outside a function. which means any variable that is declared by var outside a function block is available for the whole window.

var is function scoped when it is declared within a function. This means that it is available and can be accessed only within that function.
```js
var global = "global";

function newFunction() {
    var local = "local";
    console.log(global)
}
newFunction(); // global
console.log(local); // error: local is not defined
```

##### Hoisting of var
>Hoisting is JavaScript's default behavior of moving declarations to the top, which means a variable can be declared after it has been used.

For example:
```js
var num = 123;
function foo(){
    console.log(num);  // undefined
    var num = 456;
    console.log(num) // 456
}
foo()
```
Why the first console.log is undefined? It is because this code is interpreted as following:
```js
var num = 123;
function foo(){
    var num;
console.log(num);  // undefined
num = 456;
console.log(num) // 456
}
foo()
```

##### The problem of var
```js
var a = "initial value";

if (truethings) {
    var a = "value changed"; 
}

console.log(a) // "value changed"
```
The problem occurs if you accidently redefine the value of the variable and do not realize that it has already been defined before.

## let
>let is block scoped, a block is a chunk of code bounded by {}.

So a variable declared in a block with let  is only available for use within that block. Let me explain this with an example:
```js
let a = "initial value";
let truethings = true;

if (truethings) {
    let a = "value changed";
    console.log(a);// "value changed"
}
console.log(a) // "initial value"
```

##### let can be updated but not re-declared.
We can do this:
```js
let greeting = "say Hi";
greeting = "say Hello instead";
```
But this will leads to an error:
```js
let greeting = "say Hi";
let greeting = "say Hello instead"; // error: Identifier 'greeting' has already been declared
```

##### Hoisting of let
Just like **var**, **let** declarations are **hoisted** to the top. Unlike **var** which is initialized as **undefined**, the **let** keyword is **not initialized**. So if you try to use a **let** variable before declaration, you'll get a **Reference Error**.

## const
>Variables declared with the const maintain constant values.
>const declarations are block scoped
```js
const num = 456
if(true){
    const num = 789;
    console.log(num); // 789
}
console.log(num) // 456
```

##### const cannot be updated or re-declared
>The value of a variable declared with const remains the same within its scope. 

So this is wrong:
```js
const greeting = "say Hi";
greeting = "say Hello instead";// error: Assignment to constant variable. 
```
And this is wrong, either:
```js
const greeting = "say Hi";
const greeting = "say Hello instead";// error: Identifier 'greeting' has already been declared
```

>This behavior is somehow different when it comes to objects declared with const. While a const object cannot be updated, the properties of this objects can be updated. 

Therefore, if we declare a const object as this:
```js
const greeting = {
    message: "say Hi",
}
```
while we cannot do this:
```js
greeting = {
    newMessage: "say Hello instead";
} // error:  Assignment to constant variable.
```
we can do this:
```js
greeting.message = "say Hello instead";
console.log(greeting.message); // "say Hello instead"
```




