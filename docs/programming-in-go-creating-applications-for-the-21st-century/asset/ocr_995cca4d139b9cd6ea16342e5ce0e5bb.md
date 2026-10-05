# 112

# Chapter 3. Strings

```
asciiOnly := func(char rune) rune {
    if char > 127 {
        return '?'
    }
    return char
}
fmt.Println(strings.Map(asciiOnly, "Jérôme Österreich\))
```

Here, instead of example creating the mapping function at the call site as we did with the strings.FieldsFunc shown earlier (◄), we have created an anonymous mapping function and assigned (a reference to) to a variable (asciiOnly). We have then used the strings.Map function, passing the variable that refers to the mapping function and the string we want to process and printing the result—a string with all non-ASCII characters replaced by “?”. We, of course, have created the mapping function at the call site, but doing it separately as we have done here is more convenient if the function being passed is long, or if we will need to use it more once.

It is easy to use this approach to delete non-ASCII characters and produce:

```
Jrme_sterreich
```

This is achieved by changing the mapping function to return -1 instead of ? for non-ASCII characters.

We have mentioned previously that it is possible to iterate over every character (Unicode code point) in a string using a for ... range loop ($5.3, ► 203). A similar effect can be achieved when reading data from types that implement the ReadRun() function, such as the bufio.Reader.

```
for {
    char, size, err := reader.ReadRun()
    if err != nil { // might occur if the reader is reading a file
        if err == io.EOF { // finished without incident
            break
        }
        panic(err) // a problem occurred
    }
    fmt.Printf("%U '%c' %d: %X\n", char, size, []byte(string(char)))
}
```