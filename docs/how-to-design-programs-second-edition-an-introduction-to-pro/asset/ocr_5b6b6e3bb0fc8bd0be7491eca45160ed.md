3. Use the invariant to determine the initial value a0 for a.

4. Also exploit the invariant to determine how to compute the accumulator for the recursive function calls within the definition of function/a.

+   • Exploit the accumulator's knowledge for the design of function/a.
+   For a structurally recursive function, the accumulator's value is typically used in the base case, that is, the cond clause that does not recur. For functions that use generative-recursive functions, the accumulated knowledge might be used in an existing base case, in a new base case, or in the cond clauses that deal with generative recursion.

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