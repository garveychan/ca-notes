# Ruby on Rails

### Resources

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

e.g. a Class called **Sales** would, by convention, have a corresponding table in the database called **sales**. It is only if one deviates from this convention, such as the table **product sales**, that one needs to write code regarding these names.

This paradigm requires a greater learning curve as the developer becomes more familiar with the convention. it may also conflict with other programming design principles such as Zen of Python's **explicit over implicit**.

<hr>

### Rails Architecture

![Rails Architecture](./assets/ruby-on-rails/rails_architecture.png)

![Rails Detailed Architecture](./assets/ruby-on-rails/rails_detailed.png)

![Rails MVC](./assets/ruby-on-rails/rails_mvc.png)

#### Directory Structure

![File Structure](./assets/ruby-on-rails/rails_files.png)

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

<hr>

### Controllers Walkthrough

![Controller Diagram](./assets/ruby-on-rails/rails_controller.png)

**Controllers** are the middle-man between the **Views** and **Models** of the application. They control the logic of the application, sending the correct response back to the client based on its interpretation of the input it receives from the **Router**.


##### Creating Controllers

Controllers can be created manually with a controller file, or **generated** using a **rails command**.

e.g. `rails g controller Projects`

- Note: Controllers should be **plural**.

Actions defined in the controller will be activated when called upon by the route.

e.g. The `get "/projects", to: "Projects#index"` route will activate the **index** action within the **Projects Controller** when the `/projects` URL is requested.

##### Render

A controller can directly render elements in multiple formats to the browser using the `render` method.

``` Ruby
  render html: "<h1>Hello World</h1>".html_safe
  render plain: "Hello World"

  projects = [
  {
    id: 1,
    name: 'rails project',
    github_status: false
  },
  {
    id: 2,
    name: 'terminal app',
    github_status: true
  }
]
  render json: projects
```

##### Parameters

`params` refers to **ActionController::Parameters** which is a object containing parameters for a particular request e.g. `<ActionController::Parameters {"controller" => "projects", "action" => "show", "id" => "3"}>`.
This object can be accessed to call upon the specific parameter passed in via the URL.

``` Ruby
# Controller Action <show> - find in projects array, the project whose id matches with the /projects/:id parameter passed in via the URL

  def show
    render json: @projects.find { |project| project[:id] == params[:id].to_i }
  end
```

##### File Reading

In the controller, one can define a method for reading a file containing important information such as an array of data.
For example:

``` Ruby
def read_file
    JSON.parse(File.read(Rails.public_path.join('projects.json')))
end
```

In this example, the `.read` method is being called on the `File` object which interprets the **1** argument it is given - which in this case, is the `projects.json` file sitting in the `/public` folder of the **Rails** app (specified by the official `Rails.public_path` method and appended with the `projects.json` string). Then `JSON.parse` interprets the entire file.

- Note: JSON does not support **symbols**.

##### before_action

`before_action` is a **hook** which can be passed a **symbol** as an argument to call a **method** before any other response is provided by the **controller**.

``` Ruby
  before_action :read_projects
  
  def read_projects
    @projects = JSON.parse(File.read(Rails.public_path.join('projects.json')))
  end
```

In the above code, `read_projects` is being called before any other **action** to set the **instance variable** - `@projects`, giving it the value of the parsed array from the `projects.json` file. This **instance variable** can then be called on in any other method within the controller.

#### Create Action

``` Ruby
  # bad
  get "/projects/create", to: "projects#create"

  # best practice
  get "/projects", to: "projects#index"
  post "/projects", to: "projects#create"
```

When creating a resource, the **route** should be defined with the `post` http verb. This allows the app to use the same URL for several different endpoints, depending on the specified action.

- Note: **Postman** is an app which can be used to mock requests to test an app.

##### Cross Site Request Forgery

Before any action occurs in the **Controller**, Rails will call on a method called `verify_authenticity_token` to ensure that a request is **authentic** in order to prevent malicious actions occurring - particularly with `create` or `delete` requests.

The following code is useful for skipping the verification when testing:
``` Ruby
  # Skip the verification method which Rails calls under the hood before any action.
  skip_before_action :verify_authenticity_token
```

##### Query Strings

`http://localhost:3000/projects?id=3&name=portfolio%20app&github_status=true`

Query strings allow for data to be sent through to a resource without a **HTML form**. The query string above begins after `?` and specifies the information required to create a new 'project'. This information is then available in the `params` object which the **controller** can access to send that data to the database (in this case, 'projects.json').

##### Writing to JSON

``` Ruby
def write_projects(projects)
    File.write(Rails.public_path.join('projects.json'), JSON.generate(projects))
end
```

The above code generates **JSON** from the argument passed into the method and writes it to the specified file. This method can be used as part of the **create** action to store the resource created by the request - as below.

``` Ruby
  def create
    new_project = { "id" => params[:id].to_i, "name" => params[:name], "github_status" => is_true?(params[:github_status]) }
    @projects << new_project
    render plain: "Successfully created project!" if write_projects(@projects)
  end
```

- Tip: converting a string to boolean can be done with the following helper method:

``` Ruby
  def is_true?(bool)
    bool == "true"
  end

  # the string "true" will eval as true, while anything else, including "false" will eval as false.
```

##### redirect_to

The `redirect_to` method is a **controller** method which accepts a **path** as an **argument**, redirecting the client to the specified **route** when called.

``` Ruby
  redirect_to projects_path
```

In the above case, `projects` is the HTTP **Prefix** (which can be found with `rails routes`) and `projects_path` specifies the URL where the client will ultimately be redirected.

##### private

The `private` keyword should be used to ensure that controller-specific methods such as helpers cannot be accessed outside of the controller, e.g.

``` Ruby
  # private methods for this controller only
  private
    def is_true?(bool)
      bool == "true"
    end

    def read_projects
      @projects = JSON.parse(File.read(Rails.public_path.join('projects.json')))
    end
      
    def write_projects(projects)
      File.write(Rails.public_path.join('projects.json'), JSON.generate(projects))
    end
```

<hr>

### Views

Views are rendered using the **corresponding layout** to the controller that Rails can find in app/views/layouts. If it doesn't find the specific layout related to the controller it will use the default - **application.html.erb**. These views use **yield** to fetch the content to be displayed on the webpage.

#### Embedded Ruby Files

In Rails, HTML isn't used directly to code the content in the browser - instead, we use **embedded ruby** files. These files allow us to insert **Ruby code** into our views, which lets us embed **logic** in our HTML files.

##### Syntax

`<% %>` - 'ice cream cone' brackets - used to specify Ruby code within embedded ruby files.

`<%= %>` - string interpolation brackets - like native Ruby's `#{}`.

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

![Rails Server](./assets/ruby-on-rails/rails_server.png)