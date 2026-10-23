Will encode to an empty JSON object like this:

```
{}
```

# Using omitempty on a zero-value time.Time doesn’t work

Using omitempty on a zero-value time.Time field won’t hide it in the JSON object. This is because the time.Time type is a struct behind the scenes and, as mentioned above, omitempty never considers structs to be empty. Instead, the string "0001-01-01T00:00:00Z" will appear in the JSON (which is the value returned by calling the MarshalJSON() method on a zero-value time.Time). For example, the following struct:

```
s := struct {
    Foo time.Time `json:",omitempty"`
}{}
```

Will encode to the JSON:

```
{"Foo":"0001-01-01T00:00:00Z"}
```