
# Chapter 3. Strings

```go
p := polar(-83.40, 71.60)
fmt.Printf("%T%v%v\n", p, p)
fmt.Printf("%T%v%t\n", false, false, false)
fmt.Printf("%T%v%d\n", 7607, 7607, 7607)
fmt.Printf("%T%v%f\n", math.E, math.E)
fmt.Printf("%T%v%i\n", 57i, 57i, 57i)
s := "Relativity"
fmt.Printf("%T%v%#q%#q\n", s, s, s, s)
```

| main.polar{-83.4 71.6} | main.polar(radius:-83.4, 0:71.6) | |
| :--- | :--- | :--- |
| bool | false | |
| float64 | 2.7181282849504 | 2.718128 | |
| complex128(5+7i) | 5.000000+7.000000i | |
| string | "Relativity" | "Relativity" |

This example shows how to output an arbitrary value's type and value using %T and %v. If the %v formatting is satisfactory we can simply use fmt.Print() and similar functions. Using the # format verb modifier %v affects only struct types and causes them to be output with their type name and field names. For floating-point values, %v formats like the %v rather than the %f verb. The T format is most useful for debugging and includes the package name (in this case main) for custom types. Using the %q for strings puts them in quotes which is often convenient when debugging.

Two of Go's types have synonyms: byte for uint8 and rune for int32. Use int32 when handling 32-bit signed integers int won't do (e.g., reading/writing binary files), and rune for Unicode code points (characters).

```go
s := Alias~Synonym
chars := [rune](s)
bytes := [byte](s)
fmt.Printf("%T: %v\nT: %v\n", chars, bytes, bytes)
```

```text
[int32: [65 108 105 107 115 8596 83 121 110 111 121 109]
uint8: [65 108 105 107 115 226 134 183 121 110 111 121 109]]
```

As the code snippet illustrates, the %T verb always prints the original type name, not the synonym. Since the string has a non-ASCII character it is clear that we have a slice of runes (code points) and a slice of UTF-8 encoded bytes.

Go can also output any value's address in memory using the %p (pointer) verb.

```go
i := 5
f := -48.3124
```

## 3.5. String Formatting with the Fmt Package

```go
s := "Tomás Bretón"
fmt.Printf("%p -> %d|%p -> %f|#p -> %s\n", &i, i, &f, f, &s)
// 0xf840000030 -> 5|0xf840000308 -> -48.31240|0xf8400001990 -> Tomás Bretón
```

The & of order are explained in the next chapter (4.1, 140). If we use the %p verb with the # modifier, the address’s address 0x is dropped. Outputting memory addresses like this can be useful when debugging.

Go's ability to output slices and maps is also useful for debugging, that is, the type that can be sent and received through the channel and the channel's memory address.

```go
fmt.Println([]float64{math.E, math.Pi, math.Phi})
fmt.Printf("%v\n", []float64{math.E, math.Pi, math.Phi})
fmt.Printf("%#v\n", []float64{math.E, math.Pi, math.Phi})
fmt.Printf("%f\n", []float64{math.E, math.Pi, math.Phi})
```

```text
2.718228285904 3.14192653389793 1.61803398874995
2.718228285904 3.14192653389793 1.61803398874995
[]float64(2.718228285904, 3.14192653389793, 1.61803398874995)
[2.7182 3.14159 3.14159 1.61803]
```

Using the %v verb, slices are output as bracket enclosed sequences of space-separated items. We output them using functions like fmt.Print() or fmt.Sprint(), but if we use a output function then the usual use verb is %v or %v. However, we can also use a type-compatible verb as %f for floating-point numbers or %s for strings.

```go
fmt.Printf("%v\n", []string{"Software patents", "kill", "innovation"})
fmt.Printf("%v\n", []string{"Software patents", "kill", "innovation"})
fmt.Printf("%#v\n", []string{"Software patents", "kill", "innovation"})
fmt.Printf("%7s\n", []string{"Software patents", "kill", "innovation"})
```

```text
"Software patents" "kill" "innovation"
[Software patents kill innovation]
[string[]Software patents", "kill", "innovation"]
[ Software patents ·········kill ···········innovation]
```

Using the %v verb for outputting slices of strings is particularly useful when the strings contain spaces since it makes each string identifiable—something that doesn’t happen if we use the %v verb. The last output might look wrong at first sight it occupies 53 characters (not including brackets) rather than three strings. The apparent discrepancy is due to the space separator between each slice item.

