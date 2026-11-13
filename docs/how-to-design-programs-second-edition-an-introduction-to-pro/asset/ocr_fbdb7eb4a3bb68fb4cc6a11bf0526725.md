```
(define (wages*.v2 hours wages/h)
 (cond
  [(empty? hours) ...]
  [else
   (... (first hours)
    ... (first wages/h) ...
    ... (wages*.v2 (rest hours) (rest wages/h)))]))
```

In the first cond clause, both hours and wages/h are '(). Hence no selector expressions are needed. In the second clause, both hours and wages/h are constructed lists, which means we need four selector expressions. Finally, because the last two are lists of equal length, they make up a natural candidate for the natural recursion of wages*.v2.

The only unusual aspect of this template is that the recursive application consists of two expressions, both selector expressions for the two arguments. But, this idea directly follows from the assumption.

From here, it is a short step to a complete function definition:

```
(define (wages*.v2 hours wages/h)
 (cond
  [(empty? hours) '()]
  [else
   (cons
    (weekly-wage (first hours) (first wages/h))
    (wages*.v2 (rest hours) (rest wages/h)))]))
```

The first example implies that the answer for the first cond clause is '(). In the second one, we have three values available:

+   1. (first hours), which represents the first number of weekly hours;
+   
+   2. (first wages/h), which is the first pay rate; and
+   
+   3. (wages*.v2 (rest hours) (rest wages/h)), which, according to the purpose statement, computes the list of weekly wages for the remainders of the two lists.