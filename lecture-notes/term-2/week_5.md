# Week 5 Lecture Notes

## Monday 17/04/21

### Miscellaneous

`cat .ignore | less` - `less` is a pager for scrolling through content in the terminal.

Important Heroku Commands
- `ps` - controls heroku processes
- `run` - run a one-off command in heroku
- `config` - configure heroku in the cli (can be done via web console)
- `logs` - view heroku logs`

Master key can be added to Heroku via Settings > Config Variables > Environment Variables as RAILS_MASTER_KEY.
This key can be found in config/master.key in the Rails app.

Database convention for tuple names relating to dates/times: `<name>_at`
Examples:
- `created_at`
- `transacted_at`
- `updated_at`

Good naming convention for Git branches:
<first_name>/<branch_name> e.g. garvey/feature

Database amounts should be stored as **integers** as float calculations aren't **precise**.
E.g. $10.00 should be 1000 in the database.

N+1 query problem - unnecessary database requests - Use bullet gem to identify these issues.

Method can be defined in Model to query database based on specific criteria.
E.g. `scope :sellers, -> { joins(:sales) }`
When `User.sellers` is called, a SQL command would query the database, looking for any tuples intersecting both the 'users' table and 'transactions' table via the existing relationship.

## Tuesday 18/04/21

### Miscellaneous

When setting an attribute in a table using a Rails migration, it's good to have a foreign key attribute even if the foreign table doesn't exist.
E.g. seller_id and buyer_id in a transactions table both referring to users.

config>initializers - one-off code run at application start-up e.g. devise, renderers, permissions policies

asynchronous functions - JS scripts to perform tasks in the background while user interacts with application

Chrome JS console - command+option+J

`_path` suffix is for internal rails use.
`_url` suffix in rails returns the URL path - useful for external services - re-entry.

Make sure to set the correct AWS permissions so users have only the authorisation that they need.

Cloudinary - cloud-based image video management service.

vimtutor - terminal practice.

## Wednesday 19/04/21

### Stripe Payments

Stripe creates a session id on their servers which the Rails app can use to request specific responses related to that session.
This is unrelated to any session that Rails has created.

HTML header used for delivering form payload
`'Content-Type': 'application/x-www-form-urlencoded'`

### Miscellaneous

GET requests should always be idempotent i.e. they don't change anything on the server.

Form Helpers - Understanding Parameter Naming Conventions - Rails Guide

e.g. Similarly named parameters should be sent in an array - RESTful URL.

`body: id[]=666&id[]=777`

### Protecting the RESTful endpoints

Rough example of protecting the action in the controller.
This needs to form the basis of authorisation - hiding the button on the view is auxiliary.

```
def edit
	if current_user==recipe.user
		raise "Unauthorised"
	end
end
```

Preferred method of raising unauthorised errors

```
resuce_from RuntimeError, with: 'unauthorised'

def unauthorised
	flash[:alert] = "You're not allowed!"
	redirect_to recipes_path
end
```

Flash is a Rails mechanism for **persisting** information between two requests. 
Common flash names include:
- `notice` - used for important notices (suggested green).
- `alert` - used for information alerts (suggested yellow). 
- `error` - used to highlight issues (suggested red). 
Note that these names are inconsequential. They merely specify the name of the hash passed from one request to another.
However, it's best practice to make them semantic in the interest of code readability.

Controller Actions can only use `render` **once**.
They construct a response based on the logic in the method and either render the similarly named view by default or the render request specified.

### Pundit, Rolify

Authorisation apps let us use declarative language to define authorisation logic in the application.

Pundit is compatible with Devise - using `current_user` as convention.

Rolify - Sets roles which can be enforced with Pundit.

### VIM

'ex' commands begin with `:`.
These allow the user to issue commands to VIM.
