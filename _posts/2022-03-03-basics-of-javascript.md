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
// create a script tag and reference the app.js file inside it as src
// Inside the app.js file
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
console.log(`Hello ${firstName} ${lastName}`); // string interpolation - we use backtick (`) for string interpolation
```

### Arrays
An array is a special variable, which can hold more than one value.
It uses a zero based counting system. First element will be at index 0.
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

### Conditionals
1. if, else if, else :
```
const firstName = 'Bob';
const lastName = 'Mc';
if (firstName === 'Bob' && lastName === 'Mc') {
    console.log('Hello teacher'); // prints this
} else {
    console.log('Hello student');
}
```
Difference between == and ===
```
const x = '1';
const y = 1;

if (x == y){
    console.log('Two values are equal'); // prints this though the values are not equal.
}
if (x === y){
    console.log('Two values are equal'); // won't print this
}
```
2. switch :
```
const day = 'Tuesday';
switch (day) {
    case 'Monday':
        console.log('Welcome to the first day of the week');
        break;
    case 'Tuesday':
        console.log('I hope your week is going well');
        break;
    default:
        console.log('I don\'t know which day of the week that is');
        break;
}
```

### Loops
1. for
```
const people = ['Tim', 'Sue', 'Dan', 'Mary', 'Bob'];

for (let i = 0; i < people.length; i++) {
    console.log(people[i]);
}  
```
2. for of
```
const people = ['Tim', 'Sue', 'Dan', 'Mary', 'Bob'];

for (const person of people) {
    console.log(person);
} 
```
3. foreach
```
const people = ['Tim', 'Sue', 'Dan', 'Mary', 'Bob'];

people.forEach(function(person){
    console.log(person);
});
```
4. while
```
const people = ['Tim', 'Sue', 'Dan', 'Mary', 'Bob'];

while (people.length > 0) {
    console.log(people.pop());
}
```
5. for in
```
const person = {
    firstName: 'Tim',
    lastName: 'Corey',
    age: 31,
    isAlive: true,
    address: {
        city: 'Dallas',
        state: 'Texas'
    },
    fullName: function () {
        return `${this.firstName} ${this.lastName}`;
    }
};

for (const prop in person) {
    // console.log(`${prop}: ${person[prop]}`);
    if (person.hasOwnProperty(prop)) {
        console.log(`${prop}: ${person[prop]}`);
    }
}
```

### Functions
A JavaScript function is a block of code designed to perform a particular task.
```
function add(x, y) {
    return x + y;
}

console.log(add(1,2)); 
```
using default values in function parameters
```
function add(x = 2, y = 6) {
    return x + y;
}
console.log(add());
```

### Arrow Functions
Subtraction using arrow function
```
const subtract = (x, y) => {
    return x - y;
}
// or
const subtract = (x, y) => x - y;
```
Filtering using arrow function
```
const people = ['Tim', 'Sue', 'Dan', 'Mary', 'Bob'];

const filtered = people.filter(p => p.substring(0, 1) === 'T');
```

### Objects
In JavaScript, almost "everything" is an object.
All JavaScript values, except primitives, are objects. A primitive value is a value that has no properties or methods. A primitive data type is data that has a primitive value. Primitive values are immutable (they are hardcoded and therefore cannot be changed). *if x = 3.14, you can change the value of x. But you cannot change the value of 3.14.*
**Object values are written as name : value pairs (name and value separated by a colon)**.
```
const person = {
    //key:value pairs
    firstName: 'Bob', //propertyName:value
    lastName: 'Builder'
};
```
A more complex object with sub objects
```
const person = {
    //key:value pairs
    firstName: 'Bob',
    lastName: 'Builder',
    age: 31,
    isAlive: true,
    address: {
        city: 'Dallas',
        state: 'Texas'
    },
    fullName: function () {
        return `${this.firstName} ${this.lastName}`;
    }
};
person.firstName = 'Bobby';
person.address.country = 'USA';

