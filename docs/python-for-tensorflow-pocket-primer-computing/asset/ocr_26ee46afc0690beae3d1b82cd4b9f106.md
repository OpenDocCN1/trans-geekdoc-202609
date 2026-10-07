* len(sys.argv) is the number of command-line arguments

Here sys.argv[0] is the program name, so if the Python program is called test.py, it matches the value of sys.argv[0].

Now you can provide input values for a Python program on the command line instead of providing input values by prompting users for their input.

As an example, consider the script test.py shown here:

```
#!/usr/bin/python
import sys
print 'Number of
arguments:',len(sys.argv),'arguments'
print 'Argument List:',', str(sys.argv)
```

Now run above script as follows:

```
python test.py arg1 arg2 arg3
```

This will produce the following result:

Number of arguments: 4 arguments.
Argument List: ['test.py', 'arg1', 'arg2', 'arg3']

The ability to specify input values from the command line provides useful functionality. For example, suppose that you have a custom Python class that contains the methods add and subtract to add and subtract a pair of numbers.

You can use command-line arguments in order to specify which method to execute on a pair of numbers, as shown here:

```
python MyClass add 3 5
python MyClass subtract 3 5
```

This functionality is very useful because you can programmatically execute different methods in a Python class, which