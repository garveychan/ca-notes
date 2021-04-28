# Ruby Notes

### Resources

##### Documentation
https://www.ruby-lang.org/en/documentation/
https://ruby-doc.org/

##### Guides
https://poignant.guide/book/chapter-1.html
https://pine.fm/LearnToProgram/chap_00.html

##### Practice
https://www.codecademy.com/learn/learn-ruby
https://try.ruby-lang.org/

### Background

An object-oriented scripting language.

### Interactive Ruby Shell 

**irb** in terminal to open.
**exit** to close.
**Ctrl+L** to clear terminal.

### Methods

`.class` after data to show data type.
`.chomp` "chomps" off the last character if it is whitespace/newline/etc.
`.strip` "strips or trims" off any leading or trailing whitespace/newlines/etc.

##### Type Conversion Methods

Transform data type -
- .to_s, - turn into string
- .to_i - turn into integer
- .to_f - turn into float
- .to_sym - turn into symbol

### Data Types

Primitive data types:
- Integer
    - e.g. 1, 3, 5
- Float (decimals)
    - e.g. 1.0, 3.5, 5.9
- String
    - e.g. 'Word', "Sentences are great", "Can be in single and double quotes"
- TrueClass
    - Boolean type - True
- FalseClass
    - Boolean type - False
- NilClass
    - Nil, Empty, (not zero)
- Symbol - label/identifier
    - e.g. :account_number, :balance


Complex data types:
- `{}` Hash - Unordered container of attributes
- `[]` Array - Ordered container of attributes

Complex data types can be nested e.g. array of arrays.

### Operators

##### Arithmetic
- `+` - Add
- `-` - Subtract
- `*` - Multiply
- `/` - Divide
- `%` - Modulus (Remainder)
- `**` - Exponent (Power)

Notes - If a division produces a remainder, it will not be shown as Ruby coerces the float to an integer.

``` Ruby
5/3 #=> 1
5/3.to_f #=> 1.66666666
```

##### Iteration
- `x += y` => `x = x + y`
- `x -= y` => `x = x - y`
- `x *= y` => `x = x * y`
- `x **= y` => `x = x ** y`

### Comments

`#` at beginning or end of line.
`=begin` and `=end` for multi-line.

## Constants

Constants are variables which *shouldn't* change value throughout the execution of the program. 
Syntax is either with a capital first letter, or all caps in snake_case - 

``` Ruby
Taxrate = 0.4
TAX_RATE = 0.4
```

Note that Ruby will warn you if you try to change a constant value.

##### String Interpolation

String interpolation lets us insert data into a string. We can even run Ruby code **inline**.
Interpolation needs to be in **double-quotes**.
``` Ruby
"Five plus five is #{ 5 + 5 }"
"Santa's catch-phrase is #{"HO " * 3}!"
```

### Control Structure

Ruby has standard control statements like `if`s, `case`s and `loop`s.
Control flow stops at `end`.

**If** statement
``` Ruby
raining = true

If raining == true
    puts "Carry Umbrella"
else
    puts "Bask in the sun"
end
```

**Case** statement
```Ruby
capacity = 21

when 0
    puts "good luck"
when 1..20
    puts "get to a gas station"
when 21..100
    puts "you're alright"
else
    puts "#{capacity} is not a valid value"
end
```

##### Ternary Statements

Ternary (**3**) statements are 3-part if statements written in-line with different syntax. For example, the above code could be written as -

``` Ruby

raining = true

puts raining == true ? "Carry Umbrella" : "Bask in the sun"
```

### Logical Operators

3 main types:
- and - `&&` - both sides must eval to true
- or - `||` - either side must eval to true
- not - `!` - returns the opposite value

``` Ruby
true && true
> true
true && false
> false
false && false
> false
true || false
> true
true && !false
> true
```

##### Short Circuit Logic

Control statements with logical operators

``` Ruby
If num > 0 && num % 2 == 0
    puts "positive and even number"
end
```

