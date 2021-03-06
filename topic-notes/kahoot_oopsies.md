# Kahoot Oopsies

<hr>

#### Term 1

##### Ruby

`%` - Modulus operator - returns remainder
`**` - Exponent operator

``` Ruby
"cat" * 3
```
The above evaluates as "catcatcat" not Error.

`break` - exits loop
`next` - moves loop to next iteration

`.select` - returns an **array** of the selected elements based on specified criteria. NOT the element itself. `.each` will iterate through the array and perform the specified actions.

Hash symbol syntax -
``` Ruby
directory = {name: "Jim", age: 25} #same as abelow
directory = {:name => "Jim", :age => 25} #same as above
directory[:age] = 25 #must initialise with :symbol syntax
```

Methods are defined in `snake_case`.

`self.class` is a class method.
`@variable` is an instance variable.

Classes are the blueprints of objects, not the other way around.

Short circuit logic: 3 < 4 || 4 < 1 returns true.


Ruby interprets from left to right, there can't be spaces in if/else blocks:
``` Ruby

4 < 3 ? puts "Yes" : puts "No" # => Error

puts 4 < 3 ? "Yes" : "No" # => "No"

4 < 3 ? (puts "Yes") : (puts "No") # => "No"

```

<hr>

#### Term 2

##### Web

HTTP error codes - 
400-499 => client errors
500-599 => server errors

e.g. 404 Not Found - **client's** URL not recognised => client error

#### Rails

Models - Singular
Controllers - Plural

Recipes - Controller
Recipe - Model

#### CS Fundamentals - Bases

Hexadecimal (Base 16)
Numbers only go from 0-15

|Decimal|0|1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|16|17|18|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Base 11|0|1|2|3|4|5|6|7|8|9|A|10|11|12|13|14|15|16|17|
|Hexadecimal|0|1|2|3|4|5|6|7|8|9|A|B|C|D|E|F|10|11|12|

Hexadecimal and Binary can be quickly converted with a hack:

Hexadecimal 0xFE == 1111 1110
0b1111 => 15 Base 10 => 0xF
0b1110 => 14 Base 10 => 0xE

Binary sets of 4 add up to 15 so they can capture the full set of hexadecimal numbers/letters.

##### Rails Models

Model file name convention - lowercase singular - recipe.rb

To seed your application after seed file has been created - run db:seed

<% %> does not print to browser - requires `=` sign - <%= %>

#### Rspec

`it` is the method that sets individual tests - not `describe`
`expect` lets you create assertions
`context` / `describe` - encapsulates multiple tests

describe ###
-- it ###
---- expect ###

<hr>

#### Term 3

##### JavaScript/React

React requires `index.js` in its build.

`let a = "false" && "null"`

`a` is set to `"null"` because `"false"` is truthy.

React Component Lifecycle (Mounting) - 
```
constructor() -> static getDerivedStateFromProps() -> render() -> componentDidMount()
```

https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/

Calling `setState` will cause component to re-render.


