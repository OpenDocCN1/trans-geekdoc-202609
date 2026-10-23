```
fmt.Printf("tooShortArray: %v\n", tooShortArray)
fmt.Printf("tooLongArray: %v\n", tooLongArray)
```

Will print out:

```
tooShortArray: [1 2]
tooLongArray: [1 2 3 0]
```

# Partial JSON decoding

If you have a lot of JSON input to process and only need a small part of it, it’s often possible to leverage the json.RawMessage type to help deal with this. For example:

```
// Let's say that the only thing we're interested in is processing the
// "genres" array in
// the following JSON object
js := `{"title": "Top Gun", "genres": ["action", "romance"], "year": 1986}`

// Decode the JSON object to a map[string]json.RawMessage type. The
json.RawMessage
// values in the map will retain their original, un-decoded, JSON values.
var m map[string]json.RawMessage

err := json.NewDecoder(strings.NewReader(js)).Decode(&m)
if err != nil {
    log.Fatal(err)
}

// We can then access the JSON "genres" value from the map and decode it as
```