# Maps

You can find all the code for this chapter here

In arrays & slices, you saw how to store values in order. Now, we will look at a way to store items by a key and look them up quickly.

Maps allow you to store items in a manner similar to a dictionary. You can think of the key as the word and the value as the definition. And what better way is there to learn about Maps than to build our own dictionary?

First, assuming we already have some words with their definitions in the dictionary, if we search for a word, it should return the definition of it.

# Write the test first

In dictionary_test.go

```
```go
package main

import "testing"

func TestSearch(t *testing.T) {
    dictionary := map[string]string{"test": "this is just a test
    got := Search(dictionary, "test")
    want := "this is just a test"

    if got != want {
        t.Errorf("got %q want %q given, %q", got, want, "test")
    }
}
```
```