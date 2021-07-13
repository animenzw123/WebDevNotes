---
title: Reference and value
date: "2020-12-16T22:32:11.169Z"
description: The concept of reference and value.
keyword: "javascript"
---
> In javascript, when you assign value to a variable, it has two different ways to achieve that: assign value or assign reference.

The main difference between the two is that passing by ***value*** happens when assigning ***primitives*** while passing by ***reference*** when assigning ***objects***.

##### value
```js
let a=10
let b=a
a=11
console.log(a,b) //11, 10
```
When assign primitives such as string, number, boolean or symbol to a variable. In memory it works like below:
>a=10, it generate a key value pair and save them into stack

| key | value |  
| :---  | :---|
| a   | 10    |
>b=a

| key | value |
| :---  |:---|
| a | 10 |
| b | 10 |
>a=11

| key | value |
| :--- |:--- |
| a | 11 |
| b | 10 |

##### reference
```js
let a = {age:10}
let b = a
b.age = 11
console.log(a.age) // 11
```
But if you assign object to a variable, in memory it works like below:
>let a = {age:10}, it save the reference address of the object instead of the value of the object in the stack


| key | address |
| :--- |:--- |
| a | address1 |

> and in the heap it save the object value:

| address | value |
| :--- |:--- |
| address1 | {age:10} |

> Therefore, when assign b=a, they will share the same reference address in the stack

| key | address |
| :--- |:--- |
| a | address1 |
| b | address1 |

and this is why when you change the value of **b**, it will also effect **a**

> b.age = 11

| address | value |
| :--- |:--- |
| address1 | {age:11} |

##### Why make reference instead of value?
It is because normally object could be huge, and if we all save them as key-value pairs in the stack, it will lead to a heavy memory cost. 