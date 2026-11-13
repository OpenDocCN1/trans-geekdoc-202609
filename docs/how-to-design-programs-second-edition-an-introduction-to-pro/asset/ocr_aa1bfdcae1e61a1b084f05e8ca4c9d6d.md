# **Exercise 80.** Create templates for functions that consume instances of the following structure types:

+   - `(define-struct movie [title director year])`
+   - `(define-struct pet [name number])`
+   - `(define-struct CD [artist title price])`
+   - `(define-struct sweater [material size color])`

No, you do not need data definitions for this task.

**Exercise 81.** Design the function `time->seconds`, which consumes instances of time structures (see exercise 77) and produces the number of seconds that have passed since midnight. For example, if you are representing 12 hours, 30 minutes, and 2 seconds with one of these structures and if you then apply `time->seconds` to this instance, the correct result is 45002.

**Exercise 82.** Design the function `compare-word`. The function consumes two three-letter words (see exercise 78). It produces a word that indicates where the given ones agree and disagree. The function retains the content of the structure fields if the two agree; otherwise it places `#false` in the field of the resulting word. **Hint** The exercises mentions two tasks: the comparison of words and the comparison of “letters.”