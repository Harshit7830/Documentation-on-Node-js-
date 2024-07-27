# **Node.js Documentation**

<img src="images.png" width="100%">

## Table of Contents

- What is nodeJs ?

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
## What is nodeJs?
- Node.Js is a JavaScript runtime built on Chrome’s V8 JavaScript engine.
- Node.Js is designed to build scalable network applications.
- Node.Js can be download from the official Node.js website.
- Node.Js is a free and open-source server environment.
- Node.Js allows us to run JavaScript on the server.
- Node.Js can run on multiple operating systems.

### Why we use nodeJs?
- You can use JavaScript in the entire stack.
- Many famous companies use Node.Js as their backend.
- Node.Js comes with a lot of useful built-in modules.
- Node.Js is fast.

## Installation

### Linux for v22.5.1(current)


```jsx
# installs nvm (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# download and install Node.js (you may need to restart the terminal)
nvm install 22

# verifies the right Node.js version is in the environment
node -v # should print `v22.5.1`

# verifies the right npm version is in the environment
npm -v # should print `10.8.2`
```
For other distributions, refer to the Node.js installation guide.
## installing Vs code
-Download the VS Code .deb package:
```jsx
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
   sudo install -o root -g root -m 644 packages.microsoft.gpg /usr/share/keyrings/
   sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > 
   /etc/apt/sources.list.d/vscode.list'
   rm -f packages.microsoft.gpg
```
-Update the package list:

```jsx
  $ sudo apt update
```
## Vs code install
<img src="" width="100%">


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
- Create a index.js file in my-node-app
  ```jsx
  console.log("Hello world")
  ```
- Open terminal
  ```jsx
  node index
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

