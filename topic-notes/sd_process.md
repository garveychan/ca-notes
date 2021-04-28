# Software Development Process

### Resources


### Background

Software Development involves many different steps and people so it requires a well-planned and well-defined process.

The process includes developers, product owners, clients, quality assurance, customer support, operations, and marketing teams.

A process is needed because the development life cycle could extend for years with potential employee churn throughout this period.

### High Level Process

At a high level, the process should have the following steps:

1. Requirements
2. Design
3. Implementation
4. Verification
5. Release
6. Maintenance
7. Repeat

##### Requirements

- Determined by stakeholders, including **clients** and **product owners**.

- Define the **Minimum Viable Product** (MVP) and additional desired features.

- Revisited in each cycle.

##### Design

- Usually led by senior developers, with review by stakeholders, operations and technical team.

- Answers questions about:
    - Performance
    - Reliability
    - Security
    - Serviceability

- Output of design step can include pseudocode, logic diagrams, ERDs, data flow diagrams, wireframes and prototypes.

##### Implementation

- Code is written by development team, who work closely with product owners, testers (QA), and operations.

- Task management is crucial to stay on schedule.

- Implementation includes:
    - Writing main code
    - Writing tests
    - Writing documentation
    - Writing code to enable operations to deploy and maintain the operation

##### Verification

- In addition to testing performed during implementation, stakeholders must **verify** that their **requirements** have been met. If not, repeat implementation step.

##### Release

- Mostly involves operations, marketing and customer support.

- Can also involve third parties, like cloud computing services if deployed environments are not owned and managed by the company.

- Developers are **responsible** for addressing deployment issues when code doesn't perform as expected in deployed environment.

##### Maintenance

- Process doesn't end when application is released - it has to be maintained (the world is always changing).

- No application is bug free, the customer will find issues and they need to be fixed and addressed in a timely manner.

- Features not released in initial application can be released in later updates.

- Bug fixes and new features must not break functionality.

### Tools

##### Project Management

- Trello
- Jira
- GitHub Project

##### Code Development

Source code repositories:
- GitHub
- Bitbucket
- Gitlab
- Perforce

Text editors:
- VS Code
- Visual Studio
- Vim
- Eclipse
- Intellij

##### Testing

Unit testing (language dependent):
- Mocha (JS)
- Jest (JS)
- Rspec (Ruby/Rails)

Integration testing (cross-platform/language)
- Cypress
- Selenium

##### Collaboration/Documentation

Collaboration:
- Slack
- Zoom
- Google Hangouts

Documentation:
- GitHub README.md
- Wikis
- Google Drive
- Confluence
- Internal company website

##### Release and Maintenance

Issue tracking:
- Jira
- GitHub
- Trello

Deployment:
- AWS
- Netlify
- Heroku

Continuous Integration / Continuous Deployment:
- Octopus Deploy
- CircleCI
- Travis

### Methods

##### Waterfall

Waterfall software development was the main process used in the past.
It involves outlining all requirements, designs, schedules and expected end products, with clients and developers agreeing firmly on every aspect before development begins.

Pros:

- As a developer, you know exactly what the goal looks like - designs are completed and expected results are defined.
- As a project manager, you have a clear idea of the timing of the project and all expectations because everything is completely documented.

Cons:

- It takes longer to produce a minimum viable product because there's so much documentation required.
- When problems inevitably occur, there is little room to recover which often leads to delivering late.
- Clients never know what they really want, so even though they've agreed on what they thought they wanted, the end result could be a far cry from their expectations.

##### Agile

An iterative approach to development, where work is broken down into **user stories** (user A does action B to get result C) which are released to the client as **soon** as they're complete.

Pros:
- Implementation can begin as soon as basic requirements are understood.
- Less formal documentation.
- More likely to produce what the client wants.

Cons:
- Harder to manage, can feel chaotic.
- Gives client opportunity to change their mind, resulting in unplanned rework, as well as exploding scope and cost.

### Agile Project Management

Agile project management is an **iterative** approach to managing software development.
It aims to ensure that the developers build what the client wants, with optimal workload for all developers with the highest efficiency.

##### Agile Manifesto

Individuals and Interactions > Processes and Tools
Working Software > Comprehensive Documentation
Customer Collaboration > Contract Negotiation
Responding to Change > Following a Plan

##### Agile Key Principles

- Short Development Cycles
    - Deliver working software frequently, from weeks to months, with a preference for the shorter time scale.

- Embracing Change
    - Welcome changes to requirements, even late in development. Agile harnesses change for customer's competitiveness.

- Active participation of stakeholders
    - Business and developers must collaborate daily.

- Reflection
    - Team reflects regularly on how they can be more effective, adjusting their behaviour accordingly.

##### Agile Implementation

- Planning
    - User stories with estimates, agreement from clients/stakeholders
- Tracking
    - Trello / Jira board
- Collaborating
    - Standups / Client meetings
- Iterating
    - Incorporating client feedback and lessons learned
- Deploying
    - Frequent releases of working product to the client
- Retrospective
    - Take a look back before moving forward again

#### Agile Methodologies

##### Scrum

- **Fixed Cycle** lengths with well-defined meetings for planning, working and reflection.

- Common terminology:
    - Scrum - the methodology or team participating in scrum.
    - Iteration - one release of the product.
    - Sprint - one development cycle in scrum. Multiple sprints per iteration.
    - Stakeholders - people interested in the outcome of the project i.e. client and product owners.
    - Backlog - wish list of work and **technical debt** (existing code that needs refactoring), not planned for the next iteration.

##### Kanban

- **Continuous** releases with **work in progress limits** and less rigid meeting structure.

#### Agile User Stories

- User stories are the **smallest unit** of work, express from the **user perspective**.
- As a [person], I [want to], [so that].
- Implementation independent - focus on the **who and what**, not the how.
- Clearly defined user stories make development easier.
    - Easier to make time estimates and prioritise.
- Defined as **done** when the user can perform the task and get the expected result.

Example:
Two-sided marketplace for buying and selling videogames.
- As a game seller, I want to be able to update sale prices of the games I'm selling so I can respond to buyer demand.
- As a game buyer, I want to sort games for sale by their condition so that I can view games with the best condition first.

#### Stakeholder Agreement

- Make sure every stakeholder is on the same page.
- Have a planning meeting to discuss user stories and priorities.
- Make adjustments based on feedback.
- End meeting when everyone is in agreement.

#### Trello for Project Management

- Define work streams in lists
    - Backlog (unplanned work)
    - To Do (planned work)
    - In Progress
    - Review/Testing
    - Complete
- Can be flexible based on team style and requirements
- Will be different for scrum vs kanban

![Trello Process](./assets/sd-process/trello-process.png)

#### Retrospective

It's important to look at what was accomplished after each release to the client.
Scrums will have wrap-up meetings at the end of each **iteration**.
Kanban teams will meet after an agreed amount of **user stories** released to the client.

Meetings will involve:
- discussing what worked and what didn't.
- agree on ways to improve the **process** going forward, **not product**.