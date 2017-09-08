---
title: Express
keywords: node, express, framework
last_updated: September 5, 2017
sidebar: node
permalink: express.html
---

## Express

Writing a Node.js program is as simple as creating a new file with a `.js` extension. With a couple of lines we have a server running in our local environment. The simplicity is one of the key features of Node.js that made it one of the most used languages nowadays.

But it can get complicated if we are building large applications. You can imagine that building a social network is not an easy thing to do. Building it from the scratch would be tedious and very complicated even for a large team. MySpace is one example of a extremely large application built using Express.

### What is Express?
Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications. It's open sourced and it's first release was back in 2010.
Ok, enough of boring and historical facts. Let's start using it and explaining the main features of it.

## My first app

### Prerequisites

What do we need to start using Express?

1. Well of course you will need **Node.js** installed locally as well as **npm**.
    
And that's it. Now you are ready to start. Let's start creating our first project.

### Setting up the environment
1. First lets create a folder to contain our app.

```
mkdir my-express-app
cd my-express-app
```

2. Now let's create our project

```
npm init
```

You will be prompted with some questions, feel free to answer them with whatever you want.

3. Now let's add **Express** as a dependency in our project.

```
npm install express --save
```

4. Let's create an edit the `index.js` file

```javascript
const express = require('express');
const app = express();

app.get('/', function (req, res) {
  res.send('<h1>My first app</h1><form action="" method="POST"></form>');
})

app.listen(3000, function () {
  console.log('Example app listening on port 3000!');
})
```

Let's analize what we have just wrote.

+ In the first two lines we are importing and creating a new express app.

+ Next, we are defining a GET endpoint and responding with a simple html. As you can see here, we are receiving two parameters: req and res. It's not hard to imagine what those objects represent: the request and the response respectively.
One nice feature Express provides is a default handler for non existing routes. So, if you make a request to an endpoint that does not exist, Express will reply with a **404 Not found**.

+ Finally, we are starting the application on port 3000.

Why don't you try your server now?? Just run `node index.js` and open it on the browser `http://localhost:3000/`

### Excercise #1
Now you can see a simple page loading from your server. That's a start. But what happens if you click on the button that appears there? Oops, we don't have an endpoint for a POST request to `/`.

Why don't you try creating a new endpoint that returns a simple _Hello you!_.

### Routing
Ok, let's dig a little bit deeper on how to create new endpoints in our application. Till now, we have created one route `/` that accepts two methods: _GET_ and _POST_. Let's see what are the options and tools we have to create new endpoints.

To create a new endpoint we use the following template:

```javascript
app.METHOD(PATH, HANDLER)
```

**Method**: it's self explanatory, here you have to choose the HTTP method for the new endpoint. You can use one of the followings:

* all (this is the only one not derived from a HTTP method)
* checkout
* copy
* delete
* get
* head
* lock
* merge
* mkactivity
* mkcol
* move
* m-search
* notify
* options
* patch
* post
* purge
* put
* report
* search
* subscribe
* trace
* unlock
* unsubscribe

**Path**: you can enter a string, a string pattern or a regular expression here. It's the route you will use to make the request. Let's see some examples:

This route path will match abcd, abxcd, abRANDOMcd, ab123cd, and so on.

```javascript
app.get('/ab*cd', function (req, res) {
  res.send('ab*cd')
})
```

This route path will match /abe and /abcde.

```javascript
app.get('/ab(cd)?e', function (req, res) {
  res.send('ab(cd)?e')
})
```

Now one with a Regex. This route path will match anything with an “a” in the route name.

```javascript
app.get(/a/, function (req, res) {
  res.send('/a/')
})
```

`Handler`: is the function executed when the route is matched. You can define multiple handlers for your endpoints. They act as middlewares (explained later on in this document). Each handler receives three parameters: _req_, _res_ and _next_.

`Req` is an object that represents the request. There you can find information such as query parameters, request headers, request body, etc.

`Res` is the response object. You will add all the information you want in the response here. Most important, it provides you a set of methods to send the response back to the caller (res.send, res.json, res.render).

Finally, `next` is a next function you will call if you want to call the next handler of the function. Keep in mind that for a specific request, you can only call res.something once (you cannot call it in every handler).

For a more detailed explanation about routing, you can check the [official documentation](https://expressjs.com/en/guide/routing.html).

### Excercise 2
Ok, time to practice. Try adding another endpoint for all type of request (all methods) pointing to `admin` and reply with a `403 Forbidden` status.

If you feel comfortable with that, why don't you add a first middleware to log in the console that the request was forbidden??

### Middlewares
Nice one!! So you now know how to create any kind of endpoint with its handler. In the previous examples, we have used only one handler per endpoint because the logic wasn't to complex. But let's imagine we have one piece of code that should be executed for all requests to `/admin`. For example, we have to check some headers in the request to check if the request is allowed or not.

```javascript
    // Admin controller
    var adminHandler = function (req, res, next) {
        if (req.headers.indexOf('AuthKey') < 0) {
            return res.status(403).send();
        }
        // do some very important admin stuff
        res.send("You are the real administrator. Welcome back, sir!");
    }
```

This approach is good enough, but it's not very clean to have authorization logic in the middle of admin controller. We can make it even easier to read if we create a function that will first authorize the request and then pass it through to the business logic in the admin controller.

```javascript
    // auth.js
    module.exports.authorizeUser = function (req, res, next) {
        if (!req.get('AuthKey')) {
            return res.status(403).send();
        }
        next();
    }
```

```javascript
    // admin.js
    module.exports.adminHandler = function (req, res, next) {
        // do some very important admin stuff
        res.send("You are the real administrator. Welcome back, sir!");
    }
```

```javascript
    // router.js
    app.post('/admin', auth.authorizeUser, admin.adminHandler);
```

### Static files
Serving static files with express is really easy. We just have to tell Express where are they and that's it. Let's imagine we have all our images in `/public/images/` and we want to provide them all as static files.

```javascript
app.use(express.static('public'));
```

Now all inside the public folder will be served as a static files. For example: `http://localhost:3000/images/main.png`

### Templating

Enough of inline templates as strings. It does not scale and it is extremely difficult to read and understand. Why don't we use simple html files? Or even better, let's use a templating engine to render pages easily.

There are plenty of engines you can use (Pug, Mustache, EJS, etc). Let's use Pug (take a look at the [documentation](https://pugjs.org/api/getting-started.html) if you are not familiarized with it).

```
npm install pug --save
```

Then we have to let the app know what engine we are going to use.

```
app.set('view engine', 'pug')
```

Now, let's create the same page we had, but in a separate file named `views/index.pug` with the following

```html
html
  head
    title= title
  body
    h1= message
    form(method='POST' action='/')
      label My name
      input
      button(type='submit') SEND
```

Finally, in the handler for the GET `/` let's change the logic with:

```javascript
res.render('index', {
  title: 'My app',
  message: 'My first app'
});
```

### Final Excercise

Great, we have finished it! We know the basic of Express, the most popular framework for Node.js out there. As a final exercise, where we can practice all what we have seen, we can create a very simple To-do application.

+ Create a POST endpoint to add new items
+ Create a PUT endpoint to mark as done
+ Create a GET endpoint to get the list of items
+ Try using a template engine of your choice.

As we don't have a database, let's use a simple array of objects as the dataset. Feel free to use the **[Express Generator](https://expressjs.com/en/starter/generator.html)** to scaffold the app if you want to.
