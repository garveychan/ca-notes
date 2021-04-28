# Week 2 Lecture Notes

## Tuesday 27/04/21

ActiveRecord Callbacks
`before_###` - before a method
`after_###` - after a method
`around_###` - around a method, before and after - perfect for performance measurement 

```
    around_save do |user|
        Rails.logger.info "Starting #save: #{user.id}"
        yield
        Rails.logger.info "Finished #save: #{user.id}"
    end
```

`tail -f log/development.log`
keep running log on terminal

darwin - codename for mac - old OS for mac

### Heroku - Deployment

Heroku - AWS based service
deploying on netlify
great for MVPs, expensive once scaled, 0-100 person companies

`heroku logs -t`
show logs for heroku deployment

heroku apps
show all your heroku apps

heroku doesn't automatically migrate your database
databases are companies' value - these are important and any interaction with databases should be carefully considered.

`heroku run rails db:migrate -a rails-recipes-2021`

content delivery networks - edge servers across different geographical locations to speed up delivery of content.

asset pipeline

rails in db directory - seeds.rb
seed data - default values for the database
factory-set data

`rails -T | grep db:`
look for database tasks in rails

`heroku run` - prefix rails commands after deployment

**HTML method must be correct. Massive vulnerability and risk if the wrong verb is used e.g. POST instead of GET.**

<hr>

### CURL - interact with website via command line

`curl -X GET -o /dev/null -v localhost:3000/recipes`

`curl -X POST`
`curl -X DELETE`

`curl -X POST -o /dev/null -v --data "recipe[name]=Toasted%20Bread&recipe[difficulty]=3" localhost:3000/recipes`

`-X <HTTP VERB>` => the http method to be actioned
`-o /dev/null` => write output to null, so console isn't blown up
`-v` => verbose
`--data "recipe[id]=5"` => data to be sent to http method

percent-encoding => encoding of data in URL

`rails routes` => show routes of rails app
`rails routes -c <name>` => show routes for the controller <name>

### CS Fundamentals Review - Bases

Binary generally written in lots of 4 for readability.

Hexadecimal to Binary cheat - divide binary into lots of 4. The totals add up to the hexadecimal digit.

8 4 2 1

1000 1110 base 2 = 8 E base 16

Pattern -> the smaller the base, the larger the number. 
17 base 16 = 23 base 10 = 27 base 8 = 10111 base 2

**Final Exam - 31st May - 2-3 questions on converting between bases, bring calculator**

- Bit Shifting

- `>>` - Bit-shift to the *right*, last numbers dropped off - 10101100 >> 2 => 101011
- `<<` - Bit-shift to the *left*, 0's added to the right to shift number to the **left** - 10101100 << 2 => 1010110000

Bit-shifting Example - 

Steps for shifting from Base 5:
1. Convert Base 5 to Base 10(dec)
2. Convert Base 10(dec) to Base 2(binary)
3. Bit-Shift
4. Convert Base 2(binary) to Base 10(dec)
5. Convert Base 10(dec) to Base 5

Binary Addition/Subtraction
- Check if done correctly by converting back to Base 10. 


## Wednesday 28/04/21

Software guides are critical to professional growth.
Learn how to consume them quickly and effectively.

#### Rails Recipes App

`rails db` - open database console

attempting to implement new constraints in database can cause issues if database has **existing** values which fail these constraints

`rails c`
`Recipes.delete_all`
(Remove all existing data)

**always check database before migrating**

`git diff --cached` (check difference of committed files)

Migrations appear to be the 'changes' to the database
Actions/methods described in the ruby script alter the database once `rails db:migrate` is run

`rails db:migrate:status` - check status of migrations
`rails db:migrate:down VERSION = #####` - migrate up/down a version based on number from status command

**implement two-step validation of data**
e.g.
database - `change_column_null(:recipes, :name, false)` -  not nullable characteristic - *can var be null? - false => not nullable*
model - `validates: :first_name, :presence: true`

**Request Response Cycle**

Form submission - creating a user

1. User is instantiated in memory - User Model initialize method performed
2. User is saved
3. Client is redirected

**Interview - attention to detail - HTML**
apostrophes should use the correct character
labels should use `for` attribute so that the focus shifts to the right element on page when clicked
this is for accessibility reasons
e.g. `<label for="recipe_user_id">User<label>`

Dependent associations allows the app to delete related elements from the database.
e.g. you can specify in a User model's options that its `:dependent` is `:destroy`ed i.e. all its dependent variables get destroyed along with the user.