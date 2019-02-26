# Installing Modules

There are a number of ways we can install, import, and consume modules in Python

* Installing modules via PIP/PIP3 (individually)
* Bulk installing with PIP/PIP3 via a requirements.txt file
* Importing from a directory

In this module, we are going to cover the first and second methods of installing modules

## What is PIP

PIP and PIP3  (python2 and python3 respectively) are package managers for python code. Most commonly they are used to install modules for working in Python however there are many command line utilities that are installed via pip as well. PIP is something you will use very often in your Python adventures!

## Our First Module Install

We will be working extensively with a module called "requests" (http://docs.python-requests.org/en/master/). This module is not installed by default in Python3. From OUTSIDE a Python shell, we can do the following... 

```bash
pip3 install requests
```

Which will trigger an installation of the requests module. Once installed we can drop into our python shell

```bash
python3
```

And then we can import the python module for use

```python
import requests
```

## Installing Multiple Modules

When installing multiple modules in a project, consider distributing a requirements.txt file along with them, and using that as the reference list for installing. For example...

_requirements.txt_
```text
requests
flask
```

```bash
pip3 install -r requirements.txt
```

With these components installed, we are ready to get started with calling our APIs! 