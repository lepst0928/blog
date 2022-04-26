---
layout: post
title:04-25 Javascript Notes [4/25/22]
---

# Week 4 Notes - Intro to JavaScript
General Notes (from Scrimba videos):
> no javascript is secure or private

- prevent hoisting by declaring variable with either let or const 
- hoisting = calling a variable before it is defined, will result in null (and not an error)
- let you can intialize and reassign later, const must be intialized with a value and cannot be changed
- let & const are block scoped (ie in the if block)

how to embed variables
```javascript
let username = "Jane Doe";
let message = `Hi ${username}, how are you?`;
console.log(message);
```

- for many if statements change to switch statement with case and default conditions
- falsy values = false, 0, '', null, undefined, NaN
	avoid direct comparisions in conditionals
	use the === (strict equals operator), it does not convert types
	convert to real Boolean values where needed

- closures allow us to remember values, must call function in a different scope than where the function was originally defined
```javascript
function countdown() {
  let countFromNum = 11;
  return function decrease() {
    countFromNum -= 1;
    return countFromNum;
  }
}

const countingDown = countdown();
```

- primitive: undefined, null, boolean, number, string, symbol
- objects hold primitives

- use [] to dynamically update objects such as keys; cannot use . notation for values that can change

```javascript
const createdUser = { ...user, ...newUser, verified: false };
```
- prototypical inheritance - each instantiated object (from constructor function) inherits from prototype
- inheritance = extends ie. class SaleProduct extends Product {...

- Important: _class = should not be modified/mutated, otherwise use getters and setters

- DOM turns page into objects; event listeners
```javascript 
document.body.addEventListener('click', event => {
  if (!event.target.closest('.post')) return; 
```
