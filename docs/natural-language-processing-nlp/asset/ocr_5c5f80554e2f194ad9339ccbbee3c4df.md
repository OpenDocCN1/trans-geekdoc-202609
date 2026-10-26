![](bbox=[0.17, 0.12, 0.88, 0.29])

Figure 9.12: Some example derivations from the arithmetic grammar in Figure 9.11

defines two productions, A → x and A → y. This grammar is recursive: the non-terminals S and NUM can produce themselves.

Derivations are typically shown as trees, with production rules applied from the top to the bottom. The tree on the left in Figure 9.12 describes the derivation of a single digit, through the sequence of productions S → NUM → DIGIT → 4 (these are all unary productions, because the right-hand side contains a single element). The other two trees in Figure 9.12 show alternative derivations of the string 1 + 2 − 3. The existence of multiple derivations for a string indicates that the grammar is ambiguous.

Context-free derivations can also be written out according to the pre-order tree traversal.⁶ For the two derivations of 1 + 2 − 3 in Figure 9.12, the notation is:

```
(S (S (S (Num (Digit 1))) (Op +) (S (Num (Digit 2)))) (Op - ) (S (Num (Digit 3))))  [9.23]
```

```
(S (S (Num (Digit 1))) (Op +) (S (Num (Digit 2)) (Op - ) (S (Num (Digit 3)))))  [9.24]
```

# Grammar equivalence and Chomsky Normal Form

A single context-free language can be expressed by more than one context-free grammar. For example, the following two grammars both define the language aⁿbⁿ for n > 0.

```
S → aSb | ab
S → aSb | aabb | ab
```

Two grammars are weakly equivalent if they generate the same strings. Two grammars are strongly equivalent if they generate the same strings via the same derivations. The grammars above are only weakly equivalent.

⁶This is a depth-first left-to-right search that prints each node the first time it is encountered (Cormen et al., 2009, chapter 12).