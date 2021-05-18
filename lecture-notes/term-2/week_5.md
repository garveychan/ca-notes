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
