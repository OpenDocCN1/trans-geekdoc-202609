
So suppose we wish to combine the circle and the rectangle from above:

```
(define circle1 (mk-circle 3 4 5))
(define rectangle1 (mk-rect 0 3 10 3))
(define union1 (mk-combination circle1 rectangle1))
```

Some points are inside and some outside of this combination:

```
(check-expect (inside? union1 (make-posn 0 0)) #true)
(check-expect (inside? union1 (make-posn 0 9)) #false)
(check-expect (inside? union1 (make-posn -1 3)) #true)
```

Since (make-posn 0 0) is inside both, there is no question that it is inside the combination of the two. In a similar vein, (make-posn 0 -1) is in neither shape, and so it isn’t in the combination. Finally, (make-posn -1 3) is in circle1 but not in rectangle1. But the point must be in the combination of the two shapes because every point that is in one or the other shape is in their combination.

This analysis of examples implies a revision of mk-combination:

```
; Shape Shape -> Shape
(define (mk-combination s1 s2)
  ; Posn -> Boolean
  (lambda (p)
    (or (inside? s1 p) (inside? s2 p))))
```

The or expression says that the result is #true if one of two expressions produces #true: (inside? s1 p) or (inside? s2 p). The first expression determines whether p is in s1 and the second one whether p is in s2. And that is precisely a translation of our above explanation into ISL+.

**Exercise** 298. Design my-animate. Recall that the animate function consumes the representation of a stream of images, one per natural number. Since streams are infinitely long, ordinary compound data cannot represent them. Instead, we use functions:

```
; An ImageStream is a function:
; [N -> Image]
; interpretation a stream s denotes a series of images
```

Here is a data example:

```
; ImageStream
(define (create-rocket-scene height)
  (place-image 🚀 50 height (empty-scene 60 60)))
```

You may recognize this as one of the first pieces of code in the Prologue.

The job of (my-animate s n) is to show the images (s 0), (s 1), and so on at a rate of 30 images per second up to n images total. Its result is the number of clock ticks passed since launched.

**Note** This case is an example where it is possible to write down examples/test cases easily, but these examples/tests per se do not inform the design process of this big-bang function. Using functions as data representations calls for more design concepts than this book supplies.

**Exercise** 299. Design a data representation for finite and infinite sets so that you can represent the sets of all odd numbers, all even numbers, all numbers divisible by 10, and so on.

Design the functions `add-element`, which adds an element to a set; `union`, which combines the elements of two sets; and `intersect`, which collects all elements common to two sets.

**Hint** Mathematicians deal with sets as functions that consume a potential element `ed` and produce `#true` only if `ed` belongs to the set.

## 18 Summary

This third part of the book is about the role of abstraction in program design. Abstraction has two sides: creation and use. It is therefore natural if we summarize the chapter as two lessons:

- **Repeated code patterns call for abstraction**. To abstract means to factor out the repeated pieces of code—the abstraction—and to parameterize over the differences. With the design of proper abstractions, programmers save themselves future work and headaches because mistakes, inefficiencies, and other problems are all in one place. One fix to the abstraction thus eliminates any specific problem once and for all. In contrast, the duplication of code means that a programmer must find all copies and fix all of them when a problem is found.
- Most languages come with a large collection of abstractions. Some are contributions by the language design team; others are added by programmers who use the language. To enable **effective reuse of these abstractions**, their creators must supply the appropriate pieces of documentation—a **purpose statement**, a **signature**, and **good examples** —and programmers use them to apply abstractions.

All programming languages come with the means to build abstractions though some means are better than others. All programmers must get to know the means of abstraction and the abstractions that a language provides. A discerning programmer will learn to distinguish programming languages along these axes.

Beyond abstraction, this third part also introduces the idea that **functions are values, and they can represent information.**

While the idea is ancient for the Lisp family of programming languages (such as ISL+) and for specialists in programming language research, it has only recently gained acceptance in most modern mainstream languages—C#, C++, Java, JavaScript, Perl, Python.

## INTERMEZZO 3: SCOPE AND ABSTRACTION

While the preceding part gets away with explaining local and lambda in an informal manner, the introduction of such abstraction mechanisms really requires additional terminology to facilitate such discussions. In particular, these discussions need words to delineate regions within programs and to refer to specific uses of variables.

This intermezzo starts with a section that defines the new terminology: scope, binding variables, and bound variables. It immediately uses this new capability to introduce two abstraction mechanisms often found in programming languages: for loops and pattern matching. The former is an alternative to functions such as map, build-list, andmap, and the like; the latter abstracts over the conditional in the functions of the first three parts of the book. Both require not only the definition of functions but also the creation of entirely new language constructs, meaning they are not something programmers can usually design and add to their vocabulary.

### Scope

Consider the following two definitions:

```
(define (f x) (+ (* x x) 25))
(define (g x) (+ (f (+ x 1)) (f (- x 1))))
```

Clearly, the occurrences of x in f are completely unrelated to the occurrences of x in the definition of g. We could systematically replace the shaded occurrences with y and the function would still compute the exact same result. In short, the shaded occurrences of x have meaning only inside the definition of f and nowhere else.

At the same time, the first occurrence of x in f is different from the others. When we evaluate (f n), the occurrence of f completely disappears while those of x are replaced with n. To distinguish these two kinds of variable occurrences, we call the x in the function header a binding occurrence and those in the function's body the bound occurrences. We also say that the binding occurrence of x binds all occurrences of x in the body of f. Indeed, people who study programming languages even have a name for the region where a binding occurrence works, namely, its lexical scope.

The definitions of f and g bind two more names: f and g. Their scope is called top-level scope because we think of scopes as nested (see below).

The term free occurrence applies to a variable without any binding occurrence. It is a name without definition, that is, neither the language nor its libraries nor the program associates it with some value. For example, if you were to put the above program into a definitions area by itself and run it, entering f, g, and x at the prompt of the interactions would show that the first two are defined and the last one is not:

```
> f
f
> g
g
> x
x: this variable is not defined
```

The description of lexical scope suggests a pictorial representation of f’s definition:

![](img/19fbe4068996ced0ce42cec7fb82a834_605_0.png)

DrRacket’s “Check Syntax” functionality draws diagrams like these.

Here is an arrow diagram for top-level scope:

```
```scheme
(define (h x)
(f (* 2 x))))
(define (f x)
(+ (* x x) 25))
(define (g x)
(+ (f (+ x 1)) (f (- x 1))))
```
```

Note that the scope of f includes all definitions above and below its definition. The bullet over the first occurrence indicates that it is a binding occurrence. The arrows from the binding occurrence to the bound occurrences suggest the flow of values. When the value of a binding occurrence becomes known, the bound occurrences receive their values from there.

Along similar lines, these diagrams also explain how renaming works. If you wish to rename a function parameter, you search for all bound occurrences in scope and replace them. For example, renaming f’s x to y in the program above means that

```
(define (f x) (+ (* x x) 25))
(define (g x) (+ (f (+ x 1)) (f (- x 1))))
```

changes only two occurrences of x:

```
(define (f y) (+ (* y y) 25))
(define (g x) (+ (f (+ x 1)) (f (- x 1))))
```

**Exercise 300.** Here is a simple ISL+ program:
