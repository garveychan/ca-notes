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

### Word Count JS Frontend

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
