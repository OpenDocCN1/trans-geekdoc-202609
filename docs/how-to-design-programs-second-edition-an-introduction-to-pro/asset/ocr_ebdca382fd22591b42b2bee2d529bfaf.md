# 14.3 Similarities in Data Definitions

Now take a close look at the following two data definitions:

```
; An Lon (List-of-numbers)                    ; An Los (List-of-String)
; is one of:                                  ; is one of:
; -- '()                                      ; -- '()
; -- (cons Number Lon)                        ; -- (cons String Los)
```

The one on the left introduces lists of numbers; the one on the right describes lists of strings. And the two data definitions are similar. Like similar functions, the two data definitions use two different names, but this is irrelevant because any name would do. The only real difference concerns the first position inside of cons in the second clause, which specifies what kind of items the list contains.

In order to abstract over this one difference, we proceed as if a data definition were a function. We introduce a parameter, which makes the data definition look like a function, and where there used to be different references, we use this parameter:

```
; A [List-of ITEM] is one of:
; -- '()
; -- (cons ITEM [List-of ITEM])
```

We call such abstract data definitions *parametric data definitions* because of the parameter. Roughly speaking, a parametric data definition abstracts from a reference to a particular collection of data in the same manner as a function abstracts from a particular value.

The question is, of course, what these parameters range over. For a function, they stand for an unknown value; when the function is applied, the value becomes known. For a parametric data definition, a parameter stands for an entire class of values. The process of supplying the name of a data collection to a parametric data definition is called *instantiation*; here are some sample instantiations of the List-of abstraction:

+   - When we write [List-of Number], we are saying that ITEM represents all