# 9.1.1.3. Unit Testing and Benchmarking Packages

The Go standard library includes good support for unit testing the packages. Setting up unit testing for a package is a simple matter of creating a test file in the same directory as the package we want to test. This file should begin with the package name and end with _test.go. For example, the omap package's test file is called omap_test.go.

In the book's examples, test files are put in their own unique package (e.g., omap_test), and they import the package they are testing and the testing package, plus any other packages that are needed. This constrains us to use black testing. However, some Go programmers prefer white box testing. This can be easily done by putting test files in the same package as they are testing (e.g., omap), in which case there is no need to import the package being tested. This approach means that nonexported types can be tested, and methods can be added to support testing.

The test file is unusual in that it has no main() function. Instead, it has one or more exported functions whose names contain Test and take a single argument of type *testing.T and return nothing. We can add any supporting functions we need, of course, providing their names start with Test.

```
func TestStringKeyOmapInsertion(t *testing.T) {
	word := omap.NewCaseFoldedKey()
	for _, word := range []string{"one", "Two", "THREE", "four", "Five"}{
		word.Insert(word, word)
	}
	var words []string
	word.Do(func(_, value interface{}) {
		words = append(words, value.(string))
	})
	actual, expected := strings.Join(words, ""), "FivefourTHwo"
	if actual != expected {
		t.Error("%q != %q", actual, expected)
	}
}
```

Here is one of the tests in the omap_test.go file. It begins by creating an empty omap.Map, then it inserts some string keys (which are treated case-insensitively), and string values. We then iterate over all the key-value pairs in the map using the Map.Do method, and append each value to a slice of strings. We join the strings into a single string and see if this matches what we expect. If the match fails we call the testing.T.Error method to report the failure and provide some explanation. If no error or function is called then the test is assumed to have passed.