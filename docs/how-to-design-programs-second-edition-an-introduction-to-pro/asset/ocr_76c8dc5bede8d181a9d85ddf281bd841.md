```
; [List-of Addr] -> String
; creates a string of first names,
; sorted in alphabetical order,
; separated and surrounded by blank spaces
(define (listing.v2 1)
  (local (; 1. extract names
          (define names (map address-first-name 1))
          ; 2. sort the names
          (define sorted (sort names string<?>))
          ; 3. append them, add spaces
          ; String String -> String
          ; appends two strings, prefix with " "
          (define (helper s t)
            (string-append " " s t))
          (define concat+spaces
            (foldr helper "" sorted))))
  concat+spaces))
```

# Figure 98: Organizing a function with local

In this example, the sequence of definitions consists of four pieces: three constant definitions and a single function definition. Each constant definition represents one of the three planning tasks. The function definition is a renamed version of string-append-with-space; it is used with foldr to implement the third task. The body of local is just the name of the third task.

> Since the names are visible only within the local expression, shortening the name is fine.

The visually most appealing difference concerns the overall organization. It clearly brings across that the function achieves three tasks and in which order. As a matter of fact, this example demonstrates a general principle of readability:

> Use local to reformulate deeply nested expressions. Use well-chosen names to express what the expressions compute.

Future readers appreciate it because they can comprehend the code by looking at just the names and the body of the local expression.

**Note on Organization** A local expression is really just an expression. It may show up wherever a regular expression shows up. Hence it is possible to indicate precisely where an auxiliary function is needed. Consider this reorganization of the local expression of listing.v2: