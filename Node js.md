# **Node.js Documentation**

<img src="images.png" width="100%">

## Table of Contents

- Introduction 

- Installation 

- Creating a simple Application 

- Core Modules

- Modules and Dependencies
- Error Handling
- Asynchronous Programming
- Debugging
- Testing
- Building a REST API
- Express Framework
- Database Integration

- Package Management
- Security
- Deployment
## Introduction 
Node.js is an open-source, cross-platform JavaScript runtime environment that executes JavaScript code outside of a web browser. It is designed to build scalable network applications and allows developers to use JavaScript to write server-side scripts.

### Features
- **Asynchronous and Event-Driven:**
 All APIs of Node.js are asynchronous, non-blocking, and designed to optimize throughput and scalability.

- **Single-Threaded but Highly Scalable:**
Uses a single-threaded model with event looping.

- **Fast:**
Built on Google Chrome's V8 JavaScript Engine.

- **No Buffering:**
Applications output data in chunks, making them very efficient.

## Installation
### Linux

For Debian-based distributions (e.g., Ubuntu):

```jsx
sudo apt update
sudo apt install nodejs npm
```
For other distributions, refer to the Node.js installation guide.

### Creating a Simple Application
- Create a new directory for your project:
```jsx
mkdir my-node-app
cd my-node-app
```
- Initialize a new Node.js project:
```jsx
npm init -y
```
- Create a server.js file with the following content:
```jsx
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```
- Run the server
```jsx
node server.js
```
- Open a browser and navigate to http://127.0.0.1:3000/ to see the "Hello World" message.

## Core Modules
- ### HTTP
The http module is used to create an HTTP server and client.

Example:
```jsx
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello World\n');
});

server.listen(3000, '127.0.0.1', () => {
  console.log('Server running at http://127.0.0.1:3000/');
});
```
- ### File System 
The fs module provides an API for interacting with the file system.

Example:
```jsx
const fs = require('fs');

// Read file
fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});

// Write file
fs.writeFile('example.txt', 'Hello World', (err) => {
  if (err) throw err;
  console.log('File written successfully');
});
```
- ### Path 
The path module provides utilities for working with file and directory paths.

Example:
```jsx
const path = require('path');

console.log(path.basename('/foo/bar/baz/asdf/quux.html')); // quux.html
console.log(path.dirname('/foo/bar/baz/asdf/quux.html'));  // /foo/bar/baz/asdf
console.log(path.extname('/foo/bar/baz/asdf/quux.html'));  // .html
```
- ### Event
The events module provides the EventEmitter class, which is key to working with events in Node.js.

Example:
```jsx
const EventEmitter = require('events');
const eventEmitter = new EventEmitter();

eventEmitter.on('event', () => {
  console.log('An event occurred!');
});

eventEmitter.emit('event');
```
- ### Stream

Streams are objects that let you read data from a source or write data to a destination in a continuous fashion.

Example:
```jsx
const fs = require('fs');
const readStream = fs.createReadStream('example.txt');
const writeStream = fs.createWriteStream('example_copy.txt');

readStream.pipe(writeStream);
```
 ## Package Management 
 ### NPM
 NPM (Node Package Manager) is the default package manager for Node.js.
 - Install a package:
 ```jsx
 npm install package-name
```
- Install a package globally:
```jsx
npm install -g package-name
```
- List installed packages:
```jsx
npm list
```
### Yarn
Yarn is an alternative package manager for Node.js.
- Install a package:
```jsx
yarn add package-name
```
- Install a package globally:
```jsx
yarn global add package-name
```
- List installed packages:
```jsx
yarn list
```
## Modules and Dependencies
Modules are a fundamental part of Node.js applications. A module is a JavaScript file that can be reused throughout the Node.js application.

Example:
```jsx
// circle.js
const PI = Math.PI;

exports.area = (r) => PI * r * r;
exports.circumference = (r) => 2 * PI * r;

// app.js
const circle = require('./circle.js');
console.log(`The area of a circle of radius 4 is ${circle.area(4)}`);
```
## Error Handing 
Proper error handling is crucial in Node.js applications.

Example:
```jsx
try {
  // Code that may throw an error
} catch (error) {
  console.error(error);
}
```
Handling asynchronous errors:
```jsx
fs.readFile('file.txt', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```
Handing asynchronous errors:
```jsx
fs.readFile('file.txt', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```
## Asynchronous Programming
Node.js uses non-blocking I/O and asynchronous programming.

### Callbacks
Example:

```jsx
const fs = require('fs').promises;

fs.readFile('example.txt', 'utf8')
  .then(data => console.log(data))
  .catch(err => console.error(err));
```
## Async/Await
Example:

```jsx
const fs = require('fs').promises;

async function readFile() {
  try {
    const data = await fs.readFile('example.txt', 'utf8');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}

readFile();
```
## Debugging 
Node.js provides several ways to debug applications.

### Console

Using console.log() to print debugging information.

## Node Inspector
Use the built-in debugger

```jsx
node inspect server.js
```
Or use --inspect flag to connect to Chrome DevTools:

```jsx
node --inspect server.js
```
## Testing
Testing is essential for ensuring the reliability of applications.

### Mocha
Mocha is a popular testing framework for Node.js.
- Install Mocha:
```jsx
npm install --save-dev mocha
```
- Create a test file (test.js):

```jsx
const assert = require('assert');

describe('Array', () => {
  describe('#indexOf()', () => {
    it('should return -1 when the value is not present', () => {
      assert.strictEqual([1, 2, 3].indexOf(4), -1);
    });
  });
});
```
- Run the test:
```jsx
npx mocha
```
## Building a REST API
### Using HTTP Module
Example;
```jsx
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.method === 'GET' && req.url === '/api') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ message: 'Hello World' }));
  }
});

server.listen(3000, () => {
  console.log('Server running on port 3000');
});
```
## Express Framework 
Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.

### Installation 
```jsx
npm install express
```
### Basic Example
Example;
```jsx
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`);
});
```
## MySQL
MySQL is a popular relational database.
- Install MySQL driver;
```jsx
npm install mysql
```
- Example
```jsx
const mysql = require('mysql');

const connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: 'password',
  database: 'test'
});

connection.connect();

connection.query('SELECT 1 + 1 AS solution', (error, results, fields) => {
  if (error) throw error;
  console.log('The solution is: ', results[0].solution);
});

connection.end();
```
## Security 
### Best Practice 
- Use Helmet: Helps secure your Express apps by setting various HTTP headers.
```jsx
npm install helmet
```
```jsx
const helmet = require('helmet');
app.use(helmet());
```
- Input Validation: Use libraries like Joi to validate user input.

- Avoid Eval: Never use eval() or similar functions.

- Environment Variables: Use environment variables to store sensitive information like API keys.

## Deployement 
### Using PM2
PM2 is a production process manager for Node.js applications.

- Install PM2:
```jsx
npm install pm2 -g
```
- Start your application with PM2:
```jsx
pm2 start server.js
```
- List all running applications:
```jsx
pm2 list
```
- Monitor logs:
```jsx
pm2 logs
```
 ### Using Docker 
 Docker is a platform for developing, shipping, and running applications in containers.
 - Create a 'Dokerfile':
 ```jsx
 FROM node:14
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 8080
CMD ["node", "server.js"]
```
Build and run the Docker image
```jsx
docker build -t my-node-app .
docker run -p 8080:8080 my-node-app
```
## Conclusion
Node.js is a powerful tool for building scalable and efficient network applications. Its non-blocking, event-driven architecture allows developers to create high-performance applications using JavaScript. With the help of various modules and frameworks like Express, MongoDB, and MySQL, building robust and secure applications becomes more manageable. By following best practices in error handling, asynchronous programming, and security, you can ensure your Node.js applications are reliable and safe.