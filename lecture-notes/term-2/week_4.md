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

https://flavioscopes.com/sample-app-ideas

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

