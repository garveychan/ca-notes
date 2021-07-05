# Week 4 Lecture Notes

## Monday 05/07/21

### Misc

Commercial applications will rarely run on one server.
Front-ends will be served by a CDN and back-ends hosted elsewhere.

Alternative for Rails - https://blog.cloud66.com/taking-rails-to-the-next-level-with-hotwire/

`ag` - the silver searcher - brew install the_silver_searcher
https://github.com/ggreer/the_silver_searcher

### SQL

`TRUNCATE` - truncates rows in a table - irreversible.
`DELETE` can be rolled back.

### Monorepo

Monorepo - https://en.wikipedia.org/wiki/Monorepo
"A Monorepo is a software development strategy where code for many projects is stored in the same repository."

- Advantages

    Ease of code reuse – Similar functionality or communication protocols can be abstracted into shared libraries and directly included by projects, without the need of a dependency package manager.

    Simplified dependency management – In a multiple repository environment where multiple projects depend on a third-party dependency, that dependency might be downloaded or built multiple times. In a monorepo the build can be easily optimized, as referenced dependencies all exist in the same codebase.

    Atomic commits – When projects that work together are contained in separate repositories, releases need to sync which versions of one project work with the other. And in large enough projects, managing compatible versions between dependencies can become dependency hell.[8] In a monorepo this problem can be negated, since developers may change multiple projects atomically.[11]

    Large-scale code refactoring – Since developers have access to the entire project, refactors can ensure that every piece of the project continues to function after a refactor.

    Collaboration across teams – In a monorepo that uses source dependencies (dependencies that are compiled from source),[9] teams can improve projects being worked on by other teams. This leads to flexible code ownership.

- Disadvantages

    Loss of version information – Although not required, some monorepo builds use one version number across all projects in the repository. This leads to a loss of per-project semantic versioning.[12]

    Lack of per-project access control – With split repositories, access to a repository can be granted based upon need. A monorepo allows read access to all software in the project, possibly presenting new security issues.[13] Note that there are versioning systems in which this limitation is not an issue. For example, when Subversion is used, it's possible to download any part of the repo (even a single directory), and path-based authorization can be used to restrict access to certain parts of a repository.

    More storage needed by default – With split repositories, you fetch only the project you are interested in by default. With a monorepo, you check out all projects by default. This can take up a significant amount of storage space. While all versioning systems have a mechanism to do a partial checkout,[14][15][16] doing so defeats some of the advantages of a monorepo.

### React

React Router - Client side redirect, captures requests and renders new components as opposed to server side redirect which requests a new response from the back-end.

### Rails API

Initialised using `--api` option.

`--skip-spring`
Spring - application preloader - "speeds up development by keeping your application running in the background so you don't need to boot it every time".

`--skip-test`
Don't install tests - can bring in rspec later.

`rails new murray --skip-spring --skip-test --api --database postgresql`

`rails s -p 3010` - switch port to 3010

##### Cross-Origin Resource Sharing (CORS)

https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any other origins (domain, scheme, or port) than its own from which a browser should permit loading of resources. CORS also relies on a mechanism by which browsers make a “preflight” request to the server hosting the cross-origin resource, in order to check that the server will permit the actual request. In that preflight, the browser sends headers that indicate the HTTP method and headers that will be used in the actual request.

`gem rack-cors` - Ruby gem for handling CORS, making cross-origin AJAX possible

In rails app > initializers > cors.rb - uncomment code and adjust as required
generated with `--api` at rails app initialisation