console.log(person.fullName());
```
**A JavaScript object is a collection of named values**

Deconstructing objects
```
const person = {
    //key:value pairs
    firstName: 'Tim',
    lastName: 'Corey',
    age: 31,
    isAlive: true,
    address: {
        city: 'Dallas',
        state: 'Texas'
    },
    fullName: function () {
        return `${this.firstName} ${this.lastName}`;
    }
};
// Deconstructing the object
const {firstName, age, address: {city}} = person;
console.log(firstName);
// This is similar to doing:
const fn = person.firstName;
const age = person.age;
const city = person.address.city;
```

### this keyword
The *this* keyword refers to different objects depending on how it is used:
- In an object method, *this* refers to the object.
- Alone, *this* refers to the global object (Window in DOM).
- In a function, *this* refers to the global object.
- In a function, in strict mode, *this* is undefined.
- In an event, *this* refers to the element that received the event.
- Methods like call(), apply(), and bind() can refer this to any object.

### JSON (JavaScript Object Notation)
JSON is a format for storing and transporting data. API's transfer data in the form of JSON.
**The JSON syntax is derived from JavaScript object notation syntax, but the JSON format is text only** The JSON format is syntactically identical to the code for creating JavaScript objects.
JSON names require double quotes. JavaScript names do not.
Because of this similarity, a JavaScript program can easily convert JSON data into native JavaScript objects.
```
const person = {
    firstName: 'Tim',
    lastName: 'Corey',
    age: 31,
    isAlive: true,
    address: {
        city: 'Dallas',
        state: 'Texas'
    },
    fullName: function () {
        return `${this.firstName} ${this.lastName}`;
    }
};
const recievedInfo = JSON.stringify(person);
const parsedInfo = JSON.parse(recievedInfo);
console.log(parsedInfo.firstName);
```
- Converts javascript object to JSON:
```JSON.stringify(object)```
- Converts JSON back to javascript object:
```JSON.parse(json)```

### Classes
Classes are blueprints. The instance of a class creates a new object off the blueprint.
ECMAScript 2015, also known as ES6, introduced JavaScript Classes. JavaScript Classes are templates for JavaScript Objects.
```
// class = blueprint, class instance = house
class Person {
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
}

const person1 = new Person('Tim', 'Corey');
const person2 = new Person('Sue', 'Storm');

console.log(person1.firstName);
console.log(person2.firstName);
```

private fields, get, set
get, set helps protect our data.
```
class Person {
    #social = ''; // private variable, can only be accessed inside the class using get/set
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
    get ssn() {
        return `***-**-${this.#social.substr(this.#social.length - 4)}`;
    }
    set ssn(social) {
        this.#social = social;
    }
    getFullName = () => `${this.firstName} ${this.lastName}`;
}

const person1 = new Person('Tim', 'Corey');
person1.ssn = '123-45-5789'; // accessing set(){}

console.log(person1.ssn);
console.log(person1.getFullName());
```
*Note:* [JavaScript Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)

### IIFE (Immediately Invoking Function Expression)
It is a JavaScript function that runs as soon as it is defined.
syntax:
```
(function () {
  /* ... */
})();
```
*In the syntax the first set of parenthesis () will contain the function and the next set (); will execute the function immediately, which will pass in parameter names.*
Example: suppose we are using an external library in our project and it has a method with the same name as one of our local methods, this will cause confusion when calling the method by it's name.
```
function greetUser() {
    console.log('Hello User');
}

function greetUser() {
    console.log('Welcome to the app');
}

greetUser(); // This will log: "Welcome to the app" the second function overrides the first one.
```
We can solve this by creating an IIFE:
```
// IIFE
// Everything inside this module is inside 'app' namespace
(function (app) {
    app.greetUser = function () {
        console.log('Hello user');
    }
})(window.app = window.app || {});

function greetUser() {
    console.log('Welcome to the app');
}

greetUser();
app.greetUser(); // function is inside the namespace app
```

We can also extend an IIFE as follows:
```
(function (app) {
    app.greetUser = function () {
        console.log('Hello user');
    }
    app.Person = class {
        constructor(firstName, lastName) {
            this.firstName = firstName;
            this.lastName = lastName;
        }
    }
})(window.app = window.app || {});

function greetUser() {
    console.log('Welcome to the app');
}

greetUser();
app.greetUser();

// Extending the IIFE
(function (app) {
    app.goodByeUser = function () {
        console.log('GoodBye');
    }
})(window.app = window.app || {});

app.goodByeUser();
```

### Scope
It is the concept of where we can see the variables.
Scope determines the accessibility (visibility) of variables.

JavaScript has 3 types of scope:

- Block scope
- Function scope
- Global scope
```
var a = 4;

// functions create a new scope
function testing() {
    var a = 5;
    console.log(`Inside testing(): ${a}`);
}
testing(); // prints 4
console.log(`global: ${a}`); // prints 5
```

Now if we do this inside an if block
```
var b = 4;

if (true) {
    var b = 5;
}

console.log(b); // prints 5, because the whole thing is a single scope for var
```

- **If we use *let/const*, they are not scoped at the function level, but at the block level.**
```
let b = 4;

if (true) {
    let b = 5;
    console.log(b); // prints 5
} // let only lives till end of this block / braces

console.log(b); // prints 4
```

### use Strict
It checks for certain things a shows an error for cases where javascript normally doesn't have an issue.
"use strict"; Defines that JavaScript code should be executed in "strict mode".
Strict mode is declared by adding "```use strict";``` to the beginning of a script or a function. Declared at the beginning of a script, it has global scope (all code in the script will execute in strict mode):
- Declare variables before you use them.
- Checks for duplicate parameters in a function.
- Deleting a variable (or object), functions is not allowed.
- Writing to a read-only property is not allowed.
```
'use strict';
a = 2;
console.log(a); // shows error since variable not declared.
```