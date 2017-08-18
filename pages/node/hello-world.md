---
title: Hello World
keywords: nodejs
last_updated: August 17, 2017
sidebar: node
permalink: hello-world.html
---

## Hello World

Writing a Node.js program is as simple as creating a new file with a `.js` extension. For example you could create a simple `hello_world.js` file with the following content:

```
console.log('Hello World!');
```

After you have saved the file, you can execute it from your terminal like so:

```
node hello_world.js
```

and the ouput will be

```
Hello World
```

## Hello World on a server

Now printing hello world to a terminal isn't all that exciting. Let's take the next step and write a program that responds to hello world via http. We'll call the file `hello_server.js` and put the following code into it:

```
var http = require('http');

var server = http.createServer(function(req, res) {
  res.writeHead(200);
  res.end('Hello World, I am in the server!');
});

server.listen(8080);
```

Now let's run this program from the terminal by typing:

`node hello_server.js`

Testing the server is as simple as opening a new browser tab, and navigating to the following url: `http://localhost:8080/`. As expected, you should see a response that reads: 

>'Hello World, I am in the server!'.

