---
title: Modules
keywords: nodejs
last_updated: August 17, 2017
sidebar: node
permalink: modules.html
---

## Modules

One of the problems with JavaScript in a browser is the global scope. Any variables you create in the global scope are shared between all scripts. They can easily clash. Also, global variables are generally bad news when it comes to making any sort of sensibly architected system.

Node solves all this with a module system.

### A node module

A node module is a simple JavaScript file that saves an object in a variable called `module.exports`

```
// my-file.js
export const myVar = {
  foo: 'bar',
  hello: function () {
    console.log('Hello there!')
  }
};

// in ES5 will be module.export = myVar;
```

And then you can import that file in different files

```
// in ES5 will be var myVar = require('./my-file);
import * as myVar from './my-file';

console.log(myVar.foo); // outputs bar
console.log(myVar.hello()); // outputs Hello there!
```

More advanced `import` and `export` will be discussed later in the `ES6/7` module.