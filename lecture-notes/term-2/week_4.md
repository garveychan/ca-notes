# Week 4 Lecture Notes

## Monday 10/04/21

### Hackathon

1. CRUD app
2. Rails
3. ERB
4. Authentication (Devise)
5. Write Tests (Rspec-Rails)
6. Deploy the app (Heroku)
7. Git Workflow: Collaborate, Work on Branches, Pull Requests, Merging

1. Pair Programming (2)
2. Work on basics of the app together: user stories, ERD, basic wireframe, model generation, routes
3. Get the basics: views, forms, authentication, logic in controllers, model methods, basic styling, deployment, etc.

Examples
1. Notes app
2. Todo app
3. Reminders app
4. Image Uploading app
5. Blog app

https://flavoscopes.com/sample-app-ideas

1. Start 10am Monday
2. Finish 3pm Wednesday
3. Hackathon Presentations ~10mins each
  a. PPT
  b. Demo
4. Educators can answer questions

### Image Upload

Needs to work with AWS

Active Storage - mechanism for storing assets in the cloud (videos, images, etc.)

active_storage_attachments and active_storage_blobs

storage.yml should already be configured out of the box - convention over configuration

has_one_attached - Model characteristic to specify attached asset

image processing can be done with 'image magic', 'mini magic' - check documentation

Active Job - used for queueing jobs

### Git Workflow

Different features - different branches

anything on 'main' should be production-ready

for hackathon - create a github repo, team forks it and creates PRs to merge work

example workflow

1. git checkout -b 'branch-name'
2. do work, commit regularly
3. git push origin 'branch-name' (remote is origin)
4. create a pull request on github
5. share PR url with colleagues
6. get it reviewed
7. merge pull request
8. this code is now on the main branch
9. local machine - git checkout main (switch back to main branch); git pull origin main (fetch latest changes)
10. repeat

## Tuesday 11/04/21

### Image Upload via Amazon

Active Storage Guide - 'Amazon S3 Service'

configre via /config/storage.yml

Rails stores files within the app under /storage

configure config/environments/development.rb - select the desired storage mechanism

upper limit to files in a directory - ~4 billion

rails creates folders and subfolders to store all the images

##### Amazon S3

Amazon S3 buckets allow us to store objects

Buckets must have unique names across AWS

We should select a server geographically similar to the hosting service - in this case North America for Heroku

'Block all public access' is a 'nuclear option' to ensure that everything is completely secured immediately

##### Rails

When the Amazon S3 bucket is set up, we take those settings and put them in our /config/storage.yml file

**The access and secret access keys must be kept secured at ALL times**

##### AWS Security

Identity Access Management (IAM) lets us manage who can access our storage service

We can add the application as a user and enable 'programmatic access' - producing an access and secret access key for us to use

The keys should NOT be stored in plain text in the Rails application

Github scrapers will take these keys and use AWS on our behalf, racking up enormous charges 

Instead, we should use **rails credentials** to encrypt and retrieve our keys

**We must ensure that /config/master.key has been ignored by .gitignore**

### Git Flow

https://git-scm.com/ - good resource for git knowledge

github network graph visualises changes





