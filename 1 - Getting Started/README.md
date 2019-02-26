# Module 1 - Getting Started

_Estimated Time to Completion: 15-25 minutes_

## What are we doing

In this module we will begin our basic interactions with Python. We will work with a few concepts in the command line. 

* Importing Modules
* Creating Variables
* Printing Data
* Accessing Environment Variables
* Simple Functions

We can launch the Python Shell by typing `python3` from our command prompt. To exit, type `exit()`.

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

The `import requests` block is one we will be using extensively as it allows you to interact with http requests.

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

It's very common for users to access variables set at an operating system level within Python scripts. This might be connection URLs or other configuration items. Usernames and credentials are discouraged to be stored as environment variables; but are sometimes used in this way for environments.

As mentioned earlier, we use the os module via `import os` to access methods that support reading environment variables (among other items). 

__In Bash__
```bash
export url='http://codyslab.com'
```
__In Python__
```python
import os
url = os.environ.get('url')
print(url)
```

## Simple Functions

Functions allow us to create reusable code that can be used throughout multiple python scripts. They also provide better capabilities around error handling and failure handling. Let's use the tricks we've learned so far in an example! Functions should have a couple of key components...

* A defined function name (required, for obvious reasons)
* Inputs (optional)
* Return statement

```python
import os

def examplefunction():
    a = 'Codys Function'
    url = os.environ.get('url')
    b = a + ' is at the address ' + url
    print(b)
    return b
```

We've done a few things in this example

* Imported our OS module
* Defined our examplefunction() which has no arguments
* Defined variables inside our function (both static, and from an environment variable)
* Concatenated values from other variables into a new variable
* Printed the variable
* Returned the final value

What if we wanted to include arguments? We can do this by placing the argument names within the function definition.

```python
def examplefunction(url):
    a = 'Grants Function'
    b = a + ' is at the address ' url
    print(b)
    return b

examplefunction('http://grantslab.com')
```

In this example we feed in a value (url) which is used to construct another variable. This looks pretty ugly. Lets introduce one final concept... F STRINGS! 

```python
def examplefunction(description):
    a = f'Chris has a {description} statment of work'
    print(a)
    return a

examplefunction('ugly')
```

Using F Strings we can feed our value directly into a string, in this case, we have simplified the code, and made it more readable. At the end, our function executes, calling Chris's Slaters statement of work ugly. Poor Chris.