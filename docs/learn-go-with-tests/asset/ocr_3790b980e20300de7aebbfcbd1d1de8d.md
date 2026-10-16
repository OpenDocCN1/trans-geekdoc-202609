In my experience tests that assert against JSON strings have the following problems.

+   - *Brittleness.* If you change the data-model your tests will fail.
+   - *Hard to debug.* It can be tricky to understand what the actual problem is when comparing two JSON strings.
+   - *Poor intention.* Whilst the output should be JSON, what's really important is exactly what the data is, rather than how it's encoded.
+   - *Re-testing the standard library.* There is no need to test how the standard library outputs JSON, it is already tested. Don't test other people's code.

Instead, we should look to parse the JSON into data structures that are relevant for us to test with.

# Data modelling

Given the JSON data model, it looks like we need an array of `Player` with some fields so we have created a new type to capture this.

```
//server.go
type Player struct {
    Name string
    Wins int
}
```

# JSON decoding

```
//server_test.go
var got []Player
err := json.NewDecoder(response.Body).Decode(&got)
```

To parse JSON into our data model we create a `Decoder` from `encoding/json` package and then call its `Decode` method. To create a `Decoder` it needs an `io.Reader` to read from which in our case is our response spy's `Body`.