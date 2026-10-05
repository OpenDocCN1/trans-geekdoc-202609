
## 5.6. Custom Functions

two lines for each additional else if clause; and for the switch version we would need to add one extra line for every new case (or two lines if we format our cases with gofmt). If the function was for a file manager it could easily be required to handle handles of suffixes, making the function very long indeed.

```go
var FunctionForSuffix = map[string]func(string) (string, error) {
    ".gz": ZipFileList, ".tar": TarFileList, ".tar.gz": TarFileList,
    ".tgz": TarFileList, ".zip": ZipFileList}
func ArchiveFileListMap(file string) ([string, error) {
    if function, ok := FunctionForSuffix(Suffix(file)); ok {
        return function(file)
    }
    return nil, errors.New("unrecognized archive")
}
```

This version of the function uses a map whose keys are strings (file suffixes), and whose values are functions with the signature func(string) ([string, error). (All of the custom functions, ZipFileList(), TarFileList(), and ZipFileList(), are of this type)

The function uses the index operator to retrieve the function that matches the given suffix and set ok to true; or return nil and false if the suffix isn't a map key. If there is a matching function the function is called with the filename, and its results returned.

This function is more scalable than using an if or switch statement since how many file suffix-items we add to the FunctionForSuffix map, the function remains unchanged. And unlike a big or switch statement, map lookup speeds wont really degrade as the number of items increases\*. In addition, using a map in this way can make things clearer and also makes it possible to add new items to the map dynamically.

### 5.6.5.2. Dynamic Function Creation

Another scenario involves choosing a function at runtime when we have two or more functions that implement the same functionality using different algorithms and we don't want to commit to any of them when the program is compiled (e.g., to allow us to choose dynamically for benchmarking or regression testing).

For example we use strings that contain only 7-bit ASCII characters to write a much simpler version of the IsPalindrome() function we saw earlier (229 ◄), and at runtime create only the version that program actually needs.

> * On a lightly loaded AMD-6 quad-core 3GHz machine we found that using a map was consistently faster than a switch once there were 50 or more cases to consider.

## 232 Chapter 5. Procedural Programming

One way to do this is to declare a package-level variable with the function's signature and to create the appropriate function in an init() function.

```go
var IsPalindrome func(string) bool // Holds a reference to a function
func init() {
	if len(os.Args) > 1 &&
		os.Args[1] == "-a" || os.Args[1] == "-ascii" {
		os.Args = append(os.Args[:1], os.Args[2:]...) // Strip out arg.
		isPalindrome = func(s string) bool { // Simple ASCII-only version
		if len(s) < 1 {
			return true
		}
			if s[0] != s[len(s)-1] {
			return false
		}
		return IsPalindrome(s[1 : len(s)-1])
	}
	} else {
		isPalindrome = func(s string) bool { // UTF-8 version
		// ... same as earlier ...
	}
}
```

We have made the choice of IsPalindrome() implementation dependent on a command-line argument. If the argument is given, we strip it out of the os.Args slice (so the rest of the program doesn't have to know or care about it), and create a 7-bit ASCII version of the IsPalindrome() function. The stripping out is slightly subtle when we use os.Args to have its first string and its third and subsequent strings but not its second (string "-a" or "-ascii"). We can't use os.Args[0] in the append() call because the first argument must be a slice, so we use os.Args[:1] as a one-item slice containing os.Args ($4.2.1, 153). If the ASCII argument is not present, we create the same version as we saw earlier that works correctly on both 7-bit ASCII and UTF-8 Unicode strings. The rest of the program the IsPalindrome() function can be called normally, but the actual code gets executed will vary depending on which version was created. (The source code for this example is in palindrome/palindrome.go.)

## 5.6.6. Generic Functions

Earlier in the chapter we created a function for finding the smallest of the int arguments it was passed (221 ◄). The algorithm used in that function could also be applied to other numeric types, or to strings, since it works for any type that supports the < operator. In C++, for cases like this, we would create a generic function that is parameterized by type which would result in the compiler creating as many versions of the function as we need (i.e., one per type used). In Go, at the time of this writing, there is no support for type parameterization, so to get the same effect as C++ achieves we must manually create the functions we need (e.g., MinimumInt(), MinimumFloat(), MinimumString()). This way we end up with one function per type used (just like C++), that in Go each function must have a unique name).

Go offers various alternative approaches that avoid the need to create functions that they operate on, at the cost of some runtime efficiency. For small functions that are not used often or are fast enough, the alternative approaches can be convenient. Here are examples of how a generic Minimum() function:

```go
i := Minimum(4, 3, 8, 2)
fmt.Printf("%T v\n", i)
f := Minimum(9, 5.4, 17, 3.8)
fmt.Printf("%T v\n", f)
s := Minimum("K", "B", "C", "D")
fmt.Printf("%T v\n", s)
```

The function returns a value of type interface{}, which we convert to the built-in type we expect using an unchecked assertion (§5.1.2, 191).

```go
func Minimum(first interface{}, rest ...interface{}) interface{} {
  minimum := first
  for _, x := range rest {
    switch x := x.(type) {
    case int:
      if x < minimum.(int) {
        minimum = x
      }
    case float64:
      if x < minimum.(float64) {
        minimum = x
      }
    case string:
      if x < minimum.(string) {
        minimum = x
      }
    }
  }
  return minimum
}
```

This function takes at least one value (first) and zero or more values (rest). We use the interface{} type since it can be used for any type. We initially assume that the first value is the smallest and then iterate over the rest of the values. Whenever we find a value smaller than the current minimum we select it as the value—as an interface{}, hence the need to convert it to a built-in type using an unchecked assertion. We still have duplicate code—in each case's block—but if there were a lot of duplicate code we simply set a Boolean in each case (e.g., change = true), and then follow with an if statement that contained all the common code. Clearly, using this Minimum() function is less efficient than type-specific functions. However, it is worth knowing the technique because it is useful for cases where the overhead and conversion inconvenience are outweighed by the advantage of having to define the function only once.

The problem of duplicate code within a generic function isn't so easy to work around unless one or more of the interface{} arguments are actually slices. For example, here is a function that, given a slice and an item of the same type as the slice's items, returns the index position of the first occurrence of the item in the slice—or -1 if the item isn't in the slice.

```go
func Index(xs interface{}, x interface{}) int {
	switch slice := xs.(type) {
	case []int:
	for i, y := range slice {
		if y == x.(int) {
			return i
		}
		}
	case []string:
	for i, y := range slice {
		if y == x.(string) {
			return i
		}
		}
	}
	return -1
}
```

We have only bothered to implement the int and string cases—both of which contain essentially the same code. Here is an example of the Index() function in use and the output it produces (The code is taken from contains/main.go test program.).

```go
xs := []int{2, 4, 6, 8}
fmt.Printf("5@%d, 6@%d\n", Index(xs, 5), Index(xs, 6))
ys := []string{"C", "B", "K", "A"}
fmt.Printf("Z@%d, A@%d\n", Index(ys, "Z"), Index(ys, "A"))
// Output:
// 5@1 6@2
// Z@1 A@3
```

What we need to be able to do is treat the slice generically—that way we could have just one loop and the type-specific testing inside. Here is a function that handles this—and it produces the same output as the above code snippet if we replace calls to Index() with IndexReflect().

```go
func IndexReflect(xs interface{}, x interface{}) int { // Long-winged way
	if slice := reflect.ValueOf(xs); slice.Kind() == reflect.Slice {
		for i := 0; i < slice.Len(); i++ {
			switch y := slice.Index(i).Interface().(type) {
			case int:
				if y == x.(int) {
					return i
				}
			case string:
				if y == x.(string) {
					return i
				}
			}
		}
	}
	return -1
}
```

The function begins by using Go's reflection support (provided by the reflect package; 9.4.9, ➤ 427), to convert the xs interface{} into a slice-typed reflect.Value. Such values provide the methods we need to traverse the slice's items and to extract any items we are interested in. Here, we access each item in turn and use the reflect.Value.Interface() function to pull out the value as an interface{} which we immediately assign to y inside a type switch.