In addition to debugging, the %#v verb may be useful when generating Go programmatically.

```go
fmt.Printf("%v\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%v\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%d\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%v\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%0b\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
```

```text
map[int]string{1: "A", 2: "B", 3: "C", 4: "D"}
map[int]string{1: "A", 2: "B", 3: "C", 4: "D"}
map[int]string{1: "A", 2: "B", 3: "C", 4: "D"}
map[int]string{1: "A", 2: "B", 3: "C", 4: "D"}
map[int]string{1: "A", 2: "B", 3: "C", 4: "D"}
```

Maps are output as the "map", and then the map's key-value pairs (in arbitrary order since maps are unordered). Just as slices it is possible to use verbs other than %v—but only if both the key and value are compatible with the verb used, as we saw in the example (Maps and slices are covered in detail in Chapter 4).

## 3.6. Other Packages

Go's considerable support for strings doesn't stop at indexing and slicing. The strings package in particular provides very rich functionality, the strconv, utf8, and unicode packages also provide lots of useful functions. Examples that make use of functionality from all these packages are presented in this section. There are other packages in the standard library that provide string-related functionality, and some of them are covered elsewhere in the book or in exercises.

### 3.6.1. The Strings Package

A common requirement in string processing is to be able to split a string into a slice of strings and then do further processing—for example convert strings to numbers or trim whitespace. To get favor of how to use some of the strings package's functions we will review some tiny examples that show. All package's functions are listed in Tables 3.6 and 3.7. Let's start with splitting strings.

```go
names := "Nicolò,Noël,José"
fmt.Print("")
for _, name := range strings.Split(names, ",") {
	fmt.Printf("%s|", name)
}
fmt.Println("")
```

```text
[Nicolò|Noël|José|
```

We have a bullet-separated list of names (including one blank field) which we split using the strings.Split() function. This function takes a string to split and a separator to split on and does as many splits as possible (If we want to limit the number of splits we can use the strings.SplitN() function instead.) If used the strings.SplitAfter() function the output would look like this:

```text
Nicolò,|Noël,|José,|
```

The strings.SplitAfter() function performs the same splits as the strings.Split() function but keeps the separator. There is also a strings.SplitN() function when we want to split a specific number of times. If we need to be able to split on any of two or different characters we can use the strings.FieldsFunc() function.

```go
for _, record := range string{"László Lajtha", "Edouard La", "José Angel Lamas"} {
	fmt.Println(strings.FieldsFunc(record, func(char rune) bool {
		switch char {
		case ',', '*', '|':
				return true
		}
		return false
	}))
}
```

## Table 3.6 The Strings Package's Functions

Variables s and t are of type string, xs is of type []string, i is of type int, and f is a function with the signature func(rune) bool. Index positions are of the first UTF-8 byte of the matching Unicode code point (character) or -1 when there isn't a match.

| Syntax | Description/result |
| :--- | :--- |
| strings.Contains(s, t) | true if t occurs in s |
| strings.Count(s, t) | How many (nonoverlapping) times t occurs in s |
| strings.EqualFold(s, t) | true if the strings are case-insensitively equal |
| strings.Fields(s) | The []string that results in splitting s on white-space |
| strings.FieldsFunc(s, f) | The []string that results in splitting s at every character where f returns true |
| strings.HasPrefix(s, t) | true if s starts with t |
| strings.HasSuffix(s, t) | true if s ends with t |
| strings.Index(s, t) | the index of the first occurrence of t in s |
| strings.IndexAny(s, t) | the first index in s of any character that is in t |
| strings.IndexFunc(s, f) | the index of the first occurrence of char for which f returns true |
| strings.IndexRune(s, char) | the index of the first occurrence of character char of rune in s |
| strings.Join(xs, t) | A string containing the concatenation of all the strings in xs, each separated by t (which can be "") |
| strings.LastIndex(s, t) | the index of the last occurrence of t in s |
| strings.LastAny(s, t) | the last index in s of any character that is in t |
| strings.LastIndexFunc(s, f) | the index of the last character in s for which f returns true |
| strings.Map(mf, t) | A copy of t with every character replaced or deleted according to the mapping function mf with the signature func(rune) rune (see text) |
| strings.NewReader(s) | A pointer to a value that provides Read(), Byte(), and Rune() methods that operate on s |
| strings.NewReplacer(...) | A pointer to a value that has methods for replacing each pair of old, new strings it is given |
| strings.Repeat(s, i) | A string consisting of i concatenations of s |
