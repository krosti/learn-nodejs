---
title: Learn how to develop an API
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: August 14, 2017
sidebar: bootcamps

permalink: bootcamps_getting_started.html
---

## Node Hero - Getting Started With Node.js Tutorial

This is the first post of an upcoming Node.js tutorial series called Node Hero - in these chapters, you can learn how to get started with Node.js and deliver software products using it.

We are going to start with the basics - no prior Node.js knowledge is needed. The goal of this series is to get you started with Node.js and make sure you understand how to write an application using it, so don't hesitate to ask us if anything is unclear!

In this very first tutorial, you will learn what Node.js is, how to install it on your computer and how to get started with it - so in the next ones we can do actual development. Let's get started!

### NodeJS in a nutshell

![alt text](https://nodejs.org/static/images/logos/nodejs-new-pantone-black.png "Logo Title Text 1")


Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient.

In other words: Node.js offers you the possibility to write servers using JavaScript with an incredible performance. As the official statement says: Node.js is a runtime that uses the same V8 Javascript engine you can find in the Google Chrome browser. But that wouldn't be enough for Node.js's success - Node.js utilizes libuv, a multi-platform support library with a focus on asynchronous I/O.

From a developer's point of view Node.js is single-threaded - but under the hood libuv handles threading, file system events, implements the event loop, features thread pooling and so on. In most cases you won't interact with it directly.

### Installing Node.js to get started

To get the latest Node.js binary you can visit the official Node.js website: https://nodejs.org/en/download/.

With this approach it is quite easy to get started - however if later down the road you want to add more Node.js versions, it is better to start using nvm, the Node Version Manager.

Once you install it, you can use a very simple CLI API that you can interact with:

#### Installing Node.js Versions

```nvm install 4.4  ```

Then, if you want to check out the experimental version:

```nvm install 5  ```

To verify that you have Node.js up and running, run this:

```node --version  ```

If everything is ok, it will return the version number of the currently active Node.js binary.

##### Using Node.js Versions

If you are working on a project supporting Node.js v4, you can start using it with the following command:

```nvm use 4  ```

Then you can switch to Node.js v5 with the very same command:

```nvm use 5  ```

Okay, now we know how to install and switch between Node.js versions - but what's the point?

Since the Node.js Foundation was formed, Node.js has a release plan. It's quite similar to the other projects of the Linux Foundation. This means that there are two releases: the stable release and the experimental one. In Node.js the stable versions with long-term support (LTS) are the ones starting with even numbers (4, 6, 8 ...) and the experimental version are the odd numbers (5, 7 ...). We recommend you to use the LTS version in production and try out new things with the experimental one.

If you are on Windows, there is an alternative for nvm: nvm-windows.

### Node.js tutorial: Hello World

To get started with Node.js, let's try it in the terminal! Start Node.js by simply typing node:

```bash
$ node
```

Okay, let's try printing something:

```js
$ node
> console.log('hello from Node.js')
```

Once you hit Enter, you will get something like this:

```js
> console.log('hello from Node.js')

hello from Node.js  
undefined  
```

Feel free to play with Node.js by using this interface - I usually try out small snippets here if I don't want to put them into a file.

It is time to create our Hello Node.js application!

Let’s start with creating a file called index.js. Open up your IDE (Atom, Sublime, Code - you name it), create a new file and save it with the name index.js. If you’re done with that, copy the following snippet into this file:

```js
// index.js

console.log('hello from Node.js')  
```

To run this file, you should open up your terminal again and navigate to the directory in which you placed index.js.

Once you successfully navigated yourself to the right spot, run your file using thenode index.js command. You can see that it will produce the same output as before - printing the string directly into the terminal.

### Modularization of Your Application

Now you have your index.js file, so it is time to level up your game! Let's create something more complex by splitting our source code into multiple JavaScript files with the purpose of readability and maintainability. To get started, head back to your IDE (Atom, Sublime, Code - you name it) and create the following directory structure (with empty files), but leave the package.json out for now, we will generate it automatically in the next step:

```shell
├── app
|   ├── calc.js
|   └── index.js
├── index.js
└── package.json
```

Every Node.js project starts with creating a package.json file - you can think of it as a JSON representation of the application and its' dependencies. It contains your application's name, the author (you), and all the dependencies that is needed to run the application. We are going to cover the dependencies section later in the Using NPM chapter of Node Hero.

You can interactively generate your package.json file using the npm init command in the terminal. After hitting enter you will asked to give several inputs, like the name of your application, version, description and so on. No need to worry, just hit enter until you get the JSON snippet and the question is it ok?. Hit enter one last time and viola, your package.json has been automatically generated and placed in the folder of your application. If you open that file in your IDE, it will look very similar to the code snippet below.


```json
{
  "name": "@risingstack/node-hero",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js"
  },
  "author": "",
  "license": "ISC"
}
```

It's a good practice to add a start script to your package.json - once you do that as shown in the example above you can start your application with the npm start command as well. It comes really handy when you want to deploy your application to a PaaS provider - they can recognize it and start your application using that.

Now let’s head back to the first file you created called index.js. I recommend to keep the this file very thin - only requiring the application itself (the index.js file from the /app subdirectory you created before). Copy the following script into your index.js file and hit save to do this:

```js
// index.js

require('./app/index') 
```
 
Now it is time to start building the actual application. Open the index.js file from the /app folder to create a very simple example: adding an array of numbers. In this case the index.js file will only contain the numbers we want to add, and the logic that does the calculation needs to be placed in a separate module.

Paste this script to the index.js file in your /app directory.

```js
// app/index.js
const calc = require('./calc')

const numbersToAdd = [  
  3,
  4,
  10,
  2
]

const result = calc.sum(numbersToAdd)  

console.log(`The result is: ${result}`)  

```

Now paste the actual business logic into the calc.js file that can be found in the same folder.

```js
// app/calc.js
function sum (arr) {  
  return arr.reduce(function(a, b) { 
    return a + b
  }, 0)
}

module.exports.sum = sum 
```
 
To check if you’d succeeded, save these files, open up terminal and enter npm start or node index.js. If you did everything right, you will get back the answer: 19. If something went wrong, review the console log carefully and find the issue based on that.