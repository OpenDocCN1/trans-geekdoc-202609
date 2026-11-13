# 23.4 Function Simplification

The list-pick function in figure 134 is far more complicated than necessary. The first two cond clauses signal an error. That is, if either

```
; [List-of Symbol] N -> Symbol
; extracts the nth symbol from l;
; signals an error if there is no such symbol
(define (list-pick l n)
(cond
[(and (= n 0) (empty? l))
(error 'list-pick "list too short")]
[(and (> n 0) (empty? l))]
(error 'list-pick "list too short")]
[(and (= n 0) (cons? l)) (first l)]
[(and (> n 0) (cons? l)) (list-pick (rest l) (sub1 n))]))
```

Figure 134: Indexing into a list

```
(and (= n 0) (empty? alos))
```

or

```
(and (> n 0) (empty? alos))
```

holds, the answer is an error. We can translate this observation into code:

```
(define (list-pick alos n)
(cond
[(or (and (= n 0) (empty? alos))
(and (> n 0) (empty? alos)))]
(error 'list-pick "list too short")]
[(and (= n 0) (cons? alos)) (first alos)]
[(and (> n 0) (cons? alos))
(list-pick (rest alos) (sub1 n))]))
```

To simplify this function even more, we need to get acquainted with algebraic laws concerning Booleans: