```
(define (connect-dots img p)
(cond
 [(empty? (rest p)) img]
 [else
 (render-line
 (connect-dots img (rest p))
 (first p)
 (second p))]))
```

This definition looks simpler than the faulty version of render-poly, even though it copes with two more lists of Posns than render-poly.

Conversely, we say that connect-dots generalizes render-poly. Every input for the latter is also an input for the former. Or in terms of data definitions, every Polygon is also an NELoP. But, there are many NELoPs that are **not** Polygons. To be precise, all lists of Posns that contain two items or one belong to NELoP but not to Polygon. The key insight for you is, however, that just because a function has to deal with more inputs than another function does **not** mean that the former is more complex than the latter; generalizations often simplify function definitions.

> This argument is **informal**. If you ever need a **formal** argument for such claims about the relationship between sets or functions, you will need to study logic. Indeed, this book’s design process is deeply informed by logic, and a course on logic in computation is a natural complement. In general, logic is to computing what analysis is to engineering.

As spelled out above, render-polygon can use connect-dots to connect all successive Posns of the given Polygon; to complete its task, it must then add a line from the first to the last Posn of the given Polygon. In terms of code, this just means composing two functions: connect-dots and render-line, but we also need a function to extract the last Posn from the Polygon. Once we are granted this wish, the definition of render-poly is a one-liner: