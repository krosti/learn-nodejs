---
title: REPL & CLI
keywords: nodejs
last_updated: August 17, 2017
sidebar: node
permalink: repl-cli.html
---

## REPL

The term REPL stands for *Read Eval Print and Loop*. It specifies a computer environment like a window console or a Unix/Linux shell where you can enter the commands and the system responds with an output in an interactive mode.

### REPL Environment

The Node.js or node come bundled with REPL environment. Each part of the REPL environment has a specific work.

* Read: It reads user's input; parse the input into JavaScript data-structure and stores in memory.
* Eval: It takes and evaluates the data structure.
* Print: It prints the result.
* Loop: It loops the above command until user press ctrl-c twice.

### How to start REPL

You can start REPL by simply running "node" on the command prompt. You can execute various mathematical operations on REPL Node.js command prompt:

![](images/03-repl.png)

### Commands

Commands | Description
---------|----------
ctrl + c | It is used to terminate the current command.
ctrl + c twice | It terminates the node repl.
ctrl + d | It terminates the node repl.
up/down keys | It is used to see command history and modify previous commands.
tab keys | It specifies the list of current command.
.help | It specifies the list of all commands.
.break | It is used to exit from multi-line expressions.
.clear | It is used to exit from multi-line expressions.
.save filename | It saves current node repl session to a file.
.load filename | It is used to load file content in current node repl session.

## CLI

There is a wide variety of command line options in Node.js. These options provide multiple ways to execute scripts and other helpful run-time options.

Option   | Description
---------|----------
v, --version | It is used to print node's version.
-h, --help | It is used to print node command line options.
-e, --eval "script" | It evaluates the following argument as JavaScript. The modules which are predefined in the REPL can also be used in script.
-p, --print "script" | It is identical to -e but prints the result.
-c, --check | Syntax check the script without executing.
-i, --interactive | It opens the REPL even if stdin does not appear to be a terminal.
-r, --require module | It is used to preload the specified module at startup. It follows require()'s module resolution rules. Module may be either a path to a file, or a node module name.
--no-deprecation | Silence deprecation warnings.
--trace-deprecation | It is used to print stack traces for deprecations.
--throw-deprecation | It throws errors for deprecations.
--no-warnings | It silence all process warnings (including deprecations).
--trace-warnings | It prints stack traces for process warnings (including deprecations).
--trace-sync-io | It prints a stack trace whenever synchronous i/o is detected after the first turn of the event loop.
--zero-fill-buffers | Automatically zero-fills all newly allocated buffer and slowbuffer instances.
--track-heap-objects | It tracks heap object allocations for heap snapshots.
--prof-process | It processes V8 profiler output generated using the v8 option --prof.
--V8-options | It prints V8 command line options.
--tls-cipher-list=list | It specifies an alternative default tls cipher list. (requires node.js to be built with crypto support. (default))
--enable-fips | It enables fips-compliant crypto at startup. (requires node.js to be built with ./configure --openssl-fips)
--force-fips | It forces fips-compliant crypto on startup. (cannot be disabled from script code.) (same requirements as --enable-fips)
--icu-data-dir=file | It specifies ICU data load path. (Overrides node_icu_data)
