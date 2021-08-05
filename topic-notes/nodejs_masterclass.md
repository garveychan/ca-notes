# NodeJS Masterclass Notes

## Masterclass Outline

- Node.js - Platform for server-side Javascript.
- Express - Framework for Node.js to write web and API apps.
- MongoDB - Document-oriented NoSQL data store (JSON).
- Mongoose - NPM package to connect to a MongoDB data store.

## Node.js

### Resources

##### Documentation

https://nodejs.org/en/
https://nodejs.org/en/docs/guides/
https://nodejs.org/api/index.html

##### Guides

https://nodejs.dev
https://www.codecademy.com/learn/learn-node-js

##### Packages

https://www.npmjs.com

### Background

#### History

- Node.js is a server-side Javascript platform first released in 2009 by Ryan Dahl.
- It was developed in response to slow web servers that locked for any I/O task e.g. reading/writing files, accessing networks, CRUD operations.
- The solution that Node.js provided was a **pool of processes**, which rendered all I/O tasks asynchronous and allowed thousands of requests to be processed concurrently, resulting in higher performance with less memory usage.
- This was enabled by Google's V8 Javascript Engine which has been unbundled from the Chrome browser.

#### Packages

- Node.js has a rich module ecosystem accessed via Node Package Manager (npm). This ecosystem is one of the largest of any package system.
- A small collection of modules have been built-in (fs, http, events etc) to encourage a rich ecosystem of third-party modules.

#### Use Cases

- HTTP APIs via the HTTP module, **Express** framework.
- Distributed systems via the TCP module.
- Command-line tools.
- Cross-platform desktop applications via **Electron**, e.g. Slack, VSCode, Discord, Figma.

### Installation

- Recommended to install via Node Version Manager (nvm), in case multiple versions are required.
- Long term support (LTS) version recommended. Odd number versions - experimental. Even number versions - LTS.

### Read/Eval/Print/Loop

"REPL also known as Read Evaluate Print Loop is a programming language environment (basically a console window) that takes single expression as user input and returns the result back to the console after execution."

`node` in terminal to open.
`.exit` to close.
`.help` to list helpful commands.

### Node.js Server Example

```JavaScript
// hello-world.js

const http = require('http');
const port = process.env.PORT || 1337;

const server = http.createServer(function (req, res) {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'application/json');
  res.end(JSON.stringify({ message: 'Hi!'}));
});

server.listen(port, function () {
  console.log(`Server listening on port ${port}`);
});
```

Run with `node ./hello-world.js`.

### Asynchrony

- Node.js was built in response to slow web servers with blocking I/O operations.
- The V8 engine and **libuv** library enable single-threaded, non-blocking tasks.
- Slow I/O tasks are offloaded to the operating system, and a signal is received when ready. Other work is performed in the meantime.
- Asynchronous mechanisms - callbacks, promises, async/await.
- We cannot make assumptions about the order in which the callbacks will be executed.

```JavaScript
// async.js

const fs = require('fs').promises;

printLengths('./');

async function printLengths(dir) {
  const fileList = await fs.readdir(dir);
  const results = await Promise.all(
    fileList.map(async file => {
      try {
        const data = await fs.readFile(file);
        return [file, data.length];
      } catch {
        return [file, 0];
      }
    })
  )

  results.forEach(([file, length]) => console.log(`${file}: ${length}`));
  console.log('done!');
}
```

**Notes**

- Promises will be handled by the Callback Queue and Event Loop while the rest of the code executes.
- In the above example, if `await` was not used, the following methods would be executed and errors would be thrown because `results` would be undefined while the Promise is **pending**.
- By nesting `await` calls in `Promise.all`, each individual `readFile` method only begins when the previous is complete, allowing the `results` array to be generated in the same order as `fileList`. Only when this is all complete, will the `results` elements be printed as output.

## Express

### Resources

##### Documentation

https://expressjs.com

### Background

#### Characteristics

- "Fast, unopinionated, minimalist web framework for Node.js"
- Used widely in production environments.
- Simplifies many issues including - http, routing, params, modules.
- Flexible architecture but can be supplemented with NPM packages to implement Model View Controller (MVC).

### Recipes API with vanilla Node.js

