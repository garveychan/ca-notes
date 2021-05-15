# Ruby on Rails

### Resources

##### Top 10 Mistakes in Rails

https://www.toptal.com/ruby-on-rails/top-10-mistakes-that-rails-programmers-make

##### State of Rails in 2021

https://scoutapm.com/blog/state-of-ruby

##### Sensitive Data Handling

https://ankane.org/sensitive-data-rails

##### Guides

https://www.codecademy.com/learn/learn-rails/

https://guides.rubyonrails.org/

https://medium.com/the-renaissance-developer/ruby-on-rails-http-mvc-and-routes-f02215a46a84

https://stackshare.io/rails

### Background

Ruby on Rails is a framework created in 2003 by **David Heinemeier Hansson** while working on **BaseCamp**, a project management tool. He developed tools to automate repetitive tasks while at BaseCamp and these formed the basis of Rails.

Rails was released as open source code in July 2004. It follows three basic principles:

- Based on the **Ruby** Programming Language.
- Model-View-Controller Architecture.
- Programmer Happiness.

Rails helps people build quick flexible **Minimum Viable Products** (MVPs) for market validation. However large tech companies such as Twitter have switched from Rails to other frameworks which are more performant at scale.

#### DRY

Rails follows the coding best practice principle of **Don't Repeat Yourself* (DRY), minimising the amount of repeated code which users will have in their programs.

#### Boilerplate Code

Boilerplate code is a unit of code that can be reused in many places with little to no alteration.
e.g. HTML initial layout template code.

Rails' built-in commands generate **boilerplate** code so programmers don't have to write them every time they want to create a new app or add/update features in their existing apps.

#### Convention over Configuration

Convention over Configuration is a design paradigm in programming which forms the philosophy of Ruby on Rails. It involves attempting to **decrease the number of design decisions** that the developer has to make without necessarily sacrificing flexibility. It is related to other programming concepts such as **sensible defaults** and the **principle of least astonishment** in UI design.

In practice, the developer adapts to the **convention** of the framework as much as possible, only explicitly specifying when they must deviate from the convention, i.e. **configure** the framework.

e.g. a Class called **Sales** would, by convention, have a corresponding table in the database called **sales**. It is only if one deviates from this convention, such as the table **product sales**, that one needs to write further code to refer to these names.

This paradigm requires a greater learning curve as the developer becomes more familiar with the convention. it may also conflict with other programming design principles such as Zen of Python's **explicit over implicit**.

<hr>

### Rails Architecture

![Rails Architecture](../assets/ruby-on-rails/rails_architecture.png)

![Rails Detailed Architecture](../assets/ruby-on-rails/rails_detailed.png)

![Rails MVC](../assets/ruby-on-rails/rails_mvc.png)


#### Response Request Cycle

![Rails Request Response](../assets/ruby-on-rails/rails_app_request_response.jpeg)

![Rails Request Response Code](../assets/ruby-on-rails/rails_request_response_code.png)

#### Directory Structure

![File Structure](../assets/ruby-on-rails/rails_files.png)

#### Routes

Routes are a key part of all websites. Website content is organised into many different URLs (Universal Resource Locators). Each of these URLs and HTTP methods (GET, POST, PUT/PATCH, DELETE) require different routes to point to the correct content.

#### HTTP Requests

HTTP refers to the Hypertext Transfer Protocol which is the predominant protocol that computers use to communicate to each other over the Internet. A protocol can be defined as **a set of rules** for how messages are **formatted, transmitted and responded to**.

Any time a user wants to interact with the website, they have to send a request. If the request is valid, and the user has permission to send that request, then the website should send a response in return.

HTTP uses different **verbs** or **methods** to describe its requests:

|HTTP Verb|Action|
|:-:|:-:|
|GET| Retrieve a resource (Read)|
|POST| Create a resource |
|PUT/PATCH| Update a resource |
|DELETE| Destroy a resource |

These are also known as **CRUD** operations - **Create, Read, Update, Delete**.

##### HTTP Responses

