```
func isSubtractive(symbol uint8) bool {
	return symbol == 'I' || symbol == 'X' || symbol == 'C'
}
```

My main problem with the previous code is similar to our refactor from earlier. We had too many concerns coupled together. We wrote an algorithm which was trying to extract Roman Numerals from a string and then find their values.

So I created a new type windowedRoman which took care of extracting the numerals, offering a Symbols method to retrieve them as a slice. This meant our ConvertToArabic function could simply iterate over the symbols and total them.

I broke the code down a bit by extracting some functions, especially around the wonky if statement to figure out if the symbol we are currently dealing with is a two character subtractive symbol.

There's probably a more elegant way but I'm not going to sweat it. The code is there and it works and it is tested. If I (or anyone else) finds a better way they can safely change it - the hard work is done.

# An intro to property based tests

There have been a few rules in the domain of Roman Numerals that we have worked with in this chapter

+   - Can't have more than 3 consecutive symbols
+   - Only I (1), X (10) and C (100) can be "substractors"
+   - Taking the result of ConvertToRoman(N) and passing it to ConvertToArabic should return us N

The tests we have written so far can be described as "example" based tests where we provide the tooling some examples around our code to verify.