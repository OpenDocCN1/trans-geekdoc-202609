# 16.5 Using Abstractions, by Example

Now that you understand `local`, you can easily use the abstractions from figures 95 and 96. Let’s look at examples, starting with this one:

**Sample Problem** Design add-3-to-all. The function consumes a list of Posns and adds 3 to the x-coordinates of each.

If we follow the design recipe and take the problem statement as a purpose statement, we can quickly step through the first three steps:

```
; [List-of Posn] -> [List-of Posn]
; adds 3 to each x-coordinate on the given list

(check-expect
 (add-3-to-all
  (list (make-posn 3 1) (make-posn 0 0)))
 (list (make-posn 6 1) (make-posn 3 0)))

(define (add-3-to-all lop) '())
```

While you can run the program, doing so signals a failure in the one test case because the function returns the default value '().

At this point, we stop and ask what kind of function we are dealing with. Clearly, add-3-to-all is a list-processing function. The question is whether it is like any of the functions in figures 95 and 96. The signature tells us that add-3-to-all is a list-processing function that consumes and produces a list. In the two figures, we have several functions with similar signatures: map, filter, and sort.

The purpose statement and example also tell you that add-3-to-all deals with each Posn separately and assembles the results into a single list. Some reflection says that also confirms that the resulting list contains as many items as the given list. All this thinking points to one function—map—because the point of filter is to drop items from the list and sort has an extremely specific purpose.

Here is map’s signature again: