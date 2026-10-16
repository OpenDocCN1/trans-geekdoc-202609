Now we can easily add a scenario to see what happens if we have more than one string field.

# Write the test first

Add the following scenario to the `cases`.

```
{
    "Struct with two string fields",
    struct {
        Name string
        City string
    }{"Chris", "London"},
    []string{"Chris", "London"},
}
```

# Try to run the test

```
=== RUN   TestWalk/Struct_with_two_string_fields
--- FAIL: TestWalk/Struct_with_two_string_fields (0.00s)
    reflection_test.go:40: got [Chris], want [Chris London]
```

# Write enough code to make it pass

```
func walk(x interface{}, fn func(input string)) {
    val := reflect.ValueOf(x)

    for i := 0; i < val.NumField(); i++ {
        field := val.Field(i)
        fn(field.String())
    }
}
```