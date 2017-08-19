---
title: Exercises #1
keywords: nodejs
last_updated: August 17, 2017
sidebar: node
permalink: exercises-1.html
---

## Exercises

Based on what you learned until now, we have a list of exercises to keep the knowledge fresh. 

### 1. Node Console

* Open the REPL and do the following operation `10 + 10`.
* Show a message in the screen to output `Hello world!`.
* Show the path where you running node.
* After five seconds, show a new message in the screen with the text `5 seconds later...`.

### 2. Simple program

Create a new file called `my-program.js` and:

* Create a new server running in the port 8080 that returns random quotes stored locally.
* Log a message when the server is up with the text `Server is running in http://localhost:8080`.

### 3. Add dependencies

Using the file from the item 2, install the following dependencies

* Install `chalk` as dependency.
* Install `jshint` as developer dependency.
* Use `chalk` within console in the item 2 from exercise 2 to show a message in green color.
* Add a new task with name `linter` to verify the code by running `jshint **.js`.
* Add the `start` task to run `my-program.js`.