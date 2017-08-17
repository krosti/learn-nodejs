---
title: Package Managers
keywords: nodejs
last_updated: August 17, 2017
sidebar: node
permalink: package-manager.html
---

## Package Managers

### NPM

Node Package Manager provides two main functionalities:

* It provides online repositories for NodeJS packages/modules which are searchable on search.nodejs.org
* It also provides command line utility to install NodeJS packages, do version management and dependency management of NodeJS packages.

The npm comes bundled with NodeJS installables in versions after that v0.6.3. You can check the version by opening NodeJS command prompt and typing the following command:

`npm -v`

#### Installing Modules

Following is the syntax to install any NodeJS module:

`npm install <module name>`

for example

`npm install express`

#### Uninstalling Modules

To uninstall a NodeJS module, use the following command:

`npm uninstall <module name>`

for example

`npm uninstall express`

#### Global vs. Local installation

By default, npm installs dependency in local mode. Here local mode specifies the folder where Node application is present. For example if you installed express module, it created node_modules directory in the current directory where it installed express module.

You can install a local package like a developer dependecy to avoid adding that package into the production build, it's very used for linters, testing tools and everything that shouldn't be in the production bundle.

`npm install mocha --save-dev`

Globally installed packages/dependencies are stored in system directory. Let's install express module using global installation. Although it will also produce the same result but modules will be installed globally.

You can install a global package by adding the `-g` flag in the install command

`npm install -g typescript`

### Yarn

Yarn is a new package manager for JavaScript developed by Facebook. 

The easiest way to get started is to run:

```
npm install -g yarn
yarn
```

The `yarn` CLI replaces `npm` in your development workflow, either with a matching command or a new, similar command:

`npm install → yarn`

`npm install --save <module name> → yarn add <module name>`

`npm install --save-dev <module name> → yarn add <module name> --dev`

#### CLI commands comparison

npm | Yarn
----|-----
`npm install` | `yarn install`
(N/A) | `yarn install --flat`
(N/A) | `yarn install --har`
(N/A) | `yarn install --no-lockfile`
(N/A) | `yarn install --pure-lockfil`
`npm install [package]` | (N/A)
`npm install --save [package]` | `yarn add [package]`
`npm install --save-dev [package]` | `yarn add [package] [--dev/-D]`
(N/A) | `yarn add [package] [--peer/-P]`
`npm install --save-optional [package]` | `yarn add [package] [--optional/-O]`
`npm install --save-exact [package]` | `yarn add [package] [--exact/-E]`
(N/A) | `yarn add [package] [--tilde/-T]`
`npm install --global [package]` | `yarn global add [package]`
`npm update --global` | `yarn global upgrade`
`npm rebuild` | `yarn install --force`
`npm uninstall [package]` | (N/A)
`npm uninstall --save [package]` | `yarn remove [package]`
`npm uninstall --save-dev [package]` | `yarn remove [package]`
`npm uninstall --save-optional [package]` | `yarn remove [package]`
`npm cache clean` | `yarn cache clean`
`rm -rf node_modules && npm install` | `yarn upgrade`


