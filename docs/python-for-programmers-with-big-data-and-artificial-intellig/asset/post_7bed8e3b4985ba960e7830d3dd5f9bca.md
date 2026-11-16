
Click here to view code image

```
In [3]: '{0} {0} {1}'.format('Happy', 'Birthday')
Out[3]: 'Happy Happy Birthday'
```

Note that we used the position number 0 ('Happy') twice—you can reference each argument as often as you like and in any order.

### Referencing Keyword Arguments

You can reference keyword arguments by their keys in the placeholders:

Click here to view code image

```
In [4]: '{first} {last}'.format(first='Amanda', last='Gray')
Out[4]: 'Amanda Gray'

In [5]: '{last} {first}'.format(first='Amanda', last='Gray')
Out[5]: 'Gray Amanda'
```

## 8.3 CONCATENATING AND REPEATING STRINGS

In earlier chapters, we used the + operator to concatenate strings and the * operator to repeat strings. You also can perform these operations with augmented assignments. Strings are immutable, so each operation assigns a new string object to the variable:

Click here to view code image

```
In [1]: s1 = 'happy'

In [2]: s2 = 'birthday'

In [3]: s1 += ' ' + s2

In [4]: s1
Out[4]: 'happy birthday'

In [5]: symbol = '>'

In [6]: symbol *= 5

In [7]: symbol
Out[7]: '>>>>>'
```

## 8.4 STRIPPING WHITESPACE FROM STRINGS

There are several string methods for removing whitespace from the ends of a string. Each returns a new string leaving the original unmodified. Strings are immutable, so each method that appears to modify a string returns a new one.

### Removing Leading and Trailing Whitespace

Let's use string method `strip` to remove the leading and trailing whitespace from a string:

Click here to view code image

```
In [1]: sentence = '\t \n This is a test string. \t\t \n'
In [2]: sentence.strip()
Out[2]: 'This is a test string.'
```

### Removing Leading Whitespace

Method `lstrip` removes only leading whitespace:

Click here to view code image

```
In [3]: sentence.lstrip()
Out[3]: 'This is a test string. \t\t \n'
```

### Removing Trailing Whitespace

Method `rstrip` removes only trailing whitespace:

Click here to view code image

```
In [4]: sentence.rstrip()
Out[4]: '\t \n This is a test string.'
```

As the outputs demonstrate, these methods remove all kinds of whitespace, including spaces, newlines and tabs.

## 8.5 CHANGING CHARACTER CASE

In earlier chapters, you used string methods `lower` and `upper` to convert strings to all lowercase or all uppercase letters. You also can change a string’s capitalization with methods capitalize and title.

### Capitalizing Only a String’s First Character

Method capitalize copies the original string and returns a new string with only the first letter capitalized (this is sometimes called sentence capitalization):

Click here to view code image

```
In [1]: 'happy birthday'.capitalize()
Out[1]: 'Happy birthday'
```

### Capitalizing the First Character of Every Word in a String

Method title copies the original string and returns a new string with only the first character of each word capitalized (this is sometimes called book-title capitalization):

Click here to view code image

```
In [2]: 'strings: a deeper look'.title()
Out[2]: 'Strings: A Deeper Look'
```

## 8.6 COMPARISON OPERATORS FOR STRINGS

Strings may be compared with the comparison operators. Recall that strings are compared based on their underlying integer numeric values. So uppercase letters compare as less than lowercase letters because uppercase letters have lower integer values. For example, 'A' is 65 and 'a' is 97. You’ve seen that you can check character codes with ord:

Click here to view code image

```
In [1]: print(f'A: {ord("A")}; a: {ord("a")}')
A: 65; a: 97
```

Let’s compare the strings 'Orange' and 'orange' using the comparison operators:

Click here to view code image

```
In [2]: 'Orange' == 'orange'
Out[2]: False

In [3]: 'Orange' != 'orange'
Out[3]: True

In [4]: 'Orange' < 'orange'
Out[4]: True

In [5]: 'Orange' <= 'orange'
Out[5]: True

In [6]: 'Orange' > 'orange'
Out[6]: False

In [7]: 'Orange' >= 'orange'
Out[7]: False
```

## 8.7 SEARCHING FOR SUBSTRINGS

You can search in a string for one or more adjacent characters—known as a _substring_—to count the number of occurrences, determine whether a string contains a substring, or determine the index at which a substring resides in a string. Each method shown in this section compares characters lexicographically using their underlying numeric values.

