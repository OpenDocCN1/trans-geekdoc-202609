```
{ 1 2 } x LIST
{ 3 4 } y LIST
{ x, y, } xy LIST ( The commas delay evaluation of x and y.)
```

Invoking xy will, in turn, invoke the LIST constructors of each of its constituent members, x and y.

```
xy
{ 1 2 } x LIST { 3 4 } y LIST ( The result of xy.)
```

Alternatively, consider if xy were defined to allow the immediate evaluation of its members, x and y, such as:

```
{ x y }xy LIST
```

Then, the contents of xy would be { 1 2 3 4 }.

2 R. Chassell, An Introduction to Programming in Emacs Lisp. GNU Press, 2004. (See Section 1.1.1 on page 5.) ISBN: 1-882114-43-4. DOI: https://www.gnu.org/software/emacs/manual/html_node/eintr/Lisp-Atoms.html.
3 The term LIST is a keyword in the epop language that is used to define a list. It is essentially a type of function.

When functions are treated as data, they may be referred to as higher order functions, a concept germane to the modern discipline of functional programming. Higher order functions can either take functions as arguments or return functions as a result.