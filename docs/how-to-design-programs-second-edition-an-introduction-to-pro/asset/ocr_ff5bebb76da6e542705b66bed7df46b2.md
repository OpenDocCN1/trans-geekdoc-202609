where the "\n" inside the string indicates line breaks.

The dots aren't really a part of the result, as you probably guessed.

While it is indeed possible to break apart this string with primitive operations on strings, for example, explode, most programming languages—including BSL —support many different representations of files and functions that create such representations from existing files:

+   One way to represent this file is as a list of lines, where each line is represented as one string:

```
(cons "TTT"
  (cons ""
    (cons "Put up in a place"
      (cons ...
        '())))))
```

Here the second item of the list is the empty string because the file contains an empty line.

+   Another way is to use a list of words, again each word represented as a string:

```
(cons "TTT"
  (cons "Put"
    (cons "up"
      (cons "in"
        (cons ...
          '())))))
```

Note how the empty second line disappears with this representation. After all, there are no words on the empty line.

+   And a third representation relies on lists of lists of words: