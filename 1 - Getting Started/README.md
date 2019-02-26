# Module 1 - Getting Started

_Estimated Time to Completion: 15-25 minutes_

## What are we doing

In this module we will begin our basic interactions with Python. We will work with a few concepts in the command line 

* Importing Modules
* Creating Variables
* Printing Data
* Accessing Environment Variables
* Simple Functions

## Importing Modules

Modules expose additional functionality to the basesline python capabilities. Virtually every method and function is accessed after importing a module. Take the following script block...

```python
import json
import os
import flask
import requests
```

In this block we are importing several modules that ar commonly used. 

The `import json` block allows us to manipulate and create JSON (JavaScript Object Notation) objects (more on that later.

The`import os` is something we can use to read in Operating System environment variables and much more!

The `import flask` block references access a webframework known as flask. We will be covering this platform in a much later tutorial, but if you want to skip ahead, no one is stopping you :) (http://flask.pocoo.org/)

The `import requests` block is one we will be using extnesively as it allows you to interact with http requests.

## Creating Variables

Variables are values stored within memory behind an identifier. Python is an object oritented programming language, which means we will be frequently creating variables that represent objects, and then interacting with that object. As an example, we will call the Star Wars API and store the connection as a variable. The connection itself is an OBJECT, and using the variable, we are able to perform methods against that object. 

Creating variables is easy!

```python
a = "Codys Variable"
b = "Grant's Variable"
c = "Chris Slater doesn't get a variable"
```

Theses variables are all "string" variables, meaning simple words. Objects are another matter, but often created in the same way, we will come back to those later! 

## Printing Data

In Python3 the syntax for printing (returning data to the screen) has changed. We can print data back by either referencing a variable, or directly calling a string or number. For example...

```python
print('hello world!')
a = 'hello VMware'
print(a)
```

## Access Environment Variables

## Simple Functions