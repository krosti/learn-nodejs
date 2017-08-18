---
title: Globals
keywords: nodejs
last_updated: August 17, 2017
sidebar: node
permalink: globals.html
---

## Global Objects

Node.js global objects are global in nature and available in all modules. You don't need to include these objects in your application; rather they can be used directly. These objects are modules, functions, strings and object etc. Some of these objects aren't actually in the global scope but in the module scope.

Global objects are given below:

* __dirname
* __filename
* Console
* Process
* Buffer
* setImmediate(callback[, arg][, ...])
* setInterval(callback, delay[, arg][, ...])
* setTimeout(callback, delay[, arg][, ...])
* clearImmediate(immediateObject)
* clearInterval(intervalObject)
* clearTimeout(timeoutObject)

### __dirname

It is a string. It specifies the name of the directory that currently contains the code.

```
console.log(__dirname);  // outputs: /var/www/my-projects/
```

### __filename

It specifies the filename of the code being executed. This is the resolved absolute path of this code file. The value inside a module is the path to that module file.

```
console.log(__filename);  // outputs: /var/www/my-projects/my-sample.js
```

### Console

The Node.js console module provides a simple debugging console similar to JavaScript console mechanism provided by web browsers.

There are three console methods that are used to write any Node.js stream:

* console.log() is used to display simple message on console.
* console.error() is used to render error message on console.
* console.warn() is used to display warning message on console.

```
console.log('I am a simple message');
console.error('Fatal error');
console.warn('I am warning');
```

### Buffers 

Node.js provides Buffer class to store raw data similar to an array of integers but corresponds to a raw memory allocation outside the V8 heap. Buffer class is used because pure JavaScript is not nice to binary data. So, when dealing with TCP streams or the file system, it's necessary to handle octet streams.

Buffer class is a global class. It can be accessed in application without importing buffer module.

#### Creating buffers

Examples:

* Create an uninitiated buffer:

`var buf = new Buffer(10);`

* Create a buffer from array:

`var buf = new Buffer([10, 20, 30, 40, 50]);`

* Create a buffer from string, you can pass the encoding (optional)

`var buf = new Buffer('Node Tutorial', 'utf-8');`

#### Writing to buffers

Syntax: `buf.write(string[, offset][, length][, encoding]);`

Parameter explanation:

**string**: It specifies the string data to be written to buffer.

**offset**: It specifies the index of the buffer to start writing at. Its default value is 0.

**length**: It specifies the number of bytes to write. Defaults to buffer.length

**encoding**: Encoding to use. 'utf8' is the default encoding.

Return values from writing buffers:

This method is used to return number of octets written. In the case of space shortage for buffer to fit the entire string, it will write a part of the string.

```
buf = new Buffer(256);  
len = buf.write('Node Tutorial');  
console.log('Octets written : '+  len);  // outputs: Octets written : 13
```

#### Reading from buffers

Syntax: `buf.toString([encoding][, start][, end]);`

Parameter explanation:

**encoding**: It specifies encoding to use. 'utf8' is the default encoding

**start**: It specifies beginning index to start reading, defaults to 0.

**end**: It specifies end index to end reading, defaults is complete buffer.

```
buf = new Buffer(26);  
for (var i = 0 ; i < 26 ; i++) {  
  buf[i] = i + 97;  
}  
console.log(buf.toString('ascii'));         // outputs: abcdefghijklmnopqrstuvwxyz  
console.log(buf.toString('ascii', 0, 5));   // outputs: abcde  
console.log(buf.toString('utf8', 0, 5));    // outputs: abcde  
console.log(buf.toString(undefined, 0, 5)); // encoding defaults to 'utf8', outputs abcde 
```

### Timer

Timer functions are global functions. You don't need to use require() function in order to use timer functions. Let's see the list of timer functions.

Set timer functions:

* setImmediate(): It is used to execute setImmediate.
* setInterval(): It is used to define a time interval.
* setTimeout(): It is used to execute a one-time callback after delay milliseconds.

Clear timer functions:

* clearImmediate(immediateObject): It is used to stop an immediateObject, as created by setImmediate
* clearInterval(intervalObject): It is used to stop an intervalObject, as created by setInterval
* clearTimeout(timeoutObject): It prevents a timeoutObject, as created by setTimeout

**Example:**

```
setInterval(function() {  
 console.log('setInterval: Hey! 5 seconds completed!');   
}, 5000);
```

