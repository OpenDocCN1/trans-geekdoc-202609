```
set x 100
if {$x == 100} {
    set y 200
    if {$y == 200} {
        puts "Works!"
    }
}
```

The following program reads the indenttest.txt file, indents each line four spaces, and prints out the results. Then it reduces the indention of each line a couple spaces and prints out the new results:

```
package require textutil
set f [open "indenttest.txt"]
set t [read $f]
close $f
set res [::textutil::indent $t "  "]
puts $res
puts ""
set res2 [::textutil::indent $res "  "]
puts res2
```

Notice how I make use of the textutil package and then access the indent command using ::textutil::indent. First, I open a file and read in the file's contents into the t variable. Then I try indenting the whole file with several spaces and printing out the results. Next, I try indenting again, but with fewer spaces, and again print out the results. Here's the output; notice that the second block is indented less than the first block:

```
set x 100
if {$x == 100} {
    set y 200
    if {$y == 200} {
        puts "Works!"
    }
}
```

```
set x 100
    if {$x == 100} {
        set y 200
        if {$y == 200} {
            puts "Works!"
        }
    }
}
```

# Reformatting text

Often when working with online text you need to reformat text to fit within a certain width. Many e-mail programs perform this function, and the textutil