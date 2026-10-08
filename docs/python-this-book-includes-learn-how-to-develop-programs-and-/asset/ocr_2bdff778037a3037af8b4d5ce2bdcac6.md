then apply a loop to check every character within a sequence to “create” the new String. For example:
word = "hello"
newword = ""
for c in word:
if c ===='e' or c == 'o':
newword += "_"
else:
newword += c

# String Functions

So far you know several functions that you can use with strings.
For instance, the len () function can count the number of characters in a string.
Besides that, there are other functions that you can apply when you work
With Strings to simplify things for you as a developer.

# Determining the Largest and Smallest Character within a String

You can use Python built in functions to calculate the largest and smallest
characters inside a string. For example:

```
a = max("python")
b = min("python")
print("max:", a)
print("min:", b)
>> y
>> h
```

# String Slicing Notation

For Python to cut a string you must use a bracket symbol to define the index
range of the characters you want.
The standard notation for the following syntax includes:
`substring = bigstring[start:end:step]`nYou need to include at least an index value.

Substring properties comprises all the characters at the start value and
continue to the ending value.
Eliminating a starting index value will trigger Python to assume that you
want to begin at the start of the string or you want to proceed slicing the last
section of the string. This should resemble the function range.