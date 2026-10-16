```
        total++
    }
} else {
    total++
}
}
    return total
}
```

This is horrible but it does work. It's so bad I felt the need to add comments.

+   - I wanted to be able to look up an integer value for a given roman numeral so I made a type from our array of `RomanNumerals` and then added a method to it, `ValueOf`
+   - Next in our loop we need to look ahead if the string is big enough and *the current symbol is a valid subtractor*. At the moment it's just `I` (1) but can also be `X` (10) or `C` (100).
+     - If it satisfies both of these conditions we need to lookup the value and add it to the total if it is one of the special subtractors, otherwise ignore it
+     - Then we need to further increment `i` so we don't count this symbol twice

# Refactor

I'm not entirely convinced this will be the long-term approach and there's potentially some interesting refactors we could do, but I'll resist that in case our approach is totally wrong. I'd rather make a few more tests pass first and see. For the meantime I made the first `if` statement slightly less horrible.

```
func ConvertToArabic(roman string) int {
    total := 0

    for i := 0; i < len(roman); i++ {
        symbol := roman[i]
```