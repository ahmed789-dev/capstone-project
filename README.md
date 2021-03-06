# Casting Agency

Casting Agency is a service that is responsible for creating movies and managing and assigning actors to those movies.

The application performs the following functions:
- Showing existing actors and movies, creating actors and movies, editing actors and movies data, delete actors and movies.
- **Casting Assistant** can view actors and movies.
- **Casting Director** has all permissions of Casting Assistant, add or delete an actor from the database and modify actors or movies.
- **Executive Producer** has all permissions of Casting Director and add or delete a movie from the database.

# Getting started

- Casting Agency API is hosted on heroku
- **Base URL**: [localhost:5000/](http://localhost:5000/)

- API has an Authentication managed by Auth0

# Error Handling

**Errors** are returned as JSON object like th following:

```
{
    "success": False,
    "error": 400,
    "message": "bad request"
}
```
#### API will handle these errors:
- **400** bad request
- **404** resources not found
- **422** unprocessable
- **500** Internal Server error

# Endpoints

### GET /actors

- returns list of actors and success value
- sample `curl -X GET http://localhost:5000/actors`

```
{
    "actors": [
        {
            "name": "actor name",
            "age": "15",
            "gender": "male"
        }, 
        {
            "name": "actor name 2",
            "age": "15",
            "gender": "male"
        }
    ], 
    "success": True
}
```


### GET /movies
- returns list of movies and success value
- sample `curl -X GET http://localhost:5000/movies`

```
{
    "movies": [
        {
            "title": "movie 1",
            "release_date": "1-1-2020"
        }, 
        {
            "title": "movie 2",
            "release_date": "1-1-2020"
        }
    ], 
    "success": True
}
```


### POST /actors
- takes JSON object as an argument like : `{"name": "actor name", "age": "15", "gender": "male"}`
- takes authorization header argument in the request
- returns the ID of the created actor and success value
- sample `curl -X POST http://localhost:5000/actors -H "Content-Type:application/json" -d '{"name": "actor name", "age": "15", "gender": "male"} -H "Authorization: Bearer mytoken123"'`

```
{
    "success": True,
    "actor": 1
}
```



### POST /movies
- takes JSON object as an argument like : `{"title": "movie 1", "release_date": "1-1-2020"}`
- takes authorization header argument in the request
- returns the ID of the created movie and success value
- sample `curl -X POST http://localhost:5000/movies -H "Content-Type:application/json" -d '{"title": "movie 1", "release_date": "1-1-2020"} -H "Authorization: Bearer mytoken123"'`

```
{
    "success": True,
    "movie": 1
}
```


### DELETE /actors/<actor_id>
- takes authorization header argument in the request
- returns id of deleted actor and success value
- sample `curl -X DELETE http://localhost:5000/actors/1 -H "Authorization: Bearer mytoken123"`

```
{
    "success": True,
    "actor": 1
}
```


### DELETE /movies/<movie_id>
- takes authorization header argument in the request
- returns id of deleted movie and success value
- sample `curl -X DELETE http://localhost:5000/movies/1 -H "Authorization: Bearer mytoken123"`

```
{
    "success": True,
    "movie": 1
}
```


### PATCH /actors/<actor_id>
- takes JSON object as an argument like: `{"name": "edited actor name"}`
- takes authorization header argument in the request
- returns edited actor and success value
- sample `curl -X PATCH http://localhost:5000/actors/1 -H "Content-Type:application/json" -d '{"name": "edited actor name"}' -H "Authorization: Bearer mytoken123"`

```
{
    "success": True,
    "actor": {
        "name": "edited actor name",
        "age": "15",
        "gender": "male"
    }
}
```


### PATCH /movies/<movie_id>
- takes JSON object as an argument like: `{"title": "edited movie title"}`
- takes authorization header argument in the request
- returns edited movie and success value
- sample `curl -X PATCH http://localhost:5000/movies/1 -H "Content-Type:application/json" -d '{"title": "edited movie title"}' -H "Authorization: Bearer mytoken123"`

```
{
    "success": True,
    "movie": {
        "title": "edited movie title",
        "release_date": "1-1-2020"
    }
}
```
