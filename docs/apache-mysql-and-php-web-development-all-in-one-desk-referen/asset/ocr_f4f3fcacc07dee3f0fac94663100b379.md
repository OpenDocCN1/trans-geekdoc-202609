```
```
gets stdin author
gets stdin price
if {$author == "Jeff Cogswell" && $price < 500} {
puts "Sounds like a bargain!"
} else {
puts "I cannot vouch for the book's accuracy"
}
```
```

I separated two conditions with the characters &&, which means both conditions must be met for the main if block to run; otherwise the else block runs. Here's a sample session:

```
```
$tclsh and.tcl
Jeff Cogswell
34.95
Sounds like a bargain!

$tclsh and.tcl
Ernest Hemingway
15.95
I cannot vouch for the book's accuracy
```
```

Instead of the logical and operator, you can try out a logical or operator. With the or operator, you run the block if either condition is true; both conditions don't need to be true. Here's an example; notice I simply changed the && (which means and) to || (that is, two vertical bar characters, which means or):

```
```
gets stdin author
gets stdin price
if {$author == "Jeff Cogswell" || $price < 500} {
puts "Sounds like a bargain!"
} else {
puts "I cannot vouch for the book's accuracy"
}
```
```

Here's a sample session. Note that only one condition must be met for the main if block to run: Either the author must be me (er, I mean Jeff Cogswell), or the price must be less than 500:

```
```
$tclsh or.tcl
Jeff Cogswell
6523.35
Sounds like a bargain!

$tclsh or.tcl
Ernest Hemingway
```
```