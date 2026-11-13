# 6.3 Input Errors

One central point of this chapter concerns the role of predicates. They are critical when you must design functions that process mixes of data. Such mixes come up naturally when your problem statement mentions many different kinds of information, but they also come up when you hand your functions and programs to others. After all, you know and respect your data definitions and function signatures. You never know, however, what your friends and colleagues do, and you especially don’t know how someone without knowledge of BSL and programming uses your programs. This section therefore presents one way of protecting programs from inappropriate inputs.

> It is a form of self-delusion to expect that we always respect our own function signatures. Calling a function on the wrong kind of data happens to the best of us. While many languages are like BSL and expect programmers to check signatures on their own, others do so automatically at the cost of some additional complexity.

Let’s demonstrate this point with a simple program, a function for computing the area of a disk:

```
; Number -> Number
; computes the area of a disk with radius r
(define (area-of-disk r)
  (* 3.14 (* r r)))
```

Our friends may wish to use this function for their geometry homework. Unfortunately, when our friends use this function, they may accidentally apply it to a string rather than a number. When that happens, the function stops the program execution with a mysterious error message:

```
> (area-of-disk "my-disk")
*:expects a number as 1st argument, given "my-disk"
```

With predicates, you can prevent this kind of cryptic error message and signal an informative error of your own choice.

Specifically, we can define checked versions of our functions, when we wish to hand them to our friends. Because our friends may not know much BSL, we