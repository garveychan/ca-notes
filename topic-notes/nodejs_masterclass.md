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