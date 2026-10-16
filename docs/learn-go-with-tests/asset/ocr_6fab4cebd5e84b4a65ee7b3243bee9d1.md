```
dictionary.Delete(word)

    _, err := dictionary.Search(word)
    if err != ErrNotFound {
        t.Errorf("Expected %q to be deleted", word)
    }
}
```

Our test creates a Dictionary with a word and then checks if the word has been removed.

# Try to run the test

By running go test we get:

```
./dictionary_test.go:74:6:  dictionary.Delete  undefined  (type Dictionary has no field or method Delete)
```

# Write the minimal amount of code for the test to run and check the failing test output

```
func (d Dictionary) Delete(word string) {

}
```

After we add this, the test tells us we are not deleting the word.

```
dictionary_test.go:78: Expected 'test' to be deleted
```

# Write enough code to make it pass

```
func (d Dictionary) Delete(word string) {
    delete(d, word)
}
```