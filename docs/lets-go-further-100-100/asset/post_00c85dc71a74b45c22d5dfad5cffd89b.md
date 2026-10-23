
For example, if we wanted the value of our Runtime field to be represented as a JSON string (instead of a number) we could use the string directive like this:

```
type Movie struct {
    ID          int64       `json:"id"`
    CreatedAt   time.Time   `json:"-"`
    Title       string      `json:"title"`
    Year        int32       `json:"year,omitempty"`
    Runtime     int32       `json:"runtime,omitempty,string"` // Add the string directive
    Genres      []string    `json:"genres,omitempty"`
    Version     int32       `json:"version"`
}
```

And the resulting JSON output would look like this:

```
{
    "id": 123,
    "title": "Casablanca",
    "runtime": "102",     ← This is now a string
    "genres": [
        "drama",
        "romance",
        "war"
    ],
    "version": 1
}
```

Note that the `string` directive will only work on struct fields which have `int*`, `uint*`, `float*` or `bool` types. For any other type of struct field it will have no effect.

## Chapter 3.4.

## Formatting and Enveloping Responses

So far in this book we’ve generally been making requests to our API using Firefox, which makes the JSON responses easy-to-read thanks to the ‘pretty printing’ provided by the built-in JSON viewer.

But if you try making some requests using curl, you’ll see that the actual JSON response data is all just on one line with no whitespace.

```
$ curl localhost:4000/v1/healthcheck
{"environment":"development","status":"available","version":"1.0.0"}

$ curl localhost:4000/v1/movies/123
{"id":123,"title":"Casablanca","runtime":102,"genres":["drama","romance","war"],"version":1}
```

We can make these easier to read in terminals by using the `json.MarshalIndent()` function to encode our response data, instead of the regular `json.Marshal()` function. This automatically adds whitespace to the JSON output, putting each element on a separate line and prefixing each line with optional *prefix* and *indent* characters.

Let’s update our `writeJSON()` helper to use this instead:

Note: Behind the scenes `json.MarshalIndent()` works by calling `json.Marshal()` as normal, then running the JSON through the standalone `json.Indent()` function to add the whitespace. There’s also a reverse function available, `json.Compact()`, which you can use to remove whitespace from JSON.

## Enveloping responses

Next let's work on updating our responses so that the JSON data is always *enveloped* in a parent JSON object. Similar to this:

```
{
  "movie": {
    "id": 123,
    "title": "Casablanca",
    "runtime": 102,
    "genres": [
      "drama",
      "romance",
      "war"
    ],
    "version":1
  }
}
```

Notice how the movie data is nested under the key "movie" here, rather than being the top-level JSON object itself?

```
package main

...

// Define an envelope type.
type envelope map[string]interface{}

// Change the data parameter to have the type envelope instead of interface{}.
func (app *application) writeJSON(w http.ResponseWriter, status int, data envelope, headers http.Header) error {
    js, err := json.MarshalIndent(data, "", "\t")
    if err != nil {
        return err
    }

    js = append(js, '\n')

    for key, value := range headers {
        w.Header()[key] = value
    }

    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(status)
    w.Write(js)

    return nil
}
```

Then we need to update our showMovieHandler to create an instance of the envelope map containing the movie data, and pass this onwards to our writeJSON() helper instead of passing the movie data directly.

Like so:

File: cmd/api/movies.go

```go
package main

...

func (app *application) showMovieHandler(w http.ResponseWriter, r *http.Request) {
    id, err := app.readIDParam(r)
    if err != nil {
        http.NotFound(w, r)
        return
    }

    movie := data.Movie{
        ID:         id,
        CreatedAt:  time.Now(),
        Title:      "Casablanca",
        Runtime:    102,
        Genres:     []string{"drama", "romance", "war"},
        Version:    1,
    }

    // Create an envelope{"movie": movie} instance and pass it to writeJSON(), instead
    // of passing the plain movie struct.
    err = app.writeJSON(w, http.StatusOK, envelope{"movie": movie}, nil)
    if err != nil {
        app.logger.Println(err)
        http.Error(w, "The server encountered a problem and could not process your request", http.StatusInternalServerError)
    }
}
```

We also need to update the code in our healthcheckHandler so that it passes an envelope type to the writeJSON() helper too:

```
File: cmd/api/healthcheck.go

package main

...

func (app *application) healthcheckHandler(w http.ResponseWriter, r *http.Request) {
    // Declare an envelope map containing the data for the response. Notice that the way
    // we've constructed this means the environment and version data will now be nested
    // under a system_info key in the JSON response.
    env := envelope{
        "status": "available",
        "system_info": map[string]string{
            "environment": app.config.env,
            "version":     version,
        },
    }

    err := app.writeJSON(w, http.StatusOK, env, nil)
    if err != nil {
        app.logger.Println(err)
        http.Error(w, "The server encountered a problem and could not process your request", http.StatusInternalServerError)
    }
}
```

Alright, let’s try these changes out. Go ahead and restart the server, then use curl to make some requests to the API endpoints again.

You should now get responses formatted like the ones below.

```
$ curl localhost:4000/v1/movies/123
{
    "movie": {
        "id": 123,
        "title": "Casablanca",
        "runtime": 102,
        "genres": [
            "drama",
            "romance",
            "war"
        ],
        "version":1
    }
}

$ curl localhost:4000/v1/healthcheck
{
    "status": "available",
    "system_info": {
        "environment": "development",
        "version": "1.0.0"
    }
}
```

## Additional Information

## Response structure

## Advanced JSON Customization

By using struct tags, adding whitespace and enveloping the data, we’ve been able to add quite a lot of customization to our JSON responses already. But what happens when these things aren’t enough, and you need the freedom to customize your JSON even more?

To answer this question, we first need to talk some theory about how Go handles JSON encoding behind the scenes. The key thing to understand is this:

> *When Go is encoding a particular type to JSON, it looks to see if the type has a `MarshalJSON()` method implemented on it. If it has, then Go will call this method to determine how to encode it.*

That language is a bit fuzzy, so let’s be more exact.

Strictly speaking, when Go is encoding a particular type to JSON it looks to see if the type satisfies the `json.Marshaler` interface, which looks like this:

```
type Marshaler interface {
    MarshalJSON() ([]byte, error)
}
```

If the type does satisfy the interface, then Go will call its `MarshalJSON()` method and use the `[]byte` slice that it returns as the encoded JSON value.

If the type doesn’t have a `MarshalJSON()` method, then Go will fall back to trying to encode it to JSON based on its own internal set of rules.

So, if we want to customize how something is encoded, all we need to do is implement a `MarshalJSON()` method on it which returns a *custom JSON representation of itself* in a `[]byte` slice.

> **Hint:** You can see this in action if you look at the source code for Go’s `time.Time` type. Behind the scenes `time.Time` is actually a `struct`, but it has a `MarshalJSON()` method which outputs a RFC 3339 format representation of itself. This is what gets called whenever a `time.Time` value is encoded to JSON.

## Customizing the Runtime field

To help illustrate this, let’s look at a concrete example in our application.

When our `Movie` struct is encoded to JSON, the `Runtime` field (which is an `int32` type) is currently formatted as a JSON number. Let’s change this so that it’s encoded as a string with the format `"<runtime> mins"` instead. Like so:
