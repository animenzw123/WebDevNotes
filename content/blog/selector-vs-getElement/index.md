---
title: getElementById vs querySelector
date: "2020-12-03T23:46:37.121Z"
keyword: "javascript"
---

The JavaScript **querySelector()** method lets you retrieve an element from the DOM, or the web page, using a CSS selector. This method comes with a sister function called **querySelectorAll()** which selects all the elements that match a particular selector from the DOM.

The **getElementById()** method, on the other hand, retrieves an element based on its ID attribute, hence the name. This method is more restrictive than querySelector because you can only retrieve elements based on their particular ID.

## getElementById
Syntax:
```js
element = document.getElementById(id);
```
Returns a reference to the element by its ID. If the element with the specified ID is not in the document, it will returns null.

## querySelector
Syntax:
```js
element = document.querySelector(selectors);
```
Returns the first element within the document that matches the specified group of selectors, or null if no matches are found.

## Difference between them
Both of these functions are very similar in what they can do in term of DOM manipulation, but getXXXByXX function returns element **dynamically**, while querySelector returns element **statistically**.

See example below :

```html
    <ul>
        <li>111</li>
        <li>222</li>
        <li>333</li>
    </ul>
```
If we use querySelector to manipulation it :
```js
var ul=document.querySelector('ul');
        var list=ul.querySelectorAll('li');
        for(var i=0;i<list.length;i++){
            ul.appendChild(document.createElement('li'));
        }//now it create 3 new li and append them into ul
        console.log(list.length) //however, the result is still 3, not 6
```
On the other hand, if we use selectorElementById :
```js
var ul=document.getElementsByTagName('ul')[0];
        var list=ul.getElementsByTagName('li');
        for(var i=0;i<list.lenth;i++){
            ul.appendChild(document.createElement('li'));
        }   
        console.log(list.length)// The result will be 6, not 3
```
## Performance
Lone story short, getElementById is faster than querySelector.