# 258 Chapter 6. Object-Oriented Programming

```
if unicode.Is(unicode.Terminal_Punctuation, char) {
    return -1
}
processPhrases(phrases, removePunctuation)
```

We have created an anonymous function that matches the RuneForRune signature and passed it to the custom processPhrases() function.

```
func processPhrases(phrases []string, function RuneForRuneFunc) {
    for _, phrase := range phrases {
        fmt.Println(strings.Map(function, phrase))
    }
}
```

Day dusk and night
All day long

Using RuneForRuneFunc as a type rather than the underlying func(rune) rune is more meaningful for human readers; it also provides abstraction. (The strings.Map() function was covered in Chapter 3 ◄)

Creating custom types based on built-in types or function signatures can be useful, but doesn't get us far. What we need are custom methods, and the subject of the next subsection.

# 6.2.1. Adding Methods

A method is a special kind of function that is called on a value of a custom type and that is (usually) passed as a pointer or value depending on how the method is defined. The syntax for defining methods is almost identical to defining functions, except that between the func keyword and the method's name we must write the receiver—this is written in parentheses, either as the type of value that the method belongs to or as a variable and the name. When the method is called, the receiver's variable (if present) is automatically set to the value or pointer that the method was called on.

We can add one or more methods to any custom type. A method's receiver is always a value of the type or a pointer to a value of the type. However, every method name must be unique for any given type. One consequence of the name requirement is that we cannot have two methods of the same name where one takes a pointer and the other a value. Another consequence is that there is no support for overloaded methods, that is, methods with the same name but different signatures. One way to provide the equivalent of overloaded