```JavaScript
const http = require('http');
const querystring = require('querystring');

const { recipes } = require('./db.js');

const port = process.env.PORT || 1337 ;

const server = http.createServer(function (req, res) {
  if (req.headers['content-type'] !== 'application/json') return respondUnsupportedMediaType(req, res);

  const match = req.url.match(/\/recipes\/(?<id>\d+)$/);

  if (match && req.method === 'GET') return respondShow(req, res, match.groups.id);
  if (req.url.match(/\/recipes/) && req.method === 'GET') return respondIndex(req, res);

  respondNotFound(req, res);
});

// /recipes
function respondIndex(req, res) {
  const qs = req.url.split('?').slice(1).join('');
  let { page = 1, perpage = 10 } = querystring.parse(qs);

  page = Number(page), perpage = Number(perpage);
  const startIdx = (page - 1) * perpage, endIdx = (startIdx + perpage);
  const pagedRecipes = recipes.slice(startIdx, endIdx);

  res.statusCode = 200;
  res.setHeader('Content-Type', 'application/json');
  res.end(JSON.stringify(pagedRecipes));
}

// /recipes/:id
function respondShow(req, res, id) {
  const recipe = recipes.find(r => r.id == id);
  if (!recipe) return respondNotFound(req, res);

  res.statusCode = 200;
  res.setHeader('Content-Type', 'application/json');
  res.end(JSON.stringify(recipe));
}

function respondNotFound(req, res) {
  res.writeHead(404, { 'Content-Type': 'text/plain' })
  res.end('Not found')
}

function respondUnsupportedMediaType(req, res) {
  res.writeHead(415, { 'Content-Type': 'text/plain' })
  res.end('Not JSON')
}

server.listen(port, function () {
  console.log(`Server listening on port ${port}`);
});
```

**Notes**

`npx nodemon <api>.js` - `npx` executes the node package `nodemon` which monitors if there have been any changes to the underlying files in the directory and restarts the `node` service if necessary.

### Recipes API with Express

```JavaScript
// index.js
const express = require('express');
const { recipes } = require('./db');
const recipesRouter = require('./routes/recipes');

const port = process.env.PORT || 1337;
const app = express();

app.use(express.json());
app.use('/recipes', recipesRouter);


app.listen(port, () => console.log('Recipes listening on port ' + port));

// routes/recipes.js
const express = require('express');
const router = express.Router();
const { recipes } = require('../db');

const authorize = (req, res, next) => {
  if (req.headers['authorization'] === 'Bearer 666') {
    next();
  } else {
    res.status(401).end();
  }
  next();
}

router.use(authorize)

router.get('/:id',
  (req, res) => {
    const recipe = recipes.find(r => r.id == req.params.id);
    res.json(recipe);
  }
);

router.put('/:id', (req, res) => {
  const recipe = recipes.find(r => r.id == req.params.id);
  Object.assign(recipe, req.body);
  res.status(204).json(recipe);
});

router.get('/', (req, res) => res.json(recipes))

router.post('/', (req, res) => {
  const recipe = req.body;
  recipe.id = recipes.length + 1;
  recipes.push(recipe);
  res.status(201).json(recipe);
});

module.exports = router;
```

**Notes**

`npm init` - used to initialise the project.
`npm i --save-dev nodemon` - added as a dev dependency.

```
  "scripts": {
    "dev": "nodemon index.js",
    "start": "node index.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

## MongoDB

### Resources

##### Documentation

https://docs.mongodb.com/manual/

##### Guides

https://docs.mongodb.com/manual/crud

### Background

- Free open-source cross-platform document-oriented database.
- NoSQL - Doesn't use SQL, not a relational database - no tables and joins.
- MongoDB engine lets us write JS to perform CRUD operations with JSON.
- Facilitates rapid early development, but it can be mismanaged if not properly understood.

### Characteristics

- Document Model - Collections of 'items'.
- Collections are the non-relational equivalents of Tables.

### Command Line Interface

`mongod` - Daemon to run the database service.
`mongosh` - MongoDB REPL.

**Hint**

`control+z` to suspend service and return to shell.
`fg` to resume job.

**Useful commands (examples)**

- `help`
- `show dbs`
- `use recipes`
- `show collections`
- `db.createCollection('recipes')`
- `db.help()`
- `db.recipes.find({ ... })`
- `db.collection.insertOne/insertMany({ ... })`

### Installation

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/

Recommended to install via homebrew by following the instructions in the link above.

##### Drivers

https://docs.mongodb.com/drivers/node/

Allows Node.js applications to connect to MongoDB and work with data.

## Mongoose

### Resources

##### Documentation

https://mongoosejs.com/

##### Guides

https://mongoosejs.com/docs/guide.html
https://mongoosejs.com/docs/models.html
https://mongoosejs.com/docs/queries.html
https://mongoosejs.com/docs/validation.html
https://mongoosejs.com/docs/populate.html

##### Repository

https://github.com/Automattic/mongoose

### Background

- MongoDB driver for Node.js is quite low level with basic features.
- Mongoose is a JS library that wraps the MongoDB driver and provides additional features such as Schemas and Models.
- It mimics the actions we place on our models and mirrors them in the database.
- Similar abstractions and functionality as ActiveRecord from Rails.

### Creating Models

- Models provide schema definitions for a schema-less document database.
- Each Model will represent a MongoDB collection.

**Schema Example**

```JavaScript
const RecipeSchema = new Schema({
  title: String,
  created_at { type: Date, default: Date.now }
})
```

**Compiling the Schema into a Model**

```JavaScript
const Recipe = mongoose.model('Recipe', RecipeSchema);
module.exports = Recipe;
```

