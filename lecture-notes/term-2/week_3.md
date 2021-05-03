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

<hr>

## Wednesday 05/04/21
