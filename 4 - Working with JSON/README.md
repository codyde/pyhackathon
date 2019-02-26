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

