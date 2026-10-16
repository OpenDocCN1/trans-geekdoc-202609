In dictionary_test.go:

```
```go
func TestSearch(t *testing.T) {
    dictionary := Dictionary{"test": "this is just a test"}

    got := dictionary.Search("test")
    want := "this is just a test"

    assertStrings(t, got, want)
}
```
```

We started using the Dictionary type, which we have not defined yet. Then called Search on the Dictionary instance.

We did not need to change assertStrings.

In dictionary.go:

```
```go
type Dictionary map[string]string

func (d Dictionary) Search(word string) string {
    return d[word]
}
```
```

Here we created a Dictionary type which acts as a thin wrapper around map. With the custom type defined, we can create the Search method.

# Write the test first

The basic search was very easy to implement, but what will happen if we supply a word that's not in our dictionary?

We actually get nothing back. This is good because the program can continue to run, but there is a better approach. The function can report that the word is not in the dictionary. This way, the user isn't left wondering if the word doesn't exist or if there is just no definition