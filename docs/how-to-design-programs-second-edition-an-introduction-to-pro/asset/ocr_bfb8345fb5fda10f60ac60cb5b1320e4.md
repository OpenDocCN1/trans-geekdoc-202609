# 17.4 Specifying with lambda

Figure 99 shows a generalized sorting function that consumes a list of values and a comparison function for such values. For convenience, figure 103 reproduces the essence of the definition. The body of sort-cmp introduces two local auxiliary functions: isort and insert. In addition, the figure also comes with two test cases that illustrate the workings of sort-cmp. One demonstrates how the function works on strings and the other one on numbers.

```
; [X] [List-of X] [X X -> Boolean] -> [List-of X]
; sorts alon0 according to cmp

(check-expect (sort-cmp '("c" "b") string<?) '("b" "c"))
(check-expect (sort-cmp '(2 1 3 4 6 5) <) '(1 2 3 4 5 6))

(define (sort-cmp alon0 cmp)
  (local (; [List-of X] -> [List-of X]
          ; produces a variant of alon sorted by cmp
          (define (isort alon) ...)
          ; X [List-of X] -> [List-of X]
          ; inserts n into the sorted list of numbers alon
          (define (insert n alon) ...))
  (isort alon0)))
```

Figure 103: A general sorting function

Now take a quick look at exercise 186. It asks you to formulate check-satisfied tests for sort> using the sorted>? predicate. The former is a function that sorts lists of numbers in descending order; the latter is a function that determines whether a list of numbers is sorted in descending order. Hence, the solution of this exercise is

```
(check-satisfied (sort> '()) sorted>?)
(check-satisfied (sort> '(12 20 -5)) sorted>?)
(check-satisfied (sort> '(3 2 1)) sorted>?)
(check-satisfied (sort> '(1 2 3)) sorted>?)
```

The question is how to reformulate the tests for sort-cmp analogously.

Since sort-cmp consumes a comparison function together with a list, the