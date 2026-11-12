You can also intermix variables. Remember how the interpreter performs the substitution: If you put a dollar sign followed by your variable name, the interpreter replaces the dollar sign and variable with the variable's value (unless you put these characters inside curly braces). So you can probably guess what this example will do:

```
% set x 100
100
% puts "My favorite number is $x"
```

After pressing Enter at the end of the final line, you see this:

My favorite number is 100

# Creating a Simple Tcl Program

To create a simple Tcl program, you type the code into a text editor as you would any other programming language. You then save the file to a directory, giving the file a .tcl filename extension. To run the program, you type the following line, replacing myprogram.tcl with the name of your file:

```
tc1sh myprogram.tcl
```

Alternatively, if you're using Unix, you can make your Tcl file executable by setting the following permission:

```
chmod u+x myprogram.tcl
```

Then you can put a pound-bang (#!) line at the beginning of the file that specifies the Tcl interpreter. The line looks like this:

```
#!/usr/local/bin/tc1sh
```

(If you installed the Tcl binaries in a different location, such as /usr/bin, type #!/usr/bin/tc1sh instead.) Then you can run your program by typing the name of the file, like so:

```
myprogram.tcl
```

The Unix shell looks at the first line and runs the program /usr/local/bin/tc1sh, passing your file as a command-line parameter.