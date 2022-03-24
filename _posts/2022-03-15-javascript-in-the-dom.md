---
title: JavaScript in the DOM
author: Adithya Vijay
date: 2022-03-15 17:00:00 +0550
categories: [Blogging, programming]
tags: [development programming javascript DOM]     # TAG names should always be lowercase
---

### Introduction
There are three things associated with working with JavaScript
- Window
- Document
- DOM

**1. Window**: It is the global scope.

```
let a = 1; is actually window.a a attaches itself to the global scope that is the window.
```

**2. Document**: All the things rendered on our page. Everything is rendered inside the document

```
window.document - this is everything on our actual page
```

**3. DOM**: Document Object Model - This is a model which holds all the object in our page/document. We can manupulate the dom to change the user experience.

### DOM

There are different ways of selecting objects in the dom:
1. Get element by Id

```
document.getElementById('id-name');
```

2. QuerySelector
querySelector will select the first element which uses the class name/ id/ name of tag. It will give back the first element.

```
document.querySelector('.class-name'); - select using class
document.querySelector('h1'); - select using html tag name
document.querySelector('#id-name'); - select using id
document.querySelector('div ul li'); - select the li inside the ul in the div. (We can dial into the exact element we are looking for)
```

3. QuerySelectorAll
querySelectorAll will select all the elements from the page. We can use it to select and manipulate all the elements with similar class/ id/ tag name.

```
let q = document.querySelectorAll('p');
q.forEach(el => console.log(el));
```

### DOM Samples
- Change text of an element

```
const p = document.getElementById('first-paragraph');
p.innerText = 'This is a test';
```
- Add html to an element

```
const list = document.querySelector('ul');
list.innerHTML = '<li>Test1</li><li>Test2</li>'
```
- Remove an element

```
const p2 = document.querySelector('.support-paragraph');
p2.remove();
```
- Change style of an element

```
const headingItem = document.querySelector('h1');
headingItem.style.color = 'red';
headingItem.style.fontSize = '1.25rem';
```
- Adding a class to an element

```
const p1 = document.querySelector('p');
p1.classList.add('dark-mode');
```

- Removing/Adding a class from each of the element in the page

```
const paragraphs = document.querySelectorAll('p');
paragraphs.forEach(el => {
    el.classList.remove('support-paragraph')
    el.classList.add('dark-mode')
});
```