# Sending JSON Responses

In this section of the book, we’re going to update our API handlers so that they return JSON responses instead of just plain text.

JSON (which is an acronym for *JavaScript Object Notation*) is a human-readable text format which can be used to represent structured data. As an example, in our project a movie could be represented with the following JSON:

```
{
  "id": 123,
  "title": "Casablanca",
  "runtime": 102,
  "genres": [
    "drama",
    "romance",
    "war"
  ],
  "version": 1
}
```

To give you a *very* quick overview of the JSON syntax…

+   - The parentheses {} define an *JSON object*, which is made up of comma-separated key/value pairs.