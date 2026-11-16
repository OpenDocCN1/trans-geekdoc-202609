word must have an initial capital letter.

+   ' , e-mail : ' contains literal characters that match themselves.

+   (\w+@\w+\.\w{3}) matches a simple e-mail address consisting of one or more alphanumeric characters (\w+), the @ character, one or more alphanumeric characters (\w+), a dot (\.) and three alphanumeric characters (\w{3}). We preceded the dot with \\ because a dot (.) is a regular expression metacharacter that matches one character.

The match object's groups method returns a tuple of the captured substrings:

lick here to view code image

```
```
In [22]: result.groups()
Out[22]: ('Charlie Cyan', 'demo1@deitel.com')
```
```

The match object's group method returns the entire match as a single string:

lick here to view code image

```
```
In [23]: result.group()
Out[23]: 'Charlie Cyan, e-mail: demo1@deitel.com'
```
```

You can access each captured substring by passing an integer to the group method. The captured substrings are numbered from 1 (unlike list indices, which start at 0):

lick here to view code image

```
```
In [24]: result.group(1)
Out[24]: 'Charlie Cyan'

In [25]: result.group(2)
Out[25]: 'demo1@deitel.com'
```
```

# 8.13 INTRO TO DATA SCIENCE: PANDAS, REGULAR EXPRESSIONS AND DATA MUNGING

Data does not always come in forms ready for analysis. It could, for example, be in the wrong format, incorrect or even missing. Industry experience has shown that data