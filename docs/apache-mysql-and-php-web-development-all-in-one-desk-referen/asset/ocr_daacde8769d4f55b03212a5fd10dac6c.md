> If you include the braces, the interpreter does no substitution and passes the text on to the command. Without the braces, the interpreter does the substitution first and then passes the results on to the command.

# Processing Strings

Tcl lets you store and process strings. If you've worked in other languages, you're probably not the least bit surprised. What would a language be without strings? A very boring language at best. Not to mention nearly useless.

Here's an example of storing a string in a variable called name:

```
set name "George Washington"
```

That's pretty simple. Just type set, the name of the variable, and then put the string inside double quotes. If you're doing this interactively, you can then print out the string like so:

```
% puts $name
George Washington
```

You can see from the output that the double quotes are not part of the string.

If you want to combine and concatenate strings, you can do this:

```
set firstname "George"
set lastname "Washington"
set fullname "$firstname $lastname"
puts $fullname
```

When you run this code, the name is printed out:

```
George Washington
```

But you can do even more with strings with Tcl. In the following sections, I show you many of the possibilities.

> To use the string-processing features in Tcl, you use various string commands. You precede the names of these string commands with the command name string.

# Determining information about a string

Tcl includes two commands for finding out information about a string: length and is.