##### Truthy and Falsy

In Ruby, any defined variable will evaluate as `true` unless it is either **false** or **nil**, in which case it will evaluate as `false`. Note - this may differ in other languages.

``` Ruby
x = 1
y = 0
z = "yeet"
u = [] # empty array
v = {} # empty hash

a = nil
b = false

# u, v, x, y, and z will all evaluate as true. a and b will evaluate as false.
```

##### Loops
Loops are a type of control statement which allow a user to define a program which repeats a set of actions.

There are several types of loops:
- `while` - checks a condition and proceeds if satisfied; requires **explicit** iteration.
- `for` - loops for a specified range; **automatically iterates**.
- `do while` - checks condition after loop and determines if loop should be run again.
- `until` - run loop until condition satisfied.

``` Ruby
# while loop
num = 0
while num < 20
    puts num
    num += 1
end

# for loop
num = 0
for num in 0..20
    puts num
end
```

Certain keywords will change the control flow:
- `break` - exist the loop
- `next` - skips to the next iteration of the loop

### Arrays

- Arrays are **ordered** collections of items.
- They are denoted by square brackets `[]`.
- Arrays can contain any data type or even a combination of data types.
- An array's index is the number associated with the data type at that position. 
- **The index starts with 0.**

``` Ruby
example_arr = [1, 2, 3, "test", []]
puts example_arr[0] # This prints 1 from the above array
```
#### Accessing Elements
Syntax for accessing an array's elements:
``` Ruby
arr = [1, 2, 3, 4, 5, 6]
arr[2]     #=> 3 - (index 2)
arr[100]   #=> nil - (index does not exist)
arr[-3]    #=> 4 - (3 from the end)
arr[2, 3]  #=> [3, 4, 5] - (3 items starting from 2)
arr[1..4]  #=> [2, 3, 4, 5] - (index 1 to 4)
arr[1..-3] #=> [2, 3, 4] (index 1 to -3)
```

#### Multi-Dimensional Arrays

Arrays can be initialised within arrays, allowing for multi-dimensional arrays.

``` Ruby
multi_arr = Array.new(3) {Array.new(3) {|i| i}}

multi_arr #=> [[0, 1, 2], [0, 1, 2], [0, 1, 2]]

multi_arr[0,2] #=> [[0, 1, 2], [0, 1, 2]] (2 items starting from index 0)

multi_arr[0][2] #=> 2 (index 2 of the array at index 0 of multi_arr)
```

#### Array Methods

Common array methods include:

- `length` - returns the count of items in that array.
- `join` - returns a concatenation of all items in the array.
- `include?` - checks if the argument (value inputted into method) exists in the array.
- `delete` - deletes all instances of the argument in the array.
- `delete_at` - deletes the instance specified by the **index argument**.

``` Ruby
ex_arr = [1, 2, 3, 4, 5]

ex_arr.length # => 5
ex_arr.join # => "12345" (note this is a string! it is returned by the array itself is not changed).
ex_arr.include? 5 # => true
ex_arr.delete 3 # => 3 (3 is returned but it is also removed from the array)
ex_arr.delete_at 0 # => 1 (1 is at index 0 and is returned and removed from the array)
```

#### Array Mutation

##### Passed by Reference
- Arrays are generally **passed by reference** not by value i.e. assigning an existing array to a new variable merely **points** the new variable to the array's **existing memory location**. In contrast, assigning a **string** or **integer** to a new variable gives the variable a **new value** (and assigns **new memory**) which is **equal** to the old value.
- In practical terms, this means that if you make any changes to an array, those changes will also be present in a new variable which has been initialised with that existing array.
- To get around this, you can use the `.clone` method to **clone** an array to the new variable.

