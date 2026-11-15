+   - Data types include floats, integers, strings, tables, and executable objects.
+   - Scripts can be interpreted during run-time or run against the interpreter from the command line.
+   - Words may be defined during run-time or preprocessed into the runnable machine code at complile time.
+   - Words may also be defined during run-time that persist in the runnable machine code after restart.

Apart from the above points, please note that epop requires particular word sequences. epop will not deduce what the coder intends if a sequence is incorrect. This makes epop good for teaching/learning and enforcing systematized reasoning.

# A.2 POSTFIX

The notation used for mathematical expressions in this book includes postfix as well as the more common infix. Postfix is also called Reverse Polish Notation (RPN).

In postfix, the operation symbol is written last, after the arguments. (This pertains to words that require arguments.)

Examples of infix as postfix:

```
1 + 2 becomes: 1 2 +
x * 2 + 1 becomes: x 2 * 1 +
```

The distinguishing characteristics of postfix operations: