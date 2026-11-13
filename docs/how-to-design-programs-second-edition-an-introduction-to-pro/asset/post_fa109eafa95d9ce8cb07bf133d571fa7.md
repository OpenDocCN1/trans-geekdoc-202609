
and an interval that contains both roots.

**Exercise 448.** The `find-root` algorithm terminates for all (continuous) f, left, and right for which the assumption holds. Why? Formulate a termination argument.

**Hint** Suppose the arguments of `find-root` describe an interval of size S1. How large is the distance between `left` and `right` for the first and second recursive call to `find-root`? After how many steps is (- right left) smaller than or equal to ε?

**Exercise 449.** As presented in figure 159, `find-root` computes the value of f for each boundary value twice to generate the next interval. Use `local` to avoid this recomputation.

In addition, `find-root` recomputes the value of a boundary across recursive calls. For example, (`find-root` f `left` `right`) computes (`f` `left`) and, if [`left`,`mid`] is chosen as the next interval, `find-root` computes (`f` `left`) again. Introduce a helper function that is like `find-root` but consumes not only `left` and `right` but also (`f` `left`) and (`f` `right`) at each recursive stage.

How many recomputations of (`f` `left`) does this design maximally avoid?

**Note** The two additional arguments to this helper function change at each recursive stage, but the change is related to the change in the numeric arguments. These arguments are so-called *accumulators*, which are the topic of part VI.

**Exercise 450.** A function f is *monotonically increasing* if (<= (f a) (f b)) holds whenever (< a b) holds. Simplify `find-root` assuming the given function is not only continuous but also monotonically increasing.

**Exercise 451.** A table is a structure of two fields: the natural number VL and a function array, which consumes natural numbers and, for those between 0 and VL (exclusive), produces answers:

```
(define-struct table [length array])
; A Table is a structure:
;   (make-table N [N -> Number])
```

> Many programming languages, including Racket, support arrays and vectors, which are similar to tables.

Since this data structure is somewhat unusual, it is critical to illustrate it with

examples:

```
(define table1 (make-table 3 (lambda (i) i)))
```

```
; N -> Number
(define (a2 i)
 (if (= i 0)
  pi
  (error "table2 is not defined for i != 0")))
```

```
(define table2 (make-table 1 a2))
```

Here table1's array function is defined for more inputs than its length field allows; table2 is defined for just one input, namely 0. Finally, we also define a useful function for looking up values in tables:

```
; Table N -> Number
; looks up the ith value in array of t
(define (table-ref t i)
 ((table-array t) i))
```

The root of a table t is a number in (table-array t) that is close to 0. A root index is a natural number i such that (table-ref t i) is a root of table t. A table t is monotonically increasing if (table-ref t 0) is less than (table-ref t 1), (table-ref t 1) is less than (table-ref t 2), and so on.

Design find-linear. The function consumes a monotonically increasing table and finds the smallest index for a root of the table. Use the structural recipe for N, proceeding from 0 through 1, 2, and so on to the array-length of the given table. This kind of root-finding process is often called a linear search.

Design find-binary, which also finds the smallest index for the root of a monotonically increasing table but uses generative recursion to do so. Like ordinary binary search, the algorithm narrows an interval down to the smallest possible size and then chooses the index. Don't forget to formulate a termination argument.

Hint The key problem is that a table index is a natural number, not a plain number. Hence the interval boundary arguments for find must be natural numbers. Consider how this observation changes (1) the nature of trivially solvable problem instances, (2) the midpoint computation, (3) and the decision as to which interval to generate next. To make this concrete, imagine a table with 1024 slots and the root at 1023. How many calls to find are needed in find-linear and find-binary, respectively?■

## 27.3 A Glimpse at Parsing

As mentioned in chapter 20, computers come with files, which provide a form of permanent memory. From our perspective a file is just a list of 1Strings, though interrupted by a special string:

```
; A File is one of:
; -- '()
; -- (cons "\\n" File)
; -- (cons 1String File)
; interpretation represents the content of a file
; "\\n" is the newline character
```

> The exact convention differs from one operating system to another, but for our purposes this is irrelevant.

The idea is that Files are broken into lines, where "\\n" represents the so-called newline character, which indicates the end of a line. Let's also introduce lines before we move on:

```
; A Line is a [List-of 1String].
```

Many functions need to process files as list of lines. The read-lines from the 2htdp/batch-io library is one of them. Concretely, the function turns the file

```
(list
 "h" "o" "w" " " "a" "r" "e" " " "y" "o" "u" "\\n"
 "d" "o" "i" "n" "g" "?" "\\n"
 "a" "n" "y" " " "p" "r" "o" "g" "r" "e" "s" "s" "?")
```

into a list of three lines:

```
(list
 (list "h" "o" "w" " " "a" "r" "e" " " "y" "o" "u")
 (list "d" "o" "i" "n" "g" "?")
 (list "a" "n" "y" " " "p" "r" "o" "g" "r" "e"
 "s" "s" "?"))
```

Similarly, the file

```
(list "a" "b" "c" "\\n" "d" "e" "\\n" "f" "g" "h" "\\n")
```

also corresponds to a list of three lines:

```
(list (list "a" "b" "c")
 (list "d" "e")
 (list "f" "g" "h"))
```

Stop! What are the list-of-lines representations for these three cases: '(), (list "\\n"), and (list "\\n" "\\n")? Why are these examples important test cases?

The problem of turning a sequence of 1Strings into a list of lines is called the parsing problem. Many programming languages provide functions that retrieve lines, words, numbers, and other kinds of so-called tokens from files. But even if they do, it is common that programs need to parse these tokens even further. This section provides a glimpse at a parsing technique. Parsing is so complex and so central to the creation of full-fledged software applications, however, that most undergraduate curricula come with at least one course on parsing. So do not think you can tackle real parsing problems properly even after mastering this section.

We start by stating the obvious—a signature, a purpose statement, one of the above examples, and a header—for a function that turns a File into a list of Lines:

```
; File -> [List-of Line]
; converts a file into a list of lines

(check-expect (file->list-of-lines
   (list "a" "b" "c" "\\n"
      "d" "e" "\\n"
      "f" "g" "h" "\\n"))
   (list (list "a" "b" "c")
      (list "d" "e")
      (list "f" "g" "h"))))

(define (file->list-of-lines afile) '())
```

It is also easy to describe the parsing process, given our experience with chapter 26.1:

- 1. The problem is trivially solvable if the file is '().
- 2. In that case, the file doesn't contain a line.
- 3. Otherwise, the file contains at least one "\\n" or some other 1String. These items—up to and including the first "\\n", if any—must be separated from the rest of the File. The remainder is a new problem of the same kind that file->list-of-lines can solve.
- 4. It then suffices to cons the initial segment as a single line to the list of Lines that result from the rest of the File.

The four questions suggest a straightforward instantiation of the template for generative recursive functions. Because the separation of the initial segment from the rest of the file requires a scan of an arbitrarily long list of 1Strings, we put two auxiliary functions on our wish list: first-line, which collects all 1Strings up to, but excluding, the first occurrence of "\\n" or the end of the list; and remove-first-line, which removes the very same items that first-line collects.

From here, it is easy to create the rest of the program. In file->list-of-lines, the answer in the first clause must be '() because an empty file does not
