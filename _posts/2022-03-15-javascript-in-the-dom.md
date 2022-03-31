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

### Traversing the DOM
We generally use getElementById and querySelector to find specific element in the page. They look through the entire body of our page to find the element that we want. Once we find the element we want, if we are looking for an element inside it, in the same level or outside it, we traverse that node we have already found and search inside it.
We can traverse up/out, down/in, and in the same level from the element that we have currently selected.
This is much more efficient to traverse the DOM.

- Traversing up/outside
    We can traverse upper using 'parentElement' or closest('tag-name')
- Traversing down/inside
    We can traverse inside using children or querySelector('tag-name')
- Traversing same level
    We can traverse the same level using either 'nextElementSibling' or 'previousElementSibling'
```
<body>
    <main>
        <div id="list-section">
            <ul id="key-items">
                <li>Our First LI</li>
                <li>Our Second LI</li>
                <li>Our Third LI</li>
            </ul>
        </div>
    </main>
</body>

const section = document.getElementById('list-section');
const list = section.querySelector('ul');
const items = list.children;
const itemsArray = Array.from(items);
itemsArray.forEach(el => console.log(el));

const section = document.getElementById('key-items');
const element = section.parentElement;
const mainElement = section.closest('main')
console.log(mainElement);

const listItem = document.querySelector('li');
const nextItem = listItem.nextElementSibling;
const finalItem = nextItem.nextElementSibling;
const unknownItem = finalItem.nextElementSibling;
console.log(unknownItem);

while (listItem !== null){
    console.log(listItem);
    listItem = listItem.nextElementSibling;
}
```

### Creating HTML Elements
We can add elements to the page in many different ways.
- First Method: This method is a bit slower in performance
```
const list = document.getElementById('key-items');
list.innerHTML += '<li>Our Fourth LI</li>'

const foods = ['Hamburgers', 'Hot Dogs', 'Pasta', 'Bread'];
const foodList = document.getElementById('good-foods');
foods.forEach(food => {
    foodList.innerHTML += `<li>${food}</li>`;
});
```
- Second Method: This is better compared to the first one.
```
const foods = ['Hamburgers', 'Hot Dogs', 'Pasta', 'Bread'];
const foodList = document.getElementById('good-foods');
foods.forEach(food => {
    const li = document.createElement('li');
    li.innerHTML = food;
    foodList.appendChild(li);
});
```
- Third Method: This one is the most efficient way. Here we create a document fragment and do all manipulations to the fragment and then add it to the page. Here we modify the page only once, when the fragment is added.
```
const fragment = new DocumentFragment();
foods.forEach(food => {
    const el = document.createElement('li');
    el.innerHTML = food;
    fragment.appendChild(el);
});

foodList.appendChild(fragment);
```

### Events
HTML events are "things" that happen to HTML elements.
An HTML event can be something the browser does, or something a user does.

Here are some examples of HTML events:

- An HTML web page has finished loading
- An HTML input field was changed
- An HTML button was clicked