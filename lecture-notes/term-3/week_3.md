# Week 3 Lecture Notes

## Wednesday 28/06/21

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