### Counting Occurrences

String method `count` returns the number of times its argument occurs in the string on which the method is called:

Click here to view code image

```
In [1]: sentence = 'to be or not to   be that is the question'

In [2]: sentence.count('to')
Out[2]: 2
```

If you specify as the second argument a `start_index`, `count` searches only the slice `string[start_index:]` —that is, from `start_index` through end of the string:

Click here to view code image

```
In [3]: sentence.count('to', 12)
Out[3]: 1
```

If you specify as the second and third arguments the *start_index* and *end_index*, `count` searches only the slice *string*[*start_index*:*end_index*]—that is, from *start_index* up to, but not including, *end_index*:

Click here to view code image

```
In [4]: sentence.count('that', 12, 25)
Out[4]: 1
```

Like `count`, each of the other string methods presented in this section has *start_index* and *end_index* arguments for searching only a slice of the original string.

### Locating a Substring in a String

String method `index` searches for a substring within a string and returns the first index at which the substring is found; otherwise, a `ValueError` occurs:

Click here to view code image

```
In [5]: sentence.index('be')
Out[5]: 3
```

String method `rindex` performs the same operation as `index`, but searches from the end of the string and returns the *last* index at which the substring is found; otherwise, a `ValueError` occurs:

Click here to view code image

```
In [6]: sentence.rindex('be')
Out[6]: 16
```

String methods `find` and `rfind` perform the same tasks as `index` and `rindex` but, if the substring is not found, return -1 rather than causing a `ValueError`.

### Determining Whether a String Contains a Substring

If you need to know only whether a string contains a substring, use operator `in` or `not in`:

Click here to view code image

```
In [7]: 'that' in sentence
Out[7]: True

In [8]: 'THAT' in sentence
Out[8]: False

In [9]: 'THAT' not in sentence
Out[9]: True
```

### Locating a Substring at the Beginning or End of a String

String methods startswith and endswith return True if the string starts with or ends with a specified substring:

Click here to view code image

```
In [10]: sentence.startswith('to')
Out[10]: True

In [11]: sentence.startswith('be')
Out[11]: False

In [12]: sentence.endswith('question')
Out[12]: True

In [13]: sentence.endswith('quest')
Out[13]: False
```

## 8.8 REPLACING SUBSTRINGS

A common text manipulation is to locate a substring and replace its value. Method replace takes two substrings. It searches a string for the substring in its first argument and replaces each occurrence with the substring in its second argument. The method returns a new string containing the results. Let's replace tab characters with commas:

Click here to view code image

```
In [1]: values = '1\t2\t3\t4\t5'

In [2]: values.replace('\t', ',')
Out[2]: '1,2,3,4,5'
```

Method replace can receive an optional third argument specifying the maximum number of replacements to perform.

## 8.9 SPLITTING AND JOINING STRINGS

When you read a sentence, your brain breaks it into individual words, or **tokens**, each of which conveys meaning. Interpreters like IPython tokenize statements, breaking them into individual components such as keywords, identifiers, operators and other elements of a programming language. Tokens typically are separated by whitespace characters such as blank, tab and newline, though other characters may be used—the separators are known as **delimiters**.

### Splitting Strings

We showed previously that string method `split` with _no_ arguments tokenizes a string by breaking it into substrings at each whitespace character, then returns a list of tokens. To tokenize a string at a custom delimiter (such as each comma-and-space pair), specify the delimiter string (such as, ', ', ) that `split` uses to tokenize the string:

![](img/34b7fc2f1ee27beb73bca14927d42340_320_0.png)

```
In [1]: letters = 'A, B, C, D'

In [2]: letters.split(', ')
Out[2]: ['A', 'B', 'C', 'D']
```

If you provide an integer as the second argument, it specifies the maximum number of splits. The last token is the remainder of the string after the maximum number of splits:

![](img/34b7fc2f1ee27beb73bca14927d42340_320_1.png)

```
In [3]: letters.split(', ', 2)
Out[3]: ['A', 'B', 'C, D']
```

There is also an `rsplit` method that performs the same task as `split` but processes the maximum number of splits from the end of the string toward the beginning.

### Joining Strings

String method `join` concatenates the strings in its argument, which must be an iterable containing only string values; otherwise, a `TypeError` occurs. The separator between the concatenated items is the string on which you call `join`. The following
