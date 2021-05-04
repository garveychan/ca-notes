# Week 3 Lecture Notes

## Monday 03/04/21

##### Authentication - tips

We should use authentication apps that have been well developed and tested rather than 'rolling' our own.

Devise / Image Uploads - nice to haves for project.

##### Model Relationships

Killing existing rails server

`cat ./tmp/pids/server.pid` - to find server process

`ps -ef | grep 70681` - list processes related to `70681`

`kill -9 70681` - kill process 70681

ps - process numbers left to right - self process / parent process

##### HTML

Selection forms - values are passed back to the server, not the text itself

Form URL encoding - %20 => whitespace

HTML defect in specification - Deselecting all checkboxes will cause client to send *nothing* back to server.
This is an issue if the user wanted to remove all elements belonging to an object in the database.

Rails helps by creating a blank element at the start of the array returned.
recipe_ids = ["", "21", "23]

In this scenario, deselecting everything would send recipe_ids = [""], back to the server, which would drop all records from the table.

Most frameworks have adopted this solution to workaround the HTML defect.

##### Debugging

`raise params.inspect` - raise error and inspect params object to see if we have the correct data inside

##### Rails

Naming conventions very important - works in-line with Rails functionality

- Tip: Console command - `reload!` reloads the console to effect any changes made in the code.

##### Databases

many-to-many relationships - can't have foreign keys in either table because each record might be related to multiple of the other's records.
This can be resolved using a **join** table.

Example -

Patients / Doctors - A patient might have multiple doctors and a doctor might have multiple patients.
In order to link them, we could use an Appointments table, containing foriegn keys patient_id and doctor_id.
Each Appointment record then links a single patient to a single doctor.

Join Table - Rails Naming Convention - **alphabetical order** and **plural** - `IngredientsRecipes`

`self.table_name=` to override database referred to in Rails Model - useful if building a Rails app on top of an existing database where we can't rename the tables.

<hr>

## Tuesday 04/04/21

##### Rails

rule of thumb - .build instantiates / .create instantiates and saves to database.

self-referential association - needed for assignment - can come up in interviews.

polymorphic associations - allow for models to belong to multiple models in a **single** association.

Rails can only do **GET** or **POST**.
This is a deliberate design limitation.
It creates and interprets a **hidden** input type with a **value** of 'patch' rather than a method in order to provide the correct response.

Rails is declarative programming.

**Permitted** parameters only required if **bulk updating** to database.

`.where` vs `.find_by` - `.find_by` method only returns the first record - it instructs psql to **LIMIT** the request.

`render` vs `redirect_to`
- Render tells Rails which view or asset to show a user, without losing access to any variables defined in the controller action.
- Redirect_to tells the browser to request a new URL.

##### Authentication / Authorisation

Authentication - Authenticates the user, makes sure that they are who they say they are.
Authorisation - Once authenticated, what is the user allowed to do.

devise - authentication solution

HTTP is a **stateless** protocol 
- each request is completely independent.
- the server receives a request and delivers a response - then closes the connection.

HTTP as a stateless protocol, allowed the internet to **SCALE**.

```
HTTP stands for HyperText Transfer Protocol, the protocol used to deliver all resources on the World Wide Web. HTTP defines how the messages are formatted and transmitted.

When a client requests some information (say, clicks on a hyperlink), the browser sends a request message to the HTTP server for the requested objects. The server receives the requests and sends the response message with the objects. However, the HTTP server maintains no information about the clients, and if the client asks for the same object again, the server resends the object. Therefore, HTTP is called a stateless protocol.

HTTP can use both nonpersistent connections and persistent connections. A nonpersistent connection is the one that is closed after the server sends the requested object to the client. In other words, the connection is used exactly for one request and one response.

With persistent connections, the server leaves the TCP connection open after sending responses and hence the subsequent requests and responses between the same client and server can be sent. The server closes the connection only when it is not used for a certain configurable amount of time. With persistent connections, the performance is improved by 20%.
 
Nonpersistent connections are the default mode for HTTP/1.0 and persistent connections are the default mode for HTTP/1.1.
```

Cookies are used to store small amounts of information to maintain a session.

These can be seen using Chrome Developer Tools under 'Application > Storage > Cookies'.

Cookies can have an expiration date, if none is set they expire in 30 years.

~/new URL indicates RESTful

<hr>

## Wednesday 05/04/21
