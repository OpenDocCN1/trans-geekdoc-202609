teaching program is understood as an exact rational, unless it is prefixed with #i.
Plain Racket interprets all decimal numbers as inexact numbers; it also renders all real numbers as decimals, regardless of whether they are exact or inexact. The implication is that all such numbers are dangerous because they are likely to be inexact approximations of the true number. A programmer can force Racket to interpret numbers with a dot as exact by prefixing numerical constants with #e.

At this point, you may wonder how much a program’s results may differ from the true results if it uses these inexact numbers. This question is one that early computer scientists struggled with a lot, and over the past few decades these studies have created a separate field, called numerical analysis. Every computer scientist, and indeed, every person who uses computers and software, ought to be aware of its existence and some of its basic insights into the workings of numeric programs. As a first taste, the following exercises illustrate how bad things can get. Work through them to never lose sight of the problems of inexact numbers.

> For an accessible introduction—using Racket—read Practically Accurate Floating-Point Math, an article on error analysis by Neil Toronto and Jay McCarthy. It is also fun to watch Debugging Floating-Point Math in Racket, Neil Toronto’s RacketCon 2011 lecture, available on YouTube.

Exercise 417. Evaluate (expt 1.001 1e-12) in Racket and in ISL+. Explain what you see.

Exercise 418. Design my-expt without using expt. The function raises the first given number to the power of the second one, a natural number. Using this function, conduct the following experiment. Add

```
(define inex (+ 1 #i1e-12))
(define exac (+ 1 1e-12))
```

to the definitions area. What is (my-expt inex 30)? And how about (my-expt exac 30)? Which answer is more useful?

Exercise 419. When you add two inexact numbers of vastly different orders of magnitude, you may get the larger one back as the result. For example, if a number system uses only 15 significant digits, we run into problems when adding numbers that vary by more than a factor of 10^16: