```
```go
case reflect.Map:
	for _, key := range val.MapKeys() {
		walkValue(val.MapIndex(key))
	}
}
```
```

We've introduced walkValue which DRYs up the calls to walk inside our switch so that they only have to extract out the reflect.Values from val.

# One final problem

Remember that maps in Go do not guarantee order. So your tests will sometimes fail because we assert that the calls to fn are done in a particular order.

To fix this, we'll need to move our assertion with the maps to a new test where we do not care about the order.

```
```go
t.Run("with maps", func(t *testing.T) {
	aMap := map[string]string{
		"Foo": "Bar",
		"Baz": "Boz",
	}

	var got []string
	walk(aMap, func(input string) {
		got = append(got, input)
	})

	assertContains(t, got, "Bar")
	assertContains(t, got, "Boz")
})
```
```

# Here is how assertContains is defined

```
```go
func assertContains(t testing.TB, haystack []string, needle string) t.Helper()
	contains := false
	...
```
```