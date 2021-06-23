# Week 2 Lecture Notes

## Monday 21/06/21

### JavaScript

Four Pillars of JavaScript

1. Datatype Coercion
2. Prototypical Inheritance (and Classes)
	f.prototype; o.__proto__; Object.getPrototypeof(o)
3. Dynamic and Lexical `this`
4. Functions and Closures
5. Asynchronous Code - Callbacks, Promises, and Async

### Asynchronous Code

Call Stack - Thread of Execution

https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop

## Tuesday 22/06/21

### Promises

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises
- Good guide for promises

'You don't know JavaScript - Kyle Simpson'
https://github.com/getify/You-Dont-Know-JS
- Intermediate/Advanced JavaScript Books
- Considered 'bibles' in the industry

JavaScript - The Definitive Guide - O'Reilly
- The 'bible' of the language, good to know if pursuing a career with JS

Good to be familiar with the 'bible' of whichever technology being pursued for career

https://www.oreilly.com/
Learning platform for technology teams

### JSON

JavaScript Object Notation - sent as string, resembles an object.
'Keys' in object must always be strings enclosed with double quotes "".

### Web APIs

https://developer.mozilla.org/en-US/docs/Web/API
Good to explore the APIs available to web developers.
e.g. HTML Drag and Drop as an API.
 
XMLHttpRequest was the historical way of fetching information from the web.
The underlying functions form the basis of modern Web APIs which are more intuitive and efficient to use.

https://axios-http.com/
Axios is a simple promise based HTTP client for the browser and node.js. Axios provides a simple to use library in a small package with a very extensible interface.
Good to be aware of this - likely to be used if dealing with server-side JavaScript.

Polyfill

https://developer.mozilla.org/en-US/docs/Glossary/Polyfill
A polyfill is a piece of code (usually JavaScript on the Web) used to provide modern functionality on older browsers that do not natively support it.

Fetch
https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch
The Fetch API provides an interface accessing and manipulating parts of the HTTP pipeline - such as requests and responses.
It also provides a global fetch() method that provides an easy, logical way to fetch resources asynchronously across the network.

##### Free APIs for practice

https://github.com/public-apis/public-apis

## Wednesday 23/06/21

### React App - Stocks

https://iexcloud.io
API for curated financial data

`yarn create react-app wolf-of-react`

yarn created by the team that built react - affinity between the two technologies

##### React Structure

/build/ - production build generated with `yarn build` - not checked into git.
When hosted (for example on Netlify), the service will automatically build the production app for us.

Component code in separate files is private until it is `exported` and `imported`.

```
// StockInfo.js
export default StockInfo;

// App.js
import StockInfo from "./StockInfo";
```

##### BabelJS

Babel is a free and open-source JavaScript transcompiler that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript that can be run by older JavaScript engines. Babel is a popular tool for using the newest features of the JavaScript programming language.

JSX -> JS for our purposes

##### React Syntax (JSX)

`{ }` - curly braces used for JavaScript **expressions** (can't be used for JavaScript statements - everything in Ruby evaluates to an expression - not true for JS)

```
<div class='blue' id='first-div'>
	{ if (x) {'one'} else {'two'} }
</div>
/* this would not work */

<div class='blue' id='first-div'>
	{ x ? 'one' : 'two' }
</div>
```

The rationale is that React is for rendering - the logic would be expected to have already been done in the backend.

##### State

https://reactjs.org/docs/state-and-lifecycle.html

Stateless components - render and are disposed.
Stateful components - persist on the page and can be updated or modified.

Promoting a function to a *stateful component* - 
```
class App extends React.Component
```

```
componentDidMount() {
}
// equivalent to JS' DomContentLoaded event
```

```
constructor() {
	super()
	this.state = {
		quote: null
	}
}

this.setState( prevState => ({quote: quote}))
// sets the state of a component, intialised in the constructor method. first arg is prevState which can be used if necessary to calculate the new state

this.setState({ quote })
// this can be simplified even further if previous state isn't required and the variable name matches the property
```

```
<dl> //detailed list in JSX (list without bullet symbols)
<dt> //detailed list title
<dd> //detail
```

##### Environment Variables

`.env` file can be used to hold API tokens

```
REACT_APP_IEX_TOKEN=#######
```
Note the token must be prefixed with `REACT_APP`

```
${process.env.REACT_APP_IEX_TOKEN}
```
It can then be accessed with string interpolation as above.  

##### Context is important when invoking or declaring functions in React

```
constructor() {
    super();
    this.handleSymbolChange = this.handleSymbolChange.bind(App);
}
```

The above is a common pattern for binding a function within the class to the class so that it can be invoked thoughout the app.
