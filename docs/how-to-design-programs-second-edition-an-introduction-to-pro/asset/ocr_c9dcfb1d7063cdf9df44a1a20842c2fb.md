> **Hint** For intertwined data definitions, create one template per data definition. Create them in parallel. Make sure they refer to each other in the same way the data definitions do. **End**

This hint sounds more complicated than it is. For our problem, it means we need three templates:

+   1. one for count, which counts occurrences of symbols in S-exprs;
+   2. one for a function that counts occurrences of symbols in SLs; and
+   3. one for a function that counts occurrences of symbols in Atoms.

And here are three partial templates, with conditionals as suggested by the three data definitions:

```
(define (count sexp sy)
 (cond
   [(atom? sexp) ...]
   [else ...]))
```

```
(define (count-atom at sy)
 (cond
   [(number? at) ...]
   [(string? at) ...]
   [(symbol? at) ...]))
```

```
(define (count-sl sl sy)
 (cond
   [(empty? sl) ...]
   [else ...]))
```

The template for count contains a two-pronged conditional because the data definition for S-expr has two clauses. It uses the atom? function to distinguish the case for Atoms from the case for SLs. The template named count-sl consumes an element of SL and a symbol, and because SL is basically a list, count-sl also contains a two-pronged cond. Finally, count-atom is supposed to work for both Atoms and Symbols. And this means that its template checks for the three distinct forms of data mentioned in the data definition of Atom.

The next step is to take apart compound data in the relevant clauses: