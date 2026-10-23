For example, if a client wanted to add the genre `sci-fi` to the movie *Black Panther* in our database, they would need to send a JSON request body which looks like this:

```
{
  "title": "Black Panther",
  "year": 2018,
  "runtime": "134 mins",
  "genres": [
    "action",
    "adventure",
    "sci-fi"
  ]
}
```

# Executing the SQL query

Let’s start in our database model again, and edit the `Update()` method to execute the following SQL query:

```
UPDATE movies
SET title = $1, year = $2, runtime = $3, genres = $4, version = version + 1
WHERE id = $5
RETURNING version
```

Notice here that we’re incrementing the `version` value as part of the query? And then at the end we’re using the `RETURNING` clause to