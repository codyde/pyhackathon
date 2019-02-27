# Working with JSON

It's common for REST API responses to be in JSON (JavaScript Object Notation) format, as the Star Wars API demonstrated in our last module. You will often want to extract individual bits of data from these, and perhaps create new objects from them.

In order to access these objects, we will need to parse the data using Python. We will start off with our function from the last module (Our First API Call - Requests and Responses)

```python
def get_starwars_character(id):
    req = requests.get(f'https://swapi.co/api/people/{id}/')
    return req.json()
```

## Access the Data

When we execute the function above by entering `get_starwars_character(1)` we are returned with the Master Jedi himself, Luke Skywalker as you can see below

```python
>>> get_starwars_character(1)
{'name': 'Luke Skywalker', 'height': '172', 'mass': '77', 'hair_color': 'blond', 'skin_color': 'fair', 'eye_color': 'blue', 'birth_year': '19BBY', 'gender': 'male', 'homeworld': 'https://swapi.co/api/planets/1/', 'films': ['https://swapi.co/api/films/2/', 'https://swapi.co/api/films/6/', 'https://swapi.co/api/films/3/', 'https://swapi.co/api/films/1/', 'https://swapi.co/api/films/7/'], 'species': ['https://swapi.co/api/species/1/'], 'vehicles': ['https://swapi.co/api/vehicles/14/', 'https://swapi.co/api/vehicles/30/'], 'starships': ['https://swapi.co/api/starships/12/', 'https://swapi.co/api/starships/22/'], 'created': '2014-12-09T13:50:51.644000Z', 'edited': '2014-12-20T21:17:56.891000Z', 'url': 'https://swapi.co/api/people/1/'}
```

Since we are returning the JSON object as part of the function call, this makes it much easier for us to parse. We can choose to either parse it inline...

`get_starwars_character(1)['name']`

or we can convert it to an object and parse that directly...

```python
char = get_starwars_character(1)
print(char['name'])
```

```bash
>>> char = get_starwars_character(1)
>>> print(char['name'])
Luke Skywalker
```

We can also use a new capability we haven't discussed yet, a loop, access multiple keys within the array...

```python
for i in char:
    print(i)
```

As you can see from this statement, we are printing out all of the keys (but not values) associated with a JSON object.

## Dealing with Multiple Objects

Lets try something net new. What if we want to print the names of every star wars character in the API? This a different route than the one previously used, as well as likely deealing with another (aka A LOT of other...).

Thus far, we've been using the following api `https://swapi.co/api/people/{id}/` for calling data which requires an ID input to grab the character object.

We can pull all characters from the api using the following URL - `https://swapi.co/api/people`. Lets construct a function around it.

```python
def getallcharacters():
    url = 'https://swapi.co/api/people'
    chars = requests.get(url)
    return chars.json()
```

When we return this we actually get a very different object from before. This list is paginated, and only the first set of objects is shown. We can see in our repsonse. Maybe a good challenge exercise would be writing a function that lists all of them? 

Back to the topic at hand, we can see that this JSON object is behind several objects. If we look at the keys (or plug them into a parser like https://jsoneditoronline.org/) we can see that the data we care about is behind a "results" key. Lets update our call. Note, this call will only return the first page. 

```python
def getallcharacters():
    url = 'https://swapi.co/api/people'
    chars = requests.get(url)
    return chars.json()['results']
```

Thats better, now we're getting our main content! What if we want to just return character names? Lets expand our function. 

```python
def getcharacternames():
    chars = getallcharacters()
    for i in chars:
        print(i['name'])
```

Finally, what if we wanted to create a new JSON object that held all of these names? We can easily do that by constructing a new JSON object!

```python
def createcharacterjson():
    names = []
    chars = getallcharacters()
    for i in chars: 
        namedata = {}
        namedata['name'] =  i['name']
        names.append(namedata)
    return names
```

Success! We can see our final returned JSON is a new object consisting of all of the characters from the first page, in a new JSON object. 