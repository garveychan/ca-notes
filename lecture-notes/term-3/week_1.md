# Week 1 Lecture Notes

## Tuesday 15/06/21

### Functions

```
function Person(name, dob) {
	// 1. Creates an empty object
	// 2. Assigns `this` to the empty object
	// 3. Sets up the prototype chain
	// 4. Return the object reference to `this`
	this.name = name;
	this.dob = dob;
	this.age = function () { return 66; }
}

var adam = new Person('Adam Ant');

console.log(adam.name);
console.log(adam.age());

```

```
console.dir(adam.__proto__)
console.dir(Person.prototype)
```
The above prototype methods allow us to access the prototype chain for the `Person` object.

Note - `console.dir` logs an object with all of its properties.

### Walking the DOM

querySelector vs getElementById

Note - querySelector is static while getElement methods are dynamic.

i.e. if a variable has been assigned a query, the variable's value won't change when the DOM changes.
Conversely, the variable will be updated if it is assigned the Element and the DOM changes.

`appendChild()` allows us to append an element to a node.

Event Propagation - Event propagation is a mechanism that defines how events propagate or travel through the DOM tree to arrive at its target and what happens to it afterward.
(Bubbling / Capturing)

https://www.tutorialrepublic.com/javascript-tutorial/javascript-event-propagation.php

### Word Counter JS Frontend

'State' - the data that the application holds at that point in time.

`First Order State`, `Derived State`

Tachyons - CSS framework which formed the basis for Tailwind.

Immediately Invoked Function Expression (IIFE) - A JS function that runs as soon as it is defined.

``` JavaScript
(function() {
  statements
})();
```

`.match()` - JS function used on a string which returns an array of strings matching the regex provided as an argument.

`.match(/\S+/g)` - match strings separated by whitespace

## Wednesday 16/06/21

### Word Counter cont.

Sometimes .js files are called in at the bottom of a HTML file so that the functions are called after the DOM has been intialised with HTML.
A more professional way to do this is to add an Event Listener for event 'DOMContentLoaded' which invokes the core functions of the script.

```
document.addEventListener("DOMContentLoaded", () => initialise());
```

`Object.assign` - The Object.assign() method copies all enumerable own properties from one or more source objects to a target object. It returns the target object.
Note - any existing properties will be overriden by subsequent assignments - order is important.

```
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget);
// expected output: Object { a: 1, b: 4, c: 5 }
```

Implicit return of an arrow function - 

```
setState(() => ({text: text}));
```

If an object property is to be assigned the value of a variable with the **same name** as the property then the assignment can be shortened -

```
setState(() => ({text}));
```

### React

Documentation - reactjs.org

https://reactjs.org/docs/thinking-in-react.html

`npx` - node package execute

Note - recommended to keep React app and Rails app separate - JS implementation in Rails is convoluted.

`class` and `for` are reserved words in JavaScript.
Thus, when writing JSX (JavaScript XML) we must use `className` and `htmlFor`.
