Those machine instructions that cannot be decomposed to primitives are analogous to axioms, as defined earlier.7 It can be demonstrated that primitive machine instructions are, themselves, abstractions of the logic that is defined in hardware, such as digital logic consisting only of NOR and NAND gate combinations.8

+   6 See also the chapter Propositional Logic.
+   7 See also the chapter Computability.
+   8 Related Internet links: https://dev.to/ghoshr/creating-any-boolean-function-with-elementary-logic-gates-4jj6 https://demin.ws/blog/english/2010/04/06/modelling-a-cpu-with-only-one-operation

# 10.9 CURRYING

*Currying* is the process of converting a multi-argument function into a series of single argument functions for the same net output.

In programming language theory, a concept called Curry-Howard isomorphism considers a direct relationship between computer programs and mathematical proofs. In that context, the currying process may be used to decompose abstract functions into their primitive constituent functions. This relates to a process referred to by Haskell Curry as *abstraction elimination*.9

Consider a function *curry* that maps a function f which takes three arguments (inputs), a, b, and c, all at once, to a