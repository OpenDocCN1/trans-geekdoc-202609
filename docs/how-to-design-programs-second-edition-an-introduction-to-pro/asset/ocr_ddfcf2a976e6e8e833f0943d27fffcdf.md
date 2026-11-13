The function header contains (x), which is **not** a variable name.

```
(define (h x y) x y)        define: expected only
                           one expression for the
                           function body, but
                           found 1 extra part
```

This function definition comes with two expressions following
the header: x and y.

# *Error Messages about Structure Type Definitions in BSL*

Now you need to place the structure type definitions into the definitions area and
hit RUN to experiment with the following errors.

```
(define-struct (x) )
(define-struct (x y) )      define-struct:
                           expected the structure
                           name after
                           define-struct, but
                           found a part
```

A structure type definition consists of three parts: the `define-struct`
keyword, the structure's name, and a sequence of names
in parentheses. Here the structure's name is missing.

```
(define-struct x
[y y])        define-struct: found a
             field name that is
             used more than once: y
```

The sequence of field names in a structure type definition must
not contain duplicate names.