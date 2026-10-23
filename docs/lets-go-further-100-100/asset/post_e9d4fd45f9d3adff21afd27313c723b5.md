
For example, if we try sending a request with an invalid Host header value we will get a response like this:

```
$ curl -i -H "Host: こんにちは" http://localhost:4000/v1/healthcheck
HTTP/1.1 400 Bad Request: malformed Host header
Content-Type: text/plain; charset=utf-8
Connection: close

400 Bad Request: malformed Host header
```

Unfortunately, these responses are hard-coded into the Go standard library, and there’s nothing we can do to customize them to use JSON instead.

But while this is something to be aware of, it’s not necessarily something to worry about. In a production environment it’s relatively unlikely that well-behaved, non-malicious, clients would trigger these responses anyway, and we shouldn’t be overly concerned if bad clients are sometimes sent a plain-text response instead of JSON.

## Chapter 4.

## Parsing JSON Requests

So far we’ve been looking at how to create and send JSON responses from our API, but in this next section of the book we’re going to explore things from the other side and discuss how to *read and parse JSON requests* from clients.

To help demonstrate this, we’re going to start work on the `POST /v1/movies` endpoint and `createMovieHandler` that we set up earlier.

| Method | URL Pattern | Handler | Action |
|---|---|---|---|
| GET | /v1/healthcheck | healthcheckHandler | Show application information |
| POST | /v1/movies | createMovieHandler | Create a new movie |
| GET | /v1/movies/:id | showMovieHandler | Show the details of a specific movie |

When a client calls this endpoint, we will expect them to provide a JSON request body containing data for the movie they want to create in our system. So, for example, if a client wanted to add a record for the movie *Moana* to our API, they would send a request body similar to this:

```json
{
  "title": "Moana",
  "year": 2016,
  "runtime": 107,
  "genres": ["animation", "adventure"]
}
```

For now, we’ll just focus on the reading, parsing and validation aspects of dealing with this JSON request body. Specifically you’ll learn:

- How to read a request body and decode it to a native Go object using the `encoding/json` package.
- How to deal with bad requests from clients and invalid JSON, and return clear, actionable, error messages.
- How to create a reusable helper package for validating data to ensure it meets your business rules.
- Different techniques for controlling and customizing how JSON is decoded.

```
...
func (app *application) createMovieHandler(w http.ResponseWriter, r
*http.Request) {
    // Declare an anonymous struct to hold the information that we expect to
be in the
    // HTTP request body (note that the field names and types in the struct
are a subset
    // of the Movie struct that we created earlier). This struct will be our
*target
    // decode destination*.
    var input struct {
        Title   string  `json:"title"`
        Year    int32   `json:"year"`
        Runtime int32   `json:"runtime"`
        Genres  []string `json:"genres"`
    }

    // Initialize a new json.Decoder instance which reads from the request
body, and
    // then use the Decode() method to decode the body contents into the
input struct.
    // Importantly, notice that when we call Decode() we pass a *pointer* to
the input
    // struct as the target decode destination. If there was an error during
decoding,
    // we also use our generic errorResponse() helper to send the client a
400 Bad
    // Request response containing the error message.
    err := json.NewDecoder(r.Body).Decode(&input)
    if err != nil {
        app.errorResponse(w, r, http.StatusBadRequest, err.Error())
        return
    }

    // Dump the contents of the input struct in a HTTP response.
    fmt.Fprintf(w, "%+v\n", input)
}
```

```
...
```

There are a few important and interesting things about this code to point out:

- When calling `Decode()` you must pass a *non-nil pointer* as the target decode destination. If you don’t use a pointer, it will return a `json.InvalidUnmarshalError` error at runtime.
- If the target decode destination is a struct — like in our case — the struct fields must be exported (start with a capital letter). Just like with encoding, they need to be exported so that they’re visible to the `encoding/json` package.
- When decoding a JSON object into a struct, the key/value pairs in the JSON are mapped to the struct fields based on the struct tag names. If there is no matching struct tag, Go will attempt to decode the value into a field that matches the key name (exact matches are preferred, but it will fall back to a case-insensitive match). *Any JSON key/value pairs which cannot be successfully mapped to the struct fields will be silently ignored.*
- There is no need to close `r.Body` after it has been read. This will be done automatically by Go’s `http.Server`, so you don’t have to.

OK, let’s take this for a spin.

request with no `year` in the JSON, like so:

```
$ BODY='{"title":"Moana","runtime":107, "genres":["animation","adventure"]}'
$ curl -d "$BODY" localhost:4000/v1/movies
{Title:Moana Year:0 Runtime:107 Genres:[animation adventure]}
```

As you might have guessed, when we do this the `Year` field in our `input` struct is left with its zero value (which happens to be `0` because the `Year` field is an `int32` type).

This leads to an interesting question: how can you tell the difference between a client not providing a key/value pair, and providing a key/value pair but deliberately setting it to its zero value? Like this:

```
$ BODY='{"title":"Moana","year":0,"runtime":107, "genres":
["animation","adventure"]}'
$ curl -d "$BODY" localhost:4000/v1/movies
{Title:Moana Year:0 Runtime:107 Genres:[animation adventure]}
```

The end result is the same, despite the different HTTP requests, and it’s not immediately obvious how to tell the difference between the two scenarios. We’ll circle back to this topic later in the book, but for now, it’s worth just being aware of this behavior.

## Additional Information

## Supported destination types

It’s important to mention that certain JSON types can only be successfully decoded to certain Go types. For example, if you have the JSON string `"foo"` it can be decoded into a Go `string`, but trying to decode it into a Go `int` or `bool` will result in an error at runtime (as we’ll demonstrate in the next chapter).

The following table shows the supported target decode destinations for the different JSON types:

| JSON type | ⇒ | Supported Go types |
|---|---|---|
| JSON boolean | ⇒ | bool |
| JSON string | ⇒ | string |
| JSON number | ⇒ | int*, uint*, float*, rune |
| JSON array | ⇒ | array, slice |
| JSON object | ⇒ | struct, map |

## Using the json.Unmarshal function

As we mentioned at the start of this chapter, it’s also possible to use the `json.Unmarshal()` function to decode a HTTP request body.

For example, you could use it in a handler like this:

## Managing Bad Requests

Our `createMovieHandler` now works well when it receives a valid JSON request body with the appropriate data. But at this point you might be wondering:

- What if the client sends something that isn’t JSON, like XML or some random bytes?
- What happens if the JSON is malformed or contains an error?
- What if the JSON types don’t match the types we are trying to decode into?
- What if the request doesn’t even contain a body?

Well… let’s look and see!

```
# Send some XML as the request body
$ curl -d '<?xml version="1.0" encoding="UTF-8"?><note><to>Alice</to></note>' localhost:4000/v1/movies
{
  "error": "invalid character '\u003c' looking for beginning of value"
}

# Send some malformed JSON (notice the trailing comma)
$ curl -d '{"title": "Moana", }' localhost:4000/v1/movies
{
  "error": "invalid character '}' looking for beginning of object key string"
}
```
