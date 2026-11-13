
#false as the solution. Figure 181 contains the definition of path-exists.v2?, which is the revision of path-exists?. The definition refers to member?, an ISL+ function.

```
; Node Node SimpleGraph -> Boolean
; is there a path from origin to destination in sg
(check-expect (path-exists.v2? 'A 'E a-sg) #true)
(check-expect (path-exists.v2? 'A 'F a-sg) #false)
(define (path-exists.v2? origin destination sg)
  (local (; Node Node SimpleGraph [List-of Node] -> Boolean
          (define (path-exists?/a origin seen)
            (cond
              [(symbol=? origin destination) #t]
              [(member? origin seen) #f]
              [else (path-exists?/a (neighbor origin sg)
                                    (cons origin seen))])))
    (path-exists?/a origin '())))
```

![](img/19fbe4068996ced0ce42cec7fb82a834_901_0.png)

The definition of path-exists.v2? also eliminates the two minor problems with the first revision. By localizing the definition of the accumulating function, we can ensure that the first call always uses '() as the initial value for seen. And, path-exists.v2? satisfies the exact same signature and purpose statement as the path-exists? function.

Still, there is a significant difference between path-exists.v2? and relative-to-absolute2. Whereas the latter was equivalent to the original function, path-exists.v2? improves on path-exists?. While the latter fails to find an answer for some inputs, path-exists.v2? finds a solution for any simple graph.

**Exercise 492.** Modify the definitions in figure 169 so that the program produces #false, even if it encounters the same origin twice.

## 32 Designing Accumulator-Style Functions

The preceding chapter illustrates the need for accumulating extra knowledge with two examples. In one case, accumulation makes it easy to understand the function and yields one that is far faster than the original version. In the other case, accumulation is necessary for the function to work properly. In both cases, though, the need for accumulation becomes only apparent once a properly designed function exists.

Generalizing from the preceding chapter suggests that the design of accumulator functions has two major aspects:

- 1. the recognition that a function benefits from an accumulator; and
- 2. an understanding of what the accumulator represents.

The first two sections address these two questions. Because the second one is a difficult topic, the third section illustrates it with a series of examples that convert regular functions into accumulating ones.

### 32.1 Recognizing the Need for an Accumulator

Recognizing the need for accumulators is not an easy task. We have seen two reasons, and they are the most prevalent ones. In either case, it is critical that we first built a complete function based on a conventional design recipe. Then we study the function and proceed as follows:

- 1. If a structurally recursive function traverses the result of its natural recursion with an auxiliary, recursive function, consider the use of an accumulator parameter.

Take a look at the definition of invert in figure 182. The result of the recursive application produces the reverse of the rest of the list. It uses add-as-last to add the first item to this reversed list and thus creates the reverse of the entire list. This second, auxiliary function is also recursive. We have thus identified an accumulator candidate.

```
; [List-of X] -> [List-of X]
; constructs the reverse of alox

(check-expect (invert '(a b c)) '(c b a))

(define (invert alox)
  (cond
    [(empty? alox) '()]
    [else
     (add-as-last (first alox) (invert (rest alox)))]))

; X [List-of X] -> [List-of X]
; adds an-x to the end of alox

(check-expect (add-as-last 'a '(c b)) '(c b a))

(define (add-as-last an-x alox)
  (cond
    [(empty? alox) (list an-x)]
    [else
     (cons (first alox) (add-as-last an-x (rest alox)))]))
```

Figure 182: Design with accumulators, a structural example

It is now time to study some hand-evaluations, as in chapter 31.1, to see whether an accumulator helps. Consider the following:

```
(invert '(a b c))
== (add-as-last 'a (invert '(b c)))
== (add-as-last 'a (add-as-last 'b (invert '(c))))
== ...
== (add-as-last 'a (add-as-last 'b '(c)))
== (add-as-last 'a '(c b))
== '(c b a)
```

Stop! Replace the dots with the two missing steps. Then you can see that invert eventually reaches the end of the given list—just like add-as-last—and if it knew which items to put there, there would be no need for the auxiliary function.

