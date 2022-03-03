---
title: JavaScript Basic Concepts
author: Adithya Vijay
date: 2022-03-03 22:30:00 +0550
categories: [Blogging, programming]
tags: [development programming javascript]     # TAG names should always be lowercase
---

### Introduction
We structure the web using *HTML* and style it using *CSS*. We use *JavaScript* to power the web with scripting. <br>
**JavaScript** is a powerful scripting language that allows us to create dynamic pages and interactive applications on the web.

### History Of JavaScript
In the mid 90's when Netscape navigator was new, they commissioned a new scripting language. Brendan Eich designed this scripting language. Brendan created and shipped a version of the scripting language (called LiveScript) within 2 weeks along with the Navigator beta release in 1995. <br>
The name was later changed from LiveScript to JavaScript. Microsoft create something similar to Javascript called JScript for internet explorer. With the rise in popularity of Internet Explorer, Microsoft could dictate the terms and could thus push out JavaScript for a while in favour of JScript. <br>
In 2004, the successor of Netscape, Mozilla Firefox browser was released and JavaScript started to take back the market share. <br>
In 2008, Google released Google Chrome and brought back more life to JavaScript. (Google Chrome introduced the V8 JavaScript engine that was faster than it's counterparts). AJAX also came around during this time with the idea that we don't have to reload a page to send data back to the server or get it from the server. This led to creation of many libraries like JQuery, MooTools etc. <br>
As Javascript started to become more popular, it's standardisation started to solidify for it. In 2009, ECMAScript 5 came out, it was the start of modern javaScript. In 2015, ECMAScript 6 was released which is the current version of JavaScript. It can be compared to HTML5 and CSS3.

### Basics of JavaScript
We can write JavaScript inline in the html document inside a *script* tag in the body. Since an HTML document renders from top to bottom, we place the script tag at the bottom of the body since, scripts can sometimes be large and take a lot of time to load.

### Logging to the console 
- Inline
```
<script>
    console.log('Hello World!');
</script>
```
- From another file
```
<script src="js/app.js"></script>

app.js
console.log('Hello World from another file!');
```

### Variables
Variables hold data. They are used to pass around data to other locations and use it. We have 3 different ways to declare variables
- *var* - It has been there since the beginning. The type doesn't matter and can be changed throughout. Not a preferred way of declaring a variable.
- *let* - Scoped variable. The type can be changed. If something is designed to change, use let. *Can be declared first and value can be assigned later*.
- *const* - This value will be constant. Unless you know something is designed to changes, use const. *Needs to be defined during declaration*

1. **var**
```
    var testString = 'this is a test';
    var testNumber = 98;
    console.log(testString);
    console.log(testNumber);
```
2. **let**
```
    let testString = 'this is a test';
    testString = 'This is a better string';
```
3. **const**
```
    const testString = 'this is a test';
    testString = 'This is a better string'; // causes error here
```
- If we declare a variable, but haven't assigned a value to it, it's value will be *undefined*. Type of the variable is inferred from the value assigned to it.
```
var i;
console.log(i); // undefined
```

- **Hoisting** - It is the default behavior of moving all the declarations at the top of the scope before code execution. Hoisting can only be done for *var*. let doesn't support Hoisting.
```
i = 5;
console.log(i);
var i = 2;
```
During code execution this will be changed to :
```
var i;
i = 5;
console.log(i);
i = 2;
```

- **String interpolation** 
```
const firstName = 'First';
const lastName = 'Last';
console.log(`Hello ${firstName} ${lastName}`); // string interpolation
```

### Arrays
An array is a special variable, which can hold more than one value.
It uses a zero based counting system. First element will be at 0.
```
const people = ['Tim', 'Sue', 'Mary', 'John'];

people.push('Grey'); // add element to the array

people.pop(); // pops the last element from the array.

people.indexOf('Tim'); // gives 0
```
Important methods:
- *array.filter()*
```
const people = ['Tim', 'Sue', 'Mary', 'John'];
const coolPeople = people.filter(function (person) {
    return person.startsWith('T') === true;
});
console.log(coolPeople);
```
- *array.map()*
```
const people = ['Tim', 'Sue', 'Mary', 'John'];
const firstLetters = people.map(function (person) {
    return person.substring(0, 1);
});
console.log(firstLetters);
```
- In JavaScript, arrays use numbered indexes.
- In JavaScript, objects use named indexes.