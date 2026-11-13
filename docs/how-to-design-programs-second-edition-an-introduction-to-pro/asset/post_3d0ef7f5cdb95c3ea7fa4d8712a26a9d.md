
- 3. (insert n (rest alon)) produces a sorted list from n and the numbers on (rest alon).

The problem is how to combine these pieces of data to get the final answer. Let's work through some examples to make all this concrete:

```
(insert 7 (list 6 5 4))
```

Here n is 7 and larger than any of the numbers in the second input. We know so by just looking at the first item of the list. It is 6, but because the list is sorted all other numbers on the list are even smaller than 6. Hence it suffices if we just cons 7 onto (list 6 5 4).

In contrast, when the application is something like

```
(insert 0 (list 6 2 1 -1))
```

n must indeed be inserted into the rest of the list. More concretely, (first alon) is 6; (rest alon) is (list 2 1 -1); and (insert n (rest alon)) produces (list 2 1 0 -1) according to the purpose statement. By adding 6 back onto that last list, we get the desired answer for (insert 0 (list 6 2 1 -1)).

To get a complete function definition, we must generalize these examples. The case analysis suggests a nested conditional that determines whether n is larger than (or equal to) (first alon):

- If so, all the items in alon are smaller than n because alon is already sorted. The answer in that case is (cons n alon).

- If, however, n is smaller than (first alon), then the function has not yet found the proper place to insert n into alon. The first item of the result must be (first alon) and that n must be inserted into (rest alon). The final result in this case is

```
(cons (first alon) (insert n (rest alon)))
```

because this list contains n and all items of alon in sorted order—which is what we need.

The translation of this discussion into BSL+ calls for an if expression for such cases. The condition is (>= n (first alon)), and the expressions for the two branches have been formulated.

Figure 72 contains the complete sort program. Copy it into the definitions area of DrRacket, add the test cases back in, and test the program. All tests should pass now, and they should cover all expressions.

```
; List-of-numbers -> List-of-numbers
; produces a sorted version of l
(define (sort> l)
 (cond
  [(empty? l) '()]
  [(cons? l) (insert (first l) (sort> (rest l)))]))

; Number List-of-numbers -> List-of-numbers
; inserts n into the sorted list of numbers l
(define (insert n l)
 (cond
  [(empty? l) (cons n '())]
  [else (if (>= n (first l))
   (cons n l)
   (cons (first l) (insert n (rest l)))))]))
```

## Figure 72: Sorting lists of numbers

**Terminology** This particular program for sorting is known as *insertion sort* in the programming literature. Later we will study alternative ways to sort lists, using an entirely different design strategy.

## Exercise 186. Take a second look at intermezzo 1, the intermezzo that presents BSL and its ways of formulating tests. One of the latter is check-satisfied, which determines whether an expression satisfies a certain property. Use sorted>? from exercise 145 to reformulate the tests for sort> with check-satisfied.

```
; List-of-numbers -> List-of-numbers
; produces a sorted version of l
(define (sort>/bad l)
(list 9 8 7 6 5 4 3 2 1 0))
```

Can you formulate a test case that shows that sort>/bad is **not** a sorting function? Can you use check-satisfied to formulate this test case?

Notes (1) What may surprise you here is that we define a function to create a test. In the real world, this step is common, and, on occasion, you really need to design functions for tests—with their own tests and all. (2) Formulating tests with check-satisfied is occasionally easier than using check-expect (or other forms), and it is also a bit more general. When the predicate completely describes the relationship between all possible inputs and outputs of a function, computer scientists speak of a specification. Chapter 17.4 explains how to specify sort> completely.

## Exercise 187. Design a program that sorts lists of game players by score:

```
(define-struct gp [name score])
; A GamePlayer is a structure:
;   (make-gp String Number)
; interpretation (make-gp p s) represents player p who
; scored a maximum of s points
```

**Hint** Formulate a function that compares two elements of GamePlayer.

