# Controllers

<hr>

### Controllers Walkthrough

![MVC Diagram](../assets/ruby-on-rails/rails_mvc_ca.png)

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
  : "<h1>Hello World</h1>".html_safe
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
