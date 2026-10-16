```
}
    return "I"
}
```

# Refactor

OK so I'm starting to not enjoy these if statements and if you look at the code hard enough you can see that we're building a string of I based on the size of arabic.

We "know" that for more complicated numbers we will be doing some kind of arithmetic and string concatenation.

Let's try a refactor with these thoughts in mind, it might not be suitable for the end solution but that's OK. We can always throw our code away and start afresh with the tests we have to guide us.

```
func ConvertToRoman (arabic int) string {
    var result strings.Builder
    for i := 0; i < arabic; i++ {
        result.WriteString("I")
    }
    return result.String()
}
```

You may not have used strings.Builder before

A Builder is used to efficiently build a string using Write methods. It minimizes memory copying.

Normally I wouldn't bother with such optimisations until I have an actual performance problem but the amount of code is not much larger than a "manual" appending on a string so we may as well use the faster approach.