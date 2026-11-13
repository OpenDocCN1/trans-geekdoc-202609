local definition, added an accumulator parameter, and renamed the parameter of sum.

Figure 183 shows two side-by-side sketches of hand-evaluations. A comparison immediately suggests the central idea, namely, that sum/a can use the accumulator to add up the numbers it encounters. Concerning the accumulator invariant, the calculations suggest a represents the sum of the numbers encountered so far:

```
(sum.v1 '(10 4))
== (+ 10 (sum.v1 '(4)))
== (+ 10 (+ 4 (sum.v1 '())))
== (+ 10 (+ 4 (+ 0)))
...
== 14

(sum/a '(10 4) a0)
== (sum/a '(4) ... 10 ... a0)
== (sum/a '() ... 4 ... 10 ... a0)
...
== 14
```

# Figure 183: Calculating with accumulator-style templates

a is the sum of the numbers that alon lacks from alon0

For example, the invariant forces the following relationships to hold:

| if | alon0 | is | '(10 4 6) | '(10 4 6) | '(10 4 6) |
|---|---|---|---|---|---|
| and | alon | is | '(4 6) | '(6) | '() |
| then | | a should be | 10 | 14 | 20 |

Given this precise invariant, the rest of the design is straightforward:

```
(define (sum.v2 alon0)
  (local (; [List-of Number] ??? -> Number
          ; computes the sum of the numbers on alon
          ; accumulator a is the sum of the numbers
          ; that alon lacks from alon0
          (define (sum/a alon a)
            (cond
              [(empty? alon) a]
              [else (sum/a (rest alon)
                           (+ (first alon) a))])))
  (sum/a alon0 0)))
```