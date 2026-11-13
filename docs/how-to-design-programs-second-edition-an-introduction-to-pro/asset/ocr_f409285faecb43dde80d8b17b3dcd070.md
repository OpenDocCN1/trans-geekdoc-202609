A conditional must come with at least one cond clause and
usually it comes with at least two.

# Error Messages about Function Definitions in BSL

All of the following error scenarios assume that you have placed the code
snippet into the definitions area and hit RUN.

```
(define f(x) x)
```

define: expected only
one expression after
the variable name f,
but found 1 extra part

A definition consist of three parts: the define keyword, a
sequence of variable names enclosed in parentheses, and an
expression. This definition consists of four parts; this definition is
an attempt to use the standard notation from algebra courses for
the header f (x) instead of (f x).

```
(define (f x x) x)
```

define: found a
variable that is used
more than once: x

The sequence of parameters in a function definition must not
contain duplicate variables.

```
(define (g) x)
```

define: expected at
least one variable
after the function
name, but found none

In BSL a function header must contain at least two names. The
first one is the name of the function; the remaining variable
names are the parameters, and they are missing here.

```
(define (f (x)) x)
```

define: expected a
variable, but found a
part