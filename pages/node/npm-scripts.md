---
title: NPM Scripts
keywords: nodejs
last_updated: August 17, 2017
sidebar: node
permalink: npm-scripts.html
---

## NPM Scripts

A task is something you need to do. If you want to perform that task over and over again, as you do in development, you'll save yourself a lot of time if you automate the process. Common web development tasks include running test suites, compiling Sass, TypeScript and CoffeeScript files, starting a web server or a worker process that goes through a queue of jobs like sending out emails or push notifications.

### Built-in Tasks

There are a number of built-in tasks that npm can run for you. The most common is `test` and `start`. Some tasks are already inside NPM so by running `npm test` it should works. But if you created a new custom task named `my-awesome-task` if you run this like `npm my-awesome-task` it won't work. For those tasks you'll need to run it in this way `npm run my-awesome-task` and that's it.

NPM supports pre and post tasks natively, for example everytime you run `npm test`, the tasks `pretest` and `posttest` are also ran. 

#### Internal tasks

NPM already support the most common tasks like `test` and `start` plus a lot of more tasks listed below:

Task | Description
-----|------------
`prepublish` | Run BEFORE the package is packed and published, as well as on local npm install without any arguments. (See below)
`prepare` | Run both BEFORE the package is packed and published, and on local npm install without any arguments (See below). This is run AFTER prepublish, but BEFORE prepublishOnly.
`prepublishOnly` | Run BEFORE the package is prepared and packed, ONLY on npm publish. (See below.)
`prepack` | run BEFORE a tarball is packed (on npm pack, npm publish, and when installing git dependencies)
`postpack` | Run AFTER the tarball has been generated and moved to its final destination.
`publish`, `postpublish` | Run AFTER the package is published.
`preinstall` | Run BEFORE the package is installed
`install`, `postinstall` | Run AFTER the package is installed.
`preuninstall`, `uninstall` | Run BEFORE the package is uninstalled.
`postuninstall` | Run AFTER the package is uninstalled.
`preversion` | Run BEFORE bumping the package version.
`version` | Run AFTER bumping the package version, but BEFORE commit.
`postversion` | Run AFTER bumping the package version, and AFTER commit.
`pretest`, `test`, `posttest` | Run by the npm test command.
`prestop`, `stop`, `poststop` | Run by the npm stop command.
`prestart`, `start`, `poststart` | Run by the npm start command.
`prerestart`, `restart`, `postrestar` | Run by the npm restart command. Note: npm restart will run the stop and start scripts if no restart script is provided.
`preshrinkwrap`, `shrinkwrap`, `postshrinkwrap` | Run by the npm shrinkwrap command.