## Exercise 188. Design a program that sorts lists of emails by date:

```
(define-struct email [from date message])
; An Email Message is a structure:
;   (make-email String Number String)
; interpretation (make-email f d m) represents text m
; sent by f, d seconds after the beginning of time
```

Also develop a program that sorts lists of email messages by name. To compare two strings alphabetically, use the string<? primitive.

## Exercise 189. Here is the function search:

```
; Number List-of-numbers -> Boolean
(define (search n alon)
(cond
[(empty? alon) #false]
[else (or (= (first alon) n)
(search n (rest alon)))]))
```

It determines whether some number occurs in a list of numbers. The function may have to traverse the entire list to find out that the number of interest isn't contained in the list.

Develop the function search-sorted, which determines whether a number occurs in a sorted list of numbers. The function must take advantage of the fact that the list is sorted.

## Exercise 190. Design the prefixes function, which consumes a list of 1Strings and produces the list of all prefixes. A list p is a prefix of l if p and l are the same up through all items in p. For example, (list "a" "b" "c") is a prefix of itself and (list "a" "b" "c" "d").

Design the function suffixes, which consumes a list of 1Strings and produces all suffixes. A list s is a suffix of l if p and l are the same from the end, up through all items in s. For example, (list "b" "c" "d") is a suffix of itself and (list "a" "b" "c" "d").

## 11.4 Auxiliary Functions that Generalize

On occasion an auxiliary function is not just a small helper function but a solution to a more general problem. Such auxiliaries are needed when a problem statement is too narrow. As programmers work through the steps of the design recipe, they may discover that the “natural” solution is wrong. An analysis of this broken solution may suggest a slightly different, but more general, problem statement, as well as a simple way of using the solution to the general problem for the original one.

> Paul C. Fisher suggested this problem.

We illustrate this idea with a solution to the following problem:

## Sample Problem Design a function that adds a polygon to a given scene.

Just in case you don’t recall your basic geometry (domain) knowledge, we add a (simplistic) definition of polygon:

A polygon is a planar figure with at least three points (not on a straight line) connected by three straight sides.

One natural data representation for a polygon is thus a list of Posns. For example, the following two definitions

```
(define triangle-p
 (list
 (make-posn 20 10)
 (make-posn 20 20)
 (make-posn 30 20)))
(define square-p
 (list
 (make-posn 10 10)
 (make-posn 20 10)
 (make-posn 20 20)
 (make-posn 10 20)))
```

introduce a triangle and a square, just as the names say. Now you may wonder how to interpret '() or (list (make-posn 30 40)) as polygons, and the answer is that they do not describe polygons. Because a polygon consists of at least three points, a good data representation of polygons is the collection of lists with at least three Posns.

Following the development of the data definition for non-empty lists of temperatures (NEList-of-temperatures, in chapter 9.2), formulating a data representation for polygons is straightforward:

```
; A Polygon is one of:
; -- (list Posn Posn Posn)
; -- (cons Posn Polygon)
```

The first clause says that a list of three Posns is a Polygon, and the second clause says that consing a Posn onto some existing Polygon creates another one. Since this data definition is the very first to use list in one of its clauses, we spell it out with cons just to make sure you see this conversion from an abbreviation to long-hand in this context:

```
; a Polygon is one of:
; -- (cons Posn (cons Posn (cons Posn '())))
; -- (cons Posn Polygon)
```

The point is that a naively chosen data representation—plain lists of Posns—may not properly represent the intended information. Revising the data definition during an initial exploration is normal; indeed, on occasion such revisions become necessary during the rest of the design process. As long as you stick to a systematic approach, though, changes to the data definition can naturally be propagated through the rest of the design.

The second step calls for the signature, purpose statement, and header of the function. Since the problem statement mentions just one task and no other task is implied, we start with one function:

```
(define MT (empty-scene 50 50))
```

```
; Image Polygon -> Image
; renders the given polygon p into img
(define (render-poly img p)
  img)
```