https://developer.mozilla.org/en-US/docs/Web/HTTP/Status

HTTP response status codes indicate whether a specific HTTP request has been successfully completed.

Responses are grouped in five classes:
- Informational responses (100–199)
- Successful responses (200–299)
- Redirects (300–399)
- Client errors (400–499)
- Server errors (500–599)

The most common responses include: 
- `200` - **OK** - Server request succeeded.
- `404` - **Not Found** - The server could not find the requested resource. In the browser, this means the URL is not recognized.
- `500` - **Internal Server Error** - The server encountered a situation it could not handle.

#### Process Flow

1. **Client** sends an **HTTP request**.

When a user types a **URL** in the browser, the URL points to a running Rails **server**, which reads the **path** and looks for a **route**.

2. **Routes** connects **URLs** to **Controller Actions**.

Routes are defined in **config/routes.rb**. These routes **map** the **HTTP verbs and paths** to the app's **Controller Actions**.

3. **Controller** executes action and renders **View**.

The specified **Controller Action** will be activated and interact with the specified **Model**, providing information to the **View** via **instance variables**, as dictated with the HTTP request.

The controller will **render** the **View** with the appropriate information from the **Model** and the rendered content is sent to the client (the browser).

By default, the **View** that is rendered will be in the **Views** directory and should have a **name** that matches the **Controller Action**.

<hr>

### Routes Walkthrough

Routes can be defined in a few ways through **config/routes.rb**:

`HTTP_verb 'path' to: 'controller_name#action_name'`

##### Action Routes and View Conventions

|User Action|Controller Action|Route|View|
|:-:|:-:|:-:|:-:|
|List all orders|orders#index|get 'orders', to: 'orders#index'|views/orders/index.html.erb|
|Show one order|orders#show|get 'orders/:id', to: 'orders#show'|views/orders/show.html.erb|
|New order form|orders#new|get 'orders/new', to: 'orders#new'|views/orders/new.html.erb|

*Note, in the action route 'show one order', the route is passing a **parameter** `:id` to the controller action so it knows which order to show.*

##### Root Route

The root route tells the rails server what to display when the user specifies a URL with no additional path i.e. the **home** or **index** of the application itself.

The root route is specified in the **config/routes.rb** file with the syntax:

root, to: 'controller#action'

##### Route Path

Appending a route with `, as: '<route_name>'` creates a variable which can be accessed in the Rails application which specifies the URL of the route. This is best practice because any changes to URLs will not need to be amended throughout the application.

e.g.
``` Ruby
get '/orders', to: 'orders#index', as: 'orders'

<%= orders_path %> # provides URL
```

<hr>

### Commands

https://guides.rubyonrails.org/command_line.html

Rails commands are prefixed by `rails` - e.g. `rails new <app>`

|Command|Arguments|Description|Example|
|:-:|:-:|:-:|:-:|
| new "appname" | none <br> -d "database type"| create a new rails app <br> create with database | rails new recipes -d postgresql |
| s(erver) | none <br> -p "port" | start a rails app (server) <br> change the port that the server is listening through (multiple apps) | rails s <br> rails s -p 3001 |
| g(enerate) | scaffold <br> controller <br> model <br> view <br> | generate an app component | rails g model Recipe name:string difficulty:integer | rails g controller cafe |
| routes | -c <name> <br> -m <name> <br> -v <name> | show all the app's routes, or the routes pertaining to the model/view/controller identified by its name | rails routes -c recipes |
| db:create | none | create database for the rails app | rails db:create |

#### rails s

`rails s` starts a rails server via **Puma**, the web server that Rails comes pre-configured with.

In essence, a web server allows a local directory within a machine to be accessible by the network (in most cases, the internet). This allows us to server websites and web apps to anywhere in the world.

When using `rails s`, the web server will output `localhost:3000` by default, which refers to the address it is listening on. Any request for that address will instruct our web server to 'serve' the data from our app.

![Rails Server](../assets/ruby-on-rails/rails_server.png)
