---
title: Event Loop
keywords: nodejs
last_updated: August 17, 2017
sidebar: node
permalink: event-loop.html
---

## What is the Event Loop?

The event loop is what allows Node.js to perform non-blocking I/O operations — despite the fact that JavaScript is single-threaded — by offloading operations to the system kernel whenever possible.

Since most modern kernels are multi-threaded, they can handle multiple operations executing in the background. When one of these operations completes, the kernel tells Node.js so that the appropriate callback may be added to the poll queue to eventually be executed. We'll explain this in further detail later in this topic.

### Event Loop Explained

When Node.js starts, it initializes the event loop, processes the provided input script which may make async API calls, schedule timers, or call process.nextTick(), then begins processing the event loop.

```
   ┌───────────────────────┐
┌─>│        timers         │
│  └──────────┬────────────┘
│  ┌──────────┴────────────┐
│  │     I/O callbacks     │
│  └──────────┬────────────┘
│  ┌──────────┴────────────┐
│  │     idle, prepare     │
│  └──────────┬────────────┘      ┌───────────────┐
│  ┌──────────┴────────────┐      │   incoming:   │
│  │         poll          │<─────┤  connections, │
│  └──────────┬────────────┘      │   data, etc.  │
│  ┌──────────┴────────────┐      └───────────────┘
│  │        check          │
│  └──────────┬────────────┘
│  ┌──────────┴────────────┐
└──┤    close callbacks    │
   └───────────────────────┘
```

Each phase has a FIFO queue of callbacks to execute. While each phase is special in its own way, generally, when the event loop enters a given phase, it will perform any operations specific to that phase, then execute callbacks in that phase's queue until the queue has been exhausted or the maximum number of callbacks has executed. When the queue has been exhausted or the callback limit is reached, the event loop will move to the next phase, and so on.

Since any of these operations may schedule more operations and new events processed in the poll phase are queued by the kernel, poll events can be queued while polling events are being processed. As a result, long running callbacks can allow the poll phase to run much longer than a timer's threshold.

### Phases Overview

* timers: this phase executes callbacks scheduled by setTimeout() and setInterval().
* I/O callbacks: executes almost all callbacks with the exception of close callbacks, the ones scheduled by timers, and setImmediate().
* idle, prepare: only used internally.
* poll: retrieve new I/O events; node will block here when appropriate.
* check: setImmediate() callbacks are invoked here.
* close callbacks: e.g. socket.on('close', ...).

Between each run of the event loop, Node.js checks if it is waiting for any asynchronous I/O or timers and shuts down cleanly if there are not any.

### Limitations

Because of the event loop, Node.js doesn't have to start a new thread for every incoming tcp connection. This allows node to service hundreds of thousands of requests concurrently , as long as you aren't calculating the first 1000 prime numbers for each request.

This also means it's important to not do CPU intensive operations, as these will keep a lock on the event loop and prevent other asynchronous paths of execution from continuing. It's also important to not use the sync variant of all the I/O methods, as these will keep a lock on the event loop as well.

If you want to do CPU heavy things you should ether delegate it to a different process that can execute the CPU bound operation more efficiently or you could write it as a node native add on.