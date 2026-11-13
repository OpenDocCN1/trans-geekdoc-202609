
## Domain Knowledge

Let’s take a look at these trapezoids. Here are the two possible shapes, with minimal annotations to reduce clutter:

![](img/19fbe4068996ced0ce42cec7fb82a834_836_0.png)

The left shape assumes f (L) > f (R) while the right one shows the case where f (L) < f (R). Despite the asymmetry, it is still possible to calculate the area of these trapezoids with a single formula:

```
[(R - L) · f(R)] + [1/2 · (R - L) · (f(L) - f(R))]
```

Stop! Convince yourself that this formula adds the area of the triangle to the area of the lower rectangle for the left trapezoid, while it subtracts the triangle from the area of the large rectangle for the right one. Also show that the above formula is equal to

```
1/2 · (R - L) · (f(L) + f(R))
```

This is a mathematical validation of the asymmetry of the formula.

Design the function `integrate-kepler`. That is, turn the mathematical knowledge into an ISL+ function. Adapt the test cases from figure 165 to this use. Which of the three tests fails and by how much? »

### Exercise 459

Another simple integration method divides the area into many small rectangles. Each rectangle has a fixed width and is as tall as the function graph in the middle of the rectangle. Adding up the areas of the rectangles produces an estimate of the area under the function’s graph.

Let’s use R = 10 to stand for the number of rectangles to be considered. Hence the width of each rectangle is

W = (b - a)/R .

The height of one of these rectangles is the value of f at its midpoint. The first midpoint is clearly at a plus half of the width of the rectangle,

S = width/2 ,

which means its area is

W · f(a + S) .

To compute the area of the second rectangle, we must add the width of one rectangle to the first midpoint:

W · f(a + W + S) ,

For the third one, we get

W · f(a + 2 · W + S) .

In general, we can use the following formula for the ith rectangle:

W · f(a + i · W + S) .

The first rectangle has index 0, the last one R - 1.
Using these rectangles, we can now determine the area under the graph:

\sum_{i=0}^{i=R-1} W \cdot f(a + i \cdot W + S) \quad = \quad W \cdot f(a + 0 \cdot W + S)
+
\dots
+
\dots
W \cdot f(a + (R - 1) \cdot W + S) .

Turn the description of the process into an ISL+ function. Adapt the test cases from figure 165 to this case.

The more rectangles the algorithm uses, the closer its estimate is to the actual area. Make R a top-level constant and increase it by factors of 10 until the algorithm's accuracy eliminates problems with an ε value of 0.1.

Decrease ε to 0.01 and increase R enough to eliminate any failing test cases again. Compare the result to exercise 458.

The Kepler method of exercise 458 immediately suggests a divide-and-conquer strategy like binary search introduced in chapter 27.2. Roughly speaking, the algorithm would split the interval into two pieces, recursively compute the area of each piece, and add the two results.

### Exercise 460

Develop the algorithm `integrate-dc`, which integrates a function `f` between the boundaries `a` and `b` using a divide-and-conquer strategy. Use Kepler's method when the interval is sufficiently small.

The divide-and-conquer approach of exercise 460 is wasteful. Consider a function whose graph is level in one part and rapidly changes in another; see figure 166 for a concrete example. For the level part on the graph, it is pointless to keep splitting the interval. It is just as easy to compute the trapezoid for the complete interval as for the two halves. For the “wavy” part, however, the algorithm must continue dividing the interval until the irregularities of the graph are reasonably small.

![](img/19fbe4068996ced0ce42cec7fb82a834_839_0.png)

**Figure 166: A candidate for adaptive integration**

To discover when $f$ is level, we can change the algorithm as follows. Instead of just testing how large the interval is, the new algorithm computes the area of three trapezoids: the given one and the two halves. If the difference between the two is less than the area of a small rectangle of height $\varepsilon$ and width $b - a$,

\(\varepsilon \cdot (b - a)\)

it is safe to assume that the overall area is a good approximation. In other words, the algorithm determines whether $f$ changes so much that it affects the error margin. If so, it continues with the divide-and-conquer approach; otherwise it stops and uses the Kepler approximation.

### Exercise 461

Design integrate-adaptive. That is, turn the recursive process description into an ISL+ algorithm. Make sure to adapt the test cases from figure 165 to this use.

Do not discuss the termination of integrate-adaptive.

Does integrate-adaptive always compute a better answer than either integrate-kepler or integrate-rectangles? Which aspect is integrate-adaptive guaranteed to improve?

## Terminology

The algorithm is called adaptive integration because it automatically allocates time to those parts of the graph that need it and spends little time on the others. Specifically, for those parts of $f$ that are level, it performs just a few calculations; for the other parts, it inspects small intervals to decrease the error margin. Computer science knows many adaptive algorithms, and integrate-adaptive is just one of them.

## 28.3 Project: Gaussian Elimination

Mathematicians not only search for solutions of equations in one variable; they also study whole systems of linear equations:

**Sample Problem** In a bartering world, the values of coal (x), oil (y), and gas (z) are determined by these exchange equations:

```
2 · x + 2 · y + 3 · z = 10
2 · x + 5 · y + 12 · z = 31   (†)
4 · x + 1 · y − 2 · z = 1
```

A solution to such a system of equations consists of a collection of numbers, one per variable, such that if we replace the variable with its corresponding number, the two sides of each equation evaluate to the same number. In our running example, the solution is

```
x = 1, y = 1, and z = 2.
```

We can easily check this claim:

```
2 · 1 + 2 · 1 + 3 · 2 = 10
2 · 1 + 5 · 1 + 12 · 2 = 31
4 · 1 + 1 · 1 − 2 · 2 = 1
```

The three equations reduce to

```
10 = 10, 31 = 31, and 1 = 1.
```

Figure 167 introduces a data representation for our problem domain. It includes an example of a system of equations and its solution. This representation captures the essence of a system of equations, namely, the numeric coefficients of the variables on the left-hand side and the right-hand-side values. The names of the variables don’t play any role because they are like parameters of functions; meaning, as long as they are consistently renamed the equations have the same solutions.

```scheme
; An SOE is a non-empty Matrix.
; constraint for (list r1 ... rn), (length ri) is (+ n 1)
; interpretation represents a system of equations

; An Equation is a [List-of Number].
; constraint an Equation contains at least two numbers.
; interpretation if (list a1 ... an b) is an Equation,
; a1, ..., an are the left-hand-side variable coefficients
; and b is the right-hand side

; A Solution is a [List-of Number]

(define M ; an SOE
  (list (list 2 2 3 10) ; an Equation
        (list 2 5 12 31)
        (list 4 1 -2 1)))

(define S '(1 1 2)) ; a Solution
```

**Figure 167: A data representation for systems of equations**

For the rest of this section, it is convenient to use these functions:

```scheme
; Equation -> [List-of Number]
; extracts the left-hand side from a row in a matrix
(check-expect (lhs (first M)) '(2 2 3))
(define (lhs e)
  (reverse (rest (reverse e))))
```

```scheme
; Equation -> Number
; extracts the right-hand side from a row in a matrix
(check-expect (rhs (first M)) 10)
(define (rhs e)
  (first (reverse e)))
```

### Exercise 462

Design the function check-solution. It consumes an SOE and a Solution. Its result is #true if plugging in the numbers from the Solution for the variables in the Equations of the SOE produces equal left-hand-side values and right-hand-side values; otherwise the function produces #false. Use check-solution to formulate tests with check-satisfied.

**Hint** Design the function plug-in first. It consumes the left-hand side of an Equation and a Solution and calculates out the value of the left-hand side when
