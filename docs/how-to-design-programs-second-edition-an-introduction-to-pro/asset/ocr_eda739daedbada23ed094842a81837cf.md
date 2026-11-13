# 11.4 Auxiliary Functions that Generalize

On occasion an auxiliary function is not just a small helper function but a solution to a more general problem. Such auxiliaries are needed when a problem statement is too narrow. As programmers work through the steps of the design recipe, they may discover that the “natural” solution is wrong. An analysis of this broken solution may suggest a slightly different, but more general, problem statement, as well as a simple way of using the solution to the general problem for the original one.

> Paul C. Fisher suggested this problem.

We illustrate this idea with a solution to the following problem:

# Sample Problem Design a function that adds a polygon to a given scene.

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

introduce a triangle and a square, just as the names say. Now you may wonder how to interpret ’() or (list (make-posn 30 40)) as polygons, and the answer is that they do not describe polygons. Because a polygon consists of at least three points, a good data representation of polygons is the collection of lists with