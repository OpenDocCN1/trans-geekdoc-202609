
## exercise 432.

## 26.3 Structural versus Generative Recursion

The template for algorithms is so general that it includes structurally recursive functions. Consider the left side of figure 153. This template is specialized to deal with one trivial clause and one generative step. If we replace trivial? with empty? and generate with rest, we get a template for list-processing functions; see the right side of figure 153.

```racket
(define (general P)
  (cond
    [(trivial? P) (solve P)]
    [else
     (combine-solutions
      P
      (general
       (generate P)))]))

(define (special P)
  (cond
    [(empty? P) (solve P)]
    [else
     (combine-solutions
      P
      (special (rest P)))]))
```

Figure 153: From generative to structural recursion

**Exercise 437.** Define solve and combine-solutions so that

- special computes the length of its input,
- special negates each number on the given list of numbers, and
- special uppercases the given list of strings.

What do you conclude from these exercises?

Now you may wonder whether there is a real difference between structural recursive design and the one for generative recursion. Our answer is “it depends.” Of course, we could say that all functions using structural recursion are just special cases of generative recursion. This “everything is equal” attitude, however, is of no help if we wish to understand the process of designing functions. It confuses two kinds of design that require different forms of knowledge and that have different consequences. One relies on a systematic data analysis and not much more; the other requires a deep, often mathematical, insight into the problem-solving process itself. One leads programmers to naturally terminating functions; the other requires a termination argument. Conflating these two approaches is unhelpful.

## 26.4 Making Choices

When you interact with a function f that sorts lists of numbers, it is impossible for you to know whether f is `sort<` or `quick-sort<`. The two functions behave in an observably equivalent way. This raises the question of which of the two a programming language should provide. More generally, when we can design a function using structural recursion and generative recursion, we must figure out which one to pick.

> Observable equivalence is a central concept from the study of programming languages.

To illustrate the consequences of this choice, we discuss a classical example from mathematics: the problem of finding the greatest common divisor (gcd) of two positive natural numbers. All such numbers have 1 as divisor in common. On occasion—say, 2 and 3—this is also the only common divisor. Both 6 and 25 are numbers with several divisors:

> John Stone suggested the greatest common divisor as a suitable example.

- 6 is evenly divisible by 1, 2, 3, and 6;
- 25 is evenly divisible by 1, 5, and 25.

And yet, their greatest common divisor is 1. In contrast, 18 and 24 have many common divisors and their greatest common divisor is 6:

- 18 is evenly divisible by 1, 2, 3, 6, 9, and 18;
- 24 is evenly divisible by 1, 2, 3, 4, 6, 8, 12, and 24.

Completing the first three steps of the design recipe is straightforward:

```racket
; N[>= 1] N[>= 1] -> N
; finds the greatest common divisor of n and m
(check-expect (gcd 6 25) 1)
(check-expect (gcd 18 24) 6)
(define (gcd n m) 42)
```

The signature specifies the inputs as natural numbers greater than or equal to 1.

From here we design both a structural and a generative recursive solution.

Since this part of the book is about generative recursion, we merely present a structural solution in figure 154 and leave the design ideas to exercises. Just note that (= (remainder n i) (remainder m i) 0) encodes the idea that both n and m are “evenly divisible” by i.

```racket
(define (gcd-structural n m)
  (local (; N -> N
          ; determines the gcd of n and m less than i
          (define (greatest-divisor<= i)
            (cond
              [(= i 1) 1]
              [else
               (if (= (remainder n i) (remainder m i) 0)
                   i
                   (greatest-divisor<= (- i 1)))])))
  (greatest-divisor<= (min n m))))
```

Figure 154: Finding the greatest common divisor via structural recursion

**Exercise 438.** In your words: how does `greatest-divisor<=` work? Use the design recipe to find the right words. Why does the locally defined `greatest-divisor<=` recur on `(min n m)`?

Although the design of `gcd-structural` is rather straightforward, it is also naive. It simply tests for every number between the smaller of `n` and `m` and `1` whether it divides both `n` and `m` evenly and returns the first such number. For small `n` and `m`, this works just fine. Consider the following example, however:

```
(gcd-structural 101135853 45014640)
```

The result is 177. To get there, `gcd-structural` checks the “evenly divisible” condition for 45014640, that is, it checks 45014640 - 177 remainders. Checking that many remainders—twice!—is a large effort, and even reasonably fast computers need time to complete this task.

**Exercise 439.** Copy `gcd-structural` into DrRacket and evaluate

```
(time (gcd-structural 101135853 45014640))
```

in the interactions area.

Since mathematicians recognized the inefficiency of this structural function a long time ago, they studied the problem of finding divisors in depth. The essential insight is that

for two natural numbers, L for **large** and s for **small**, the greatest common divisor is equal to the greatest common divisor of s and the remainder of L divided by s.

Here is how we can articulate this insight as an equation:

```
(gcd L S) == (gcd S (remainder L S))
```

Since `(remainder L S)` is smaller than both L and s, the right-hand side use of gcd consumes s first.

Here is how this insight applies to our small example:

- The given numbers are 18 and 24.
- According to the insight, they have the same gcd as 18 and 6.
- And these two have the same greatest common divisor as 6 and 0.

Now we seem stuck because 0 is unexpected. But, 0 can be evenly divided by every number, meaning we have found our answer: 6.

Working through the example not only validates the basic insight but also suggests how to turn the insight into an algorithm:

- when the smaller of the numbers is 0, we face a trivial case;
- the larger of the two numbers is the solution in the trivial case;
- generating a new problem requires one `remainder` operation; and
- the above equation tells us that the answer to the newly generated problem is also the answer to the originally given problem.

In short, the answers for the four design-recipe questions fall out.

Figure 155 presents the definition of the algorithm. The local definition introduces the workhorse of the function: clever-gcd. Its first cond line discovers the trivial case by comparing smaller to 0 and produces the matching solution. The generative step uses smaller as the new first argument and (remainder large small) as the new second argument to clever-gcd.

```racket
(define (gcd-generative n m)
  (local (; N[>= 1] N[>= 1] -> N
          ; generative recursion
          ; (gcd L S) == (gcd S (remainder L S))
          (define (clever-gcd L S)
            (cond
              [(= S 0) L]
              [else (clever-gcd S (remainder L S))])))
    (clever-gcd (max m n) (min m n))))
```

Figure 155: Finding the greatest common divisor via generative recursion

If we now use gcd-generative with our above example,

```
(gcd-generative 101135853 45014640)
```

we see that the response is nearly instantaneous. A hand-evaluation shows that clever-gcd recurs only nine times before it produces the solution:

```
...
== (clever-gcd 101135853 45014640)
== (clever-gcd 45014640 11106573)
== (clever-gcd 11106573 588348)
== (clever-gcd 588348 516309)
== (clever-gcd 516309 72039)
== (clever-gcd 72039 12036)
== (clever-gcd 12036 11859)
== (clever-gcd 11859 177)
== (clever-gcd 177 0)
```

This also means that it checks only nine remainder conditions, clearly a much smaller effort than gcd-structural expends.
