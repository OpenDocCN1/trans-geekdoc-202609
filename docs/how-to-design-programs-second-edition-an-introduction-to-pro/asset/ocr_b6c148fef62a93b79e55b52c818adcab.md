# 1.7 Predicates: Know Thy Data

Remember the expression (string-length 42) and its result. Actually, the expression doesn't have a result, it signals an error. DrRacket lets you know about errors via red text in the interactions area and highlighting of the faulty expression (in the definitions area). This way of marking errors is particularly helpful when you use this expression (or its relatives) deeply nested within some other expression:

```
( * ( + (string-length 42) 1) pi )
```

Experiment with this expression by entering it both into DrRacket's interactions area and in the definitions area (and then click on RUN).

Of course, you really don't want such error-signaling expressions in your program. And usually, you don't make such obvious mistakes as using 42 as a string. It is quite common, however, that programs deal with variables that may stand for either a number or a string:

```
(define in ...)
```

```
(string-length in)
```

A variable such as in can be a placeholder for any value, including a number, and this value then shows up in the string-length expression.

One way to prevent such accidents is to use a predicate, which is a function that consumes a value and determines whether or not it belongs to some class of data. For example, the predicate number? determines whether the given value is a number or not:

```
> (number? 4)
#true
> (number? pi)
#true
> (number? #true)
#false
> (number? "fortytwo")
```