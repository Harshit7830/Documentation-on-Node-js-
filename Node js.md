# **Node.js Documentation**

<img src="images.png" width="100%">

## Table of Contents

- What is nodeJs ?

- Installation 
-Simple program 

- OS Modules

  
- Error Handling
- File System


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

  -Run the command to install Express:
  ```jsx
  npm install express --save
   ```
## OS Modules
- Frist we have to import
  ```jsx
  const os = require('node:os');
  ```
-then you can use os function 
```jsx

const os = require('node:os');

console.log(os.freemem())

```
Returns the amount of free system memory in bytes as an integer.

-os.homedir()
```jsx
const os = require('node:os');

console.log(os.homedir())
```
Returns the string path of the current user's home directory.

- os.platform()
  ```jsx
   const os = require('node:os');

   console.log(os.platform())
   ```

Returns a string identifying the operating system platform for which the Node.js binary was compiled. The value is set at compile time. Possible values are 'aix', 'darwin', 'freebsd','linux', 'openbsd', 'sunos', and 'win32'.

-os.release()
 ```jsx
const os = require('node:os');

   console.log(os.release())
```
Returns the operating system as a string.
-os.uptime()
```jsx
const os = require('node:os');

   console.log(os.uptime())
```
Returns the system uptime in number of seconds.

## Error Handling
-Proper error handling is crucial in Node.js applications.

-Example:
```jsx
try {
  // Code that may throw an error
} catch (error) {
  console.error(error);
}
```
-Handling asynchronous errors:
```jsx
fs.readFile('file.txt', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```
## File System
- The fs module provides an API for interacting with the file system.

```jsx
const fs = require('fs');
fs.readFile('example.txt', 'utf8', (err, data) => {
  console.log(data);
});
```

