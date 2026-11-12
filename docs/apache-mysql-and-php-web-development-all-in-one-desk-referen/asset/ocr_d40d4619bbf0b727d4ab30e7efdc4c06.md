+   * repeat
+   * tolower, touper, totitle
+   * trim, trimleft, trimright

# ## map

The map command replaces characters and strings with other characters and strings. Here's an interactive example:

```
% string map {a A b B} "There's a bear in my house"
There's A BeAr in my house
```

You enter the information you want to replace inside curly braces and use spaces to divide each item. In this example, each a gets replaced with an A, and each b gets replaced with a B. You can see in the output that those characters did get replaced.

Here's an example that's a bit more interesting:

```
set mymap (Monday Montag Tuesday Dienstag Wednesday Mittwoch)
set mystring "Today is Monday, tomorrow is Tuesday!"
set result [string map $mymap $mystring]
puts $result
set mystring2 "And then comes Wednesday!"
set result2 [string map $mymap $mystring2]
puts $result2
```

This example replaces three English words with their German counterparts. The first line sets up a map, which is really just a list. The first item in the list is Monday, and that maps to the second item, which is Montag (the German word for Monday). Next I create a string, map it, and print it out. And just for good measure, I do the same process on another string. Here's the output:

```
Today is Montag, tomorrow is Dienstag!
And then comes Mittwoch!
```

# ## replace

The replace command replaces characters based on position. Here's an example:

```
set mytring "Eat at Joe's"
set result [string replace $mytring 7 9 "Frank"]
puts $result
```