``` Ruby
ex_arr = [1,2,3]
# ex_arr => 1,2,3
new_arr = ex_arr
# ex_arr => 1,2,3
# new_arr => 1,2,3
ex_arr[2] = 5
# ex_arr => 1,2,5
# new_arr => 1,2,5 <------- this also changed because array was passed by reference.
```
``` Ruby
ex_arr = [1,2,3]
# ex_arr => 1,2,3
new_arr = ex_arr.clone
# ex_arr => 1,2,3
# new_arr => 1,2,3
ex_arr[2] = 5
# ex_arr => 1,2,5
# new_arr => 1,2,3 <------- this does not change. array was passed by value.
```

### Error Handling

- The default behaviour of Ruby is such that it will stop the app should any errors arise.
- We can circumvent these premature exits by using **short circuit logic** to return **nil** instead of an **error**.

``` Ruby
names = ["Jim", "Terry", "Sam"]

names[3].capitalize # => Error (there is no index of 3 in the array, program stops).
names[3] && names[3].capitalize # => Nil ('and' operator returns nil since names[3] could not be found - the error has been 'nullified').
```

### Iterators

Iterators are methods which iterate through a collection (array or hash).
Examples include -
- `.each` - iterates through the array/hash and performs the specified actions.
- `.map` - iterates through the array/hash like `.each` but returns an array with your new items.
- `.with_index` - lets you use the index of the item in your block as well.
- `.select` - selects the elements matching the specified criteria.

``` Ruby
array.map { |variable| puts variable }

hash.map do |key, value|
    puts "This is a #{key} and this is its #{value}."
end
```

### Methods

- Methods are an isolated sequence of instructions which can be called repeatedly with certain arguments. They can be user-defined.

- Methods can help facilitate the **DRY** principle (Don't Repeat Yourself).

- Methods have to be called/invoked before they are executed.

``` Ruby
def example_method(parameter_1, parameter_2) #Define the method
    puts "Example Method with #{parameter_1} and #{parameter_2}"
end

example_method (argument_1, argument_2) #Call the method
```

- Methods can be defined with default values. Remember that you must pass the name as well as the value or an error will be evaluated.

``` Ruby
def greeting(name: "stranger", language: "ruby")
    puts "welcome #{name}, we heard you are an awesome #{language} programmer"
end

greeting(name: "Jim")
# => welcome Jim, we heard you are an awesome ruby programmer
```

- Methods will return the last action specified (**implicit return**) unless an **explicit return** has been specified within the block.

``` Ruby
def sub(a,b)
    return a + b
    puts "This line will not be actioned as it occurs after the explicit return which exits the method"
end

def sub(a,b)
    a + b
end
# => a + b, Ruby will return the last action regardless even if it doesn't hae the return keyword.
```

### Ruby Gems

Gems are open-source code packaged in line with RubyGem specifications which you can use in your applications. 
They consist of:
- Gemspec (name, versions, authors)
- Code
- Documentation
- Tests

Gems can be found at http://ruby-toolbox.com or with the **command line**.

**Tips**
- Be selective with gems.
- Ensure they fit the needs of your application and are well documented, tested and maintained.
- If they are used by lots of people then that's generally a good sign.

##### Commands

`gem search` - search for a gem
`gem search ^rails` - regex syntax in search
`gem search ^rails -d` - see details about gem

`gem install` - install gem
`gem install colorize` - install gem 'colorize'
`gem install colorize -v 0.8.1` - install gem 'colorize' version 0.8.1 (good to include version in case mistyped and a similar name gem installed)

`require 'colorize'` - use installed gem in ruby

`gem uninstall colorize` - uninstall gem 'colorize'

`gem list` - show list of gems (append --help to show command options)
`gem list color` - regex to list specific gems (this will show colorize)

##### Bundler

Bundler is a gem dependency manager that can be used when your application uses gems.

The bundler itself is a gem which can be installed with `gem install bundler`.

`bundle init` - initialises your Gemfile in your application root folder (like git init).

source "https://rubygems.org" - remote source for the gems to install for this app, typically rubygems.org.

`bundle add colorize` - adds gems to your app with the following actions:
- installs the gem.
- adds the gem to the Gemfile as a dependency.
- updates Gemfile.lock (tracks dependencies of installed gems and their own dependencies as well) with the version of the installed gem.

`bundle install` - installs all dependencies for your app using Gemfile.

### Modules

A ruby module is a grouping of objects under a module name.
They allow us to encapsulate our code in a namespace so we can use it in multiple areas without name clashes. 

Objects in a module can include:
- Methods
- Classes
- Constants
- Other Modules

Modules are used for the following reasons:
- Reusability (provide methods, classes, constants used by multiple apps or app components)
- Provide a namespace (prevent name clashes)
- Enable mixins (used by classes to implement multiple inheritance)

Use module name with `.` to refer to methods and `::` to refer to classes and constants.

``` Ruby
MyLogger.info("An informational message")
puts MyLogger::SEPARATOR
MyLogger.warning("A warning")
puts MyLogger::SEPARATOR
MyLogger.error("Danger Will Robinson!")
debugger = MyLogger::Debugger.new("test")
debugger.debug("debugging message")
```

## Object Oriented Programming

##### Procedural Design

Standard design pattern:
1. Get dog name
2. Feed dog.
3. Take dog for walk.
4. Print dog daily journal.

![Dog Procedural](./assets/ruby/dog-procedural.png)

##### Object Oriented Design

Centered around what the Dog object can do instead.

![Dog OOP](./assets/ruby/dog-oop.png)
![Dog OOP](./assets/ruby/dog-oop-code.png)

### Classes

Classes are objects which can be **instantiated**. They provide a way to define an element's attributes and actions.

Example - Pet Class:
Attributes => type, name, colour, breed, size
Actions => speak, walk, eat, sleep

##### Components

- **Initialize method**
    When a class is instantiated, `Class.new`, the `initialize` method is invoked, performing any action specified within its block. It can be used to set initial attribute values and performing other operations as required.

- **Instance variables**
    These are used to store information about an **instance** of a class. It's defined with the syntax `@variable`. The `@` sign specifies that a variable is an instance variable, only applicable to that specific instance. It has **global** scope within the **class** and can be accessed by all **methods** within the class. 

- **Class variables**
    Class variables are identified by double `@@` signs e.g. `@@global`. These can be accessed **OUTSIDE** of the class, and in the broader program, which is why they're not recommended for use. 

    ``` Ruby
    @@total_pets = 0

    def self.total_pets
        @@total_pets
    end
    ```

    The program can also run into inheritance problems:
    ``` Ruby
    class Car
        @@default_max_speed = 100

        def self.default_max_speed
            @@default_max_speed
        end
    end

    class SuperCar < Car
    @@default_max_speed = 200 # and all cars in the world become turbo-charged
    end

    SuperCar.default_max_speed # returns 200, makes sense!
    Car.default_max_speed # returns 200, oops!
    ```

- **Methods**
    These define **actions** which can be performed by or on objects created by the class.
    ``` Ruby
    def greet
        puts "Hi! My name is #{@name}"
    end
    ```
- **to_s**
    A method of the parent Object which prints information of a class.
    This is commonly overridden to print useful information for each instance.

    ``` Ruby
    def to_s
        return "Pet: type - #{@type}, name - #{@name}"
    end
    ```

- **setters/getters**
    Used to give access to **instance variables** outside of the class.
    Controls access to the object from outside.
    Should follow **principle of least privilege**, only create access where **necessary**.

    ``` Ruby
    // getter - READ ACCESS

    attr_reader :name, :type

    def name
        @name
    end
    
    def type
        @type
    end

    // setter - WRITE ACCESS

    attr_writer :name, :type

    def name= (name)
        @name = name
    end

    def type= (type)
        @type = type
    end

    // accessor - READ AND WRITE ACCESS
    attr_accessor :name

    def name
        @name
    end
    
    def name= (name)
        @name = name
    end
    ```

- **Naming Conventions**
    Class names are in **PascalCase**.
    Method names are in **snake_case**.
    
### Four Pillars

#### Encapsulation (Changeability)

Encapsulation refers to how each object keeps its attributes (state) private within its scope, controlling what external entities are allowed to see and how they can interact with the information (e.g. reader/accessor etc.)

#### Abstraction (Readability)

Abstraction allows for a consistent high-level interface for interacting with objects, as complex object attributes and internal structures are 'abstracted' away from the main program.

#### Polymorphism (Flexibility)

Meaning 'many shapes' in Greek, parent objects can define methods which child objects can call upon in **different** ways to achieve varying outcomes. Since child objects are more specific, if they define methods with the same name as parent objects, they will override the method of the parent.

#### Inheritance (Reusability)

Objects can be defined in a hierarchy. Inheritance is when an object inherits attributes from another object.

There are two main types of objects used for inheritance:

- **Classes** are created in a hierarchy of inheritance, directly inheriting from the classes above it. Think vertical inheritance.
- **Modules** exist outside of the hierarchy and can be *mixed in* to another object or method. Think horizontal inheritance.

Note that a class can only inherit directly from one another class. Child classes can inherit from all classes above it in the hierarchy.

![Class Hierarchy](./assets/ruby/class-hierarchy-example.png)
![Class Extension](./assets/ruby/class-extension.png)

Inheritance lets similar class types share common attributes:
- Reduces code duplication (DRY)
- Facilitates modularity
- Facilitates code reuse
- Easier testing and maintenance

##### Syntax

``` 
class subclass < superclass    
end
```
Above code defines a subclass (child) which inherits `<` from its superclass (parent) - think superclass 'pushing' its features into the subclass. Any inheritance above the parent comes from what's called an 'ancestor' and the inheriting class is a 'descendant'.

All Ruby classes are subclasses of Object. Object is a subclass of BasicObject.

`.superclass` method can show us the superclass of an object.

##### super

The `super` method allows a class to execute a method with the same name in an ancestor superclass, moving up the hierarchy tree until it reaches the first method it finds.

This is useful, particularly for the `initialize` method if the subclass needs to be initialized in the same way as a parent class.

![super method](./assets/ruby/super-method.png)

`super()` can be used to specify that no arguments are to be passed up to the superclass method.

##### Polymorphism

Polymorphism refers to the ability for the same method to return different results depending on the object it's called on due to inheritance rules.

![Polymorphism example](./assets/ruby/polymorphism-example.png)
![Polymorphism example 2](./assets/ruby/polymorphism-example-2.png)

##### Mixins

Since classes can only inherit from their direct hierarchy, we can use **mixins** to provide features from other **modules** not directly linked to those classes.

This is achieved using the `include` keyword within the class to bring the module into play.

Mixins follow the same **naming convention** as classes - **PascalCase**.

![Mixin example](./assets/ruby/mixin-example.png)

### Error handling

Code is often too optimistic, making many assumptions including user input format, their knowledge of the application, the way the app is used, the environment it's used in, etc. 

Errors which aren't handled can lead to unexpected results - best case scenario: user frustration, worst case scenario: unusable app / security breaches.

If possible, errors should be handled internally if possible. This can be achieved with the following functions:

- `rescue`
The **rescue** keyword is placed in a block of code to execute if at any point prior, the program encounters an error. If any instructions create an issue, the flow of control will be passed to **rescue** and the code will continue to execute until **end**. If there is nothing after `rescue`, the program will simply do nothing and end the block prematurely.

``` Ruby

begin

  1 + gets

rescue

    puts "you're trying to add a string to an integer, silly"

end

```

https://ruby-doc.org/core-2.7.1/Exception.html

There are specific type of errors which can be handled (see Exceptions) with `rescue`, you can identify them in descending specificity to capture them before moving on to a more broad error.

You can also output pass exception to a variable and execute its methods:
- inspect
- message
- set_backtrace
- to_s

``` Ruby
begin
    # bad code
rescue NoMethodError #more specific error
    #FIXES
rescue StandardError => e
    puts "Error: #{e.message}"
end
```

- `raise`
**raise** allows the user to explicitly *raise* a **RuntimeError**, through which the user can specify an exception type.

![Error Raising](./assets/ruby/raising-errors.png)

As seen above, you can raise custom errors by utilising control statements, only raising the error if the specified issue has occurred.

You can define your custom error as a subclass, using it to inherit the properties of a built-in error class:

``` Ruby

class InvalidNameError < StandardError
end

def validate_name(name)
    name = name.strip # Trim whitespace
    raise InvalidNameError,
        "Name must not be empty" if name.empty?
    name
end
```

- `retry`
The **retry** keyword will bring the flow of control back to the instruction that raised the error, allowing the program to try and re-execute the code.

``` Ruby
begin
  retries ||= 0
  puts "try ##{ retries }"
  raise "the roof"
rescue
  retry if (retries += 1) < 3
end
```

- `else`/`ensure`
The **else** keyword will capture control flow after **raise** error has been evaluated and hasn't return any issues, continuing to execute any further instructions. **ensure** will execute the following code block no matter what happens in the block.

![Else/Ensure](./assets/ruby/else-ensure.png)

### Testing with Rspec

https://www.rubyguides.com/2018/07/rspec-tutorial/

Rspec is a testing framework for Ruby that is used to write automated tests.
It is often used for Test Driven Development but can be used for other tests as well.
Rspec is a **collection** of Ruby gems. It provides libraries for tests (rspec-core), test assertions (rspec-expectations), and testing mocks (rspec-mocks).

Installation (can be used in any directory once installed, or added as a dependency in a bundle):
`gem install rspec`
`bundle add rspec`

##### rspec-core

Rspec core provides the structure for writing tests, controlling which tests are run and the format of results output. Uses the words `describe` and `it` to express tests like a conversation.

``` Ruby
describe `maths methods` do #what should this method do?
    it `should be able to add` do # TEST 1 - it should do this
    end
    it `should be able to subtract` do # TEST 2 - it should also do this
    end
end
```

##### rspec-expectations

Used to assert expected test results.
Built-in matchers:
- Identity - to be, to eq
- Comparisons - to be <, to be >
- Regular Expressions - to match
- Types/Classes - to be_an_instance_of, to be_a_kind_of
- Truthiness - to be_truthy, to be_falsy, to be_nil, to_not be_nil
- Errors - to raise_error

``` Ruby
require_relative "../pet"

describe Pet do
    it "should have a name" do
        pet = Pet.new("Poto")
        expect(pet.name).to eq "Poto"
        expect(pet.name).to match /^P/
        expect(pet).to be_instance_of Pet
    end
end
```

##### Test Driven Development Example

Scenario: Write a method called **largest** that will return the largest value in an array of values.

1. Write tests
2. Run tests - watch them fail.
3. Write code and modify until the tests pass.

Step 0:
Create directory called **largest**. Create file called **largest.rb** for the method.
Create file in a **spec** subdirectory called **largest_spec.rb** for the tests.
**Rspec looks for test files in the **spec** directory** (spec = specifications).

- rspec
    - largest
        - spec
            - largest_spec.rb
        - largest.rb

Step 1,2:
Write tests.

``` Ruby
require_relative '../largest'

describe 'largest' do
    it 'it should return the largest number in an array of numbers' do
        expect(largest([1,2])). to be(2)
    end
    it 'it should return the largest number when it is second in the array' do
        expect(largest([0,1])). to be(1)
    end
    it 'it should return the largest string' do 
        expect(largest(["a","ab"])). to eq("ab")
    end
end
```

**Note** - #to eq tests the value. "ab" would not **be** "ab" as they are different objects.

Step 3:
``` Ruby
def largest(array)
    array.max
end
```

##### Rspec Arguments

`rspec -f d` can change the formatting to provide **documentation**, describing the errors in more detail for easier evaluation.

`rspec -help` shows all the options available to the user.