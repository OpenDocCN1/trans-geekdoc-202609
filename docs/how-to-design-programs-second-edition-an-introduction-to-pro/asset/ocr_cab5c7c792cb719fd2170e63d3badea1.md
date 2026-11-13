numbers, posn structures, and so on, as well as instances of posn that contain instances of ball. Try it out in DrRacket! Add

```
(define-struct ball [location velocity])
```

to the definitions area, hit RUN, and create some structure instances.

As far as the pragmatics of data definitions is concerned, a data definition for structure types describes large collections of data via combinations of existing data definitions with instances. When we write

```
; Posn is (make-posn Number Number)
```

we are describing an infinite number of possible instances of posn. Like above, the data definitions use combinations of natural language, data collections defined elsewhere, and data constructors. Nothing else should show up in a data definition at the moment.

A data definition for structures specifies a new collection of data made up of those instances to be used by our functions. For example, the data definition for Posns identifies the region shaded in gray in the center bubble of the universe in figure 31, which includes all those posn structures whose two fields contain numbers. At the same time, it is perfectly possible to construct an instance of posn that doesn’t satisfy the requirement that both fields contain numbers:

```
(make-posn (make-posn 1 1) "hello")
```

This structure contains a posn in the x field and a string in the y field.

**Exercise 76.** Formulate data definitions for the following structure type definitions:

+   * (define-struct movie [title producer year])
+   * (define-struct person [name hair eyes phone])
+   * (define-struct pet [name number])
+   * (define-struct CD [artist title price])
+   * (define-struct sweater [material size producer])