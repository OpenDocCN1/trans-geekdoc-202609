```
(sort ... string<?)
```

The dots represent the result of the map expression. Since the latter supplies a list of strings, the sort expression produces a sorted list of first names. And that leaves us with the outermost expression:

```
(foldr string-append-with-space " " ...)
```

This one reduces the sorted list of first names to a single string, using a function named string-append-with-space. With such a suggestive name, you can easily imagine now that this reduction concatenates all the strings in the desired way—even if you do not quite understand how the combination of foldr and string-append-with-space works.

**Exercise 257.** You can design build-list and foldl with the design recipes that you know, but they are not going to be like the ones that ISL provides. For example, the design of your own foldl function requires a use of the list reverse function:

```
; [X Y] [X Y -> Y] Y [List-of X] -> Y
; f*oldl works just like foldl
(check-expect (f*oldl cons '() '(a b c))
   (foldl cons '() '(a b c)))
(check-expect (f*oldl / 1 '(6 3 2))
   (foldl / 1 '(6 3 2)))
(define (f*oldl f e l)
   (foldr f e (reverse l))))
```

Design build-1*st, which works just like build-list. **Hint** Recall the add-at-end function from exercise 193. **Note on Design** Part VI covers the concepts needed to design these functions from scratch.