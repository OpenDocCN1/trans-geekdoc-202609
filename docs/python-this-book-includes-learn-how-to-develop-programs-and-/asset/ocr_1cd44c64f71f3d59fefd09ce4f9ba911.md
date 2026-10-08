```
word = "Craig"
newword = word.lower()
print (word)
>> craig
```

# Searching and Replacing

Programs usually need to search and substitute functions on data, same as “find and replace” functionality that is found in your word processor.
Strings can be searched for strings and substrings with the help of find () index () methods.

The find method returns -1 in case the substring isn’t found.
The index () returns an error in case the substring isn’t found.

# Searching a Specific Section of a String

Both the find () and index () methods search from the start of the string, and determine the occurrence of the substring.
You can also define a start and ending index to only check a portion of the string.

# How to Search Backwards Through a String

Both the index() and rfind() methods work the same as find() and index(), except the string is searched backwards from the end of the string.

# Centering Text

s.center(w, [pad]) centers the text within a field of width w.
The optional pad character will be included to the ends of the string.

# Concatenation

You can concatenate strings using the + operator.
>>> ‘welcome’ + ‘home'
‘welcomehome'

# Join Method

Strings too have a join () method.

# Multiplications

Strings even be multiplied by integers.
>>> ‘ship’ * 5

# Methods of Extracting Information About a String

s.count(ss)- this counts the number of times of substring ss
s.endswith(sfx)- this confirms whether a string ends with the substring sfx.