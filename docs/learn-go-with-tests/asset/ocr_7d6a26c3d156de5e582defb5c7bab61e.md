```
{
    "Maps",
    map[string]string{
        "Foo": "Bar",
        "Baz": "Boz",
    },
    []string{"Bar", "Boz"},
},
```

# Try to run the test

```
=== RUN   TestWalk/Maps
--- FAIL: TestWalk/Maps (0.00s)
    reflection_test.go:86: got [], want [Bar Boz]
```

# Write enough code to make it pass

Again if you think a little abstractly you can see that map is very similar to struct, it's just the keys are unknown at compile time.

```
func walk(x interface{}, fn func(input string)) {
    val := getValue(x)

    numberOfValues := 0
    var getField func(int) reflect.Value

    switch val.Kind() {
    case reflect.String:
        fn(val.String())
    case reflect.Struct:
        numberOfValues = val.NumField()
        getField = val.Field
    case reflect.Slice, reflect.Array:
        numberOfValues = val.Len()
        getField = val.Index
    case reflect.Map:
        for _, key := range val.MapKeys() {
            walk(val.MapIndex(key).Interface(), fn)
        }
    }
}
```