# Our First API Call - Requests and Responses

In our previous module we installed the requests module. The requests module is a very easy to use module for communicating with a variety of endpoints. In our case, we'll be specifically working with the Star Wars API endpoint. The request module has built in methods for performing GET, POST, and all of the other common methods for communicating with API's. 

It's highly reccommended to review the documentation for the requests module often (http://docs.python-requests.org/en/master/). 

## Import and Request 

We will start by initiating a python3 prompt...

```bash
python3
```

And importing the requests module

```python
import requests
```

At this point the module is loaded into our session and we can begin to interact with it. Let's perform our first sample call. 

`requests.get('https://swapi.co/api/people/1/')`

Uh oh... You probably see something like this 

```python3 
>>> requests.get('https://swapi.co/api/people/1/')
<Response [200]>
```

Good news, it worked. Bad news, you can't see anything. That my friends is an object. You returned and object. Yay? 

In our first module, we mentioned that Python is an object oriented language. It is going to be extremely common to define variables as we begin to interact with objects. Let's demonstrate what this means 

```python
>>> import requests
>>> req = requests.get('https://swapi.co/api/people/1/')
```

Well, no error. That's good I guess? IT IS GOOD NEWS. Type in `req` and hit tab. Autocomplete will kick in and you'll see all the methods available against a request object. 

```bash
>>> req.
req.apparent_encoding      req.iter_lines(
req.close(                 req.json(
req.connection             req.links
req.content                req.next
req.cookies                req.ok
req.elapsed                req.raise_for_status(
req.encoding               req.raw
req.headers                req.reason
req.history                req.request
req.is_permanent_redirect  req.status_code
req.is_redirect            req.text
req.iter_content(          req.url
```

If we do `req.text` we can see the text output of this entry. Very cool! 

```bash
>>> req.text
'{"name":"Luke Skywalker","height":"172","mass":"77","hair_color":"blond","skin_color":"fair","eye_color":"blue","birth_year":"19BBY","gender":"male","homeworld":"https://swapi.co/api/planets/1/","films":["https://swapi.co/api/films/2/","https://swapi.co/api/films/6/","https://swapi.co/api/films/3/","https://swapi.co/api/films/1/","https://swapi.co/api/films/7/"],"species":["https://swapi.co/api/species/1/"],"vehicles":["https://swapi.co/api/vehicles/14/","https://swapi.co/api/vehicles/30/"],"starships":["https://swapi.co/api/starships/12/","https://swapi.co/api/starships/22/"],"created":"2014-12-09T13:50:51.644000Z","edited":"2014-12-20T21:17:56.891000Z","url":"https://swapi.co/api/people/1/"}'
```

That is a whole lot of squiggly lines and such though! 