# Rails Deployment

### Deploying via Heroku

https://www.heroku.com

https://devcenter.heroku.com/articles/getting-started-with-rails6

##### Asset Pipeline - Production

https://devcenter.heroku.com/articles/rails-asset-pipeline

##### Heroku Console

The Heroku console allows commands to be run for the application in the command line, specifically for the production environment.

`heroku run - <standard commands>`

e.g.

`heroku run rails console`

`heroku run rails db:create`
`heroku run rails db:migrate`
`heroku run rails db:seed`

##### Debugging

Heroku provides a live log of issues to help with debugging.

`heroku logs --tail`