- 2. If we are dealing with a function based on generative recursion, we are faced with a much more difficult task. Our goal must be to understand whether the algorithm can fail to produce a result for inputs for which we expect a result. If so, adding a parameter that accumulates knowledge may help. Because these situations are complex, we defer the discussion of an example to chapter 33.

**Exercise 493.** Argue that, in the terminology of intermezzo 5, invert consumes $O(n^2)$ time when the given list consists of $n$ items.

**Exercise 494.** Does the insertion-sort> function from chapter 11.3 need an accumulator? If so, why? If not, why not?

### 32.2 Adding Accumulators

Once you have decided that an existing function should be equipped with an accumulator, take these two steps:

- Determine the knowledge that the accumulator represents, what kind of data to use, and how the knowledge is acquired as data.

For example, for the conversion of relative distances to absolute distances, it suffices to accumulate the total distance encountered so far. As the function processes the list of relative distances, it adds each new relative distance found to the accumulator’s current value. For the routing problem, the accumulator remembers every node encountered. As the path-checking function traverses the graph, it conses each new node on to the accumulator.

In general, you will want to proceed as follows.

- 1. Create an accumulator template:

```
; Domain -> Range
(define (function d0)
  (local (; Domain AccuDomain -> Range
          ; accumulator ...
          (define (function/a d a)
            ...))
    (function/a d0 a0)))
```

Sketch a manual evaluation of an application of function to understand the nature of the accumulator.

- 2. Determine the kind of data that the accumulator tracks.

Write down a statement that explains the accumulator as a relationship between the argument d of the auxiliary function/a and the original argument d0.

**Note** The relationship remains constant, also called **invariant**, over the course of the evaluation. Because of this property, an accumulator statement is often called an _invariant_.

- 3. Use the invariant to determine the initial value a0 for a.

- 4. Also exploit the invariant to determine how to compute the accumulator for the recursive function calls within the definition of function/a.

- Exploit the accumulator's knowledge for the design of function/a.

For a structurally recursive function, the accumulator's value is typically used in the base case, that is, the cond clause that does not recur. For functions that use generative-recursive functions, the accumulated knowledge might be used in an existing base case, in a new base case, or in the cond clauses that deal with generative recursion.

As you can see, the key is the precise description of the role of the accumulator. It is therefore important to practice this skill.

Let's take a look at the invert example:

```
(define (invert.v2 alox0)
(local (; [List-of X] ??? -> [List-of X]
; constructs the reverse of alox
; accumulator ...
(define (invert/a alox a)
(cond
[(empty? alox) ...]
[else
(invert/a (rest alox) ... a ...)])))
(invert/a alox0 ...)))
```

As illustrated in the preceding section, this template suffices to sketch a manual evaluation of an example such as

```
(invert '(a b c))
```

Here is the idea:

```
== (invert/a '(a b c) a0)
== (invert/a '(b c) .... 'a .... a0)
== (invert/a '(c) .... 'b .... 'a .... a0)
== (invert/a '() .... 'c .... 'b .... 'a .... a0)
```

This sketch suggests that invert/a can keep track of all the items it has seen in a list that tracks the difference between alox0 and a in reverse order. The initial value is clearly '(); updating the accumulator inside of invert/a with cons produces exactly the desired value when invert/a reaches '().

Here is a refined template that includes these insights:

```
(define (invert.v2 alox0)
  (local (; [List-of X] [List-of X] -> [List-of X]
          ; constructs the reverse of alox
          ; accumulator a is the list of all those
          ; items on alox0 that precede alox
          ; in reverse order
          (define (invert/a alox a)
            (cond
              [(empty? alox) a]
              [else
               (invert/a (rest alox)
                         (cons (first alox) a))]]))
(invert/a alox0 '()))
```

While the body of the local definition initializes the accumulator with '(), the recursive call uses cons to add the current head of alox to the accumulator. In the base case, invert/a uses the knowledge in the accumulator, the reversed list.

Note how, once again, invert.v2 merely traverses the list. In contrast, invert reprocesses every result of its natural recursion with add-as-last. Stop! Measure how much faster invert.v2 runs than invert.

**Terminology** Programmers use the phrase _accumulator-style function_ to discuss functions that use an accumulator parameter. Examples of functions in accumulator style are relative->absolute/a, invert/a, and path-exists?/a.
