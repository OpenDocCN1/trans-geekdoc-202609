Here's a program that reads in a string from the console, saves the string to the variable name, and then compares name to various strings, printing out a message if name equals the particular string:

```
gets stdin name
switch $name {
"Jeff" ( puts "Hi Jeff" )
"Sally" ( puts "Hi Sally" )
"Bill" ( puts "Hi Bill" )
"Jessica" ( puts "Hi Jessica" )
default ( puts "Hi you" )
}
```

If the name contains the string Jeff, the program prints out Hi Jeff. If the name contains the string Sally, it prints out Hi Sally, and so on. As you can see, this switch statement is just like a big if command followed by a bunch of elseif commands and a final default command.

From here to the end of this section is a more sophisticated example of the switch statement. If you're familiar with other programming languages, this one might surprise you a bit because you can put strings in switch statements in Tcl:

```
gets stdin name
set greeting ( "Hello there $name" )
switch $name {
"Jeff" {
puts [expr $greeting]
puts "You look sharp today!"
}
"Sally" {
puts [expr $greeting]
puts "Great outfit!"
}
"Bill" {
puts [expr $greeting]
puts "Good to see you!"
}
"Jessica" {
puts [expr $greeting]
puts "Thanks for stopping by!"
}
default { puts "I don't know you" }
}
```

Look carefully at the second line:

```
set greeting ( "Hello there $name" )
```