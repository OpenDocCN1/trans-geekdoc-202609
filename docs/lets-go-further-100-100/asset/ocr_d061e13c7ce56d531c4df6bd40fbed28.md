```
```json
{"Person":{"name":"Alice","age":21}}
```
```

> **Important**: Take care when using `json.RawMessage` to make sure that the pre-computed value contains valid JSON, otherwise you'll get an error when trying to encode the parent object. If you need to check this at runtime, you can do so by using the `json.Valid()` function.

# The MarshalText fallback

If a type *doesn't* have a `MarshalJSON()` method but *does* have a `MarshalText()` method instead (so that it implements the `encoding.TextMarshaler` interface), then Go will fall back to calling this during JSON encoding and present the result as a JSON string.

For example, if you run the following code:

```
```go
type myFloat float64

func (f myFloat) MarshalText() ([]byte, error) {
    return []byte(fmt.Sprintf("%.2f", f)), nil
}

func main() {
    f := myFloat(1.0/3.0)

    js, err := json.Marshal(f)
}
```
```