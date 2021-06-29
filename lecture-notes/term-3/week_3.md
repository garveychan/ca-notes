# Week 3 Lecture Notes

## Monday 28/06/21

### Misc

https://en.wikipedia.org/wiki/Single-page_application
"A single-page application (SPA) is a web application or website that interacts with the user by dynamically rewriting the current web page with new data from the web server, instead of the default method of a web browser loading entire new pages."
e.g. gmail

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Public_class_fields
Public class fields can reduce constructor methods -

```
  constructor() {
    super();
    this.state = {
      products: null,
    }
  }

state = {products: null}
```

`faker.js` - random generator like faker gem for ruby

https://exploringjs.com
Great JavaScript books - 'exploring' series covers changes in JS.

`var x = require('module')` comes from old server-side JS syntax.

Using the `map` function's `index` to set a `key` for an element isn't optimal if drawing data from a backend service as adding/deleting any elements will cause their keys to change.
e.g. better to set a component key with product.id
```
this.state.products.map(product => {
	<ol key={product.id}>
		<li>{product.name}</li>
	</ol>
}
```

`map` must be used instead of `forEach` because `map` returns a new array which forms the `expression` that React interprets.

https://jwt.io - JSON web token - proposed web standard for creating data with optional signature and optional encryption. Tokens signed with private secret or public/private key.

## Tuesday 29/06/21

### Misc

https://jsisweird.com - test for tricky JS behaviour

https://2ality.com/2021/06/temporal-api.html

**new JavaScript date time API**

### JS context

```
const obj = {
	firstName: 'Adam',
	lastName: 'Ant',
	fullName() {
		return `${this.firstName} ${this.lastName}`
	}
}

let func = obj.fullName;
console.log(func()); // context lost - func has no 'this'

let blah = { firstName: 'Burt', lastName: 'Banana' }

console.log(func.call(blah)); // 'call' executes the function in the context of its argument 'blah'

let blahFunc = func.bind(blah) // creates a perfect facsimile of the 'obj.fullName' function binded to 'blah'
console.log(blahFunc());
```

### React

Components should always be PascalCase - files and function names.
Utility functions and others can be lowercase.

### React Routing

Route `Switch` prioritises from top to bottom.

```
/products
/products/:id
```

In the above example, '/products' will catch any URL which tries to reach a specific `product id`.
This can be resolved by adding a `exact` property to the `Route` component.

```
<Route exact path='/products'>
```

However, this can be difficult to maintain later on as the application grows.
It's best practice to structure the routes appropriately i.e. organising them based on their specificity.

```
/products/:id <- specific product
/products <- catch the rest of the product URLS if they don't exist and show all products
```

*`match` will be useful for assignment*
https://reactrouter.com/web/api/match

```
A match object contains information about how a <Route path> matched the URL. match objects contain the following properties:

    params - (object) Key/value pairs parsed from the URL corresponding to the dynamic segments of the path
    isExact - (boolean) true if the entire URL was matched (no trailing characters)
    path - (string) The path pattern used to match. Useful for building nested <Route>s
    url - (string) The matched portion of the URL. Useful for building nested <Link>s
```

