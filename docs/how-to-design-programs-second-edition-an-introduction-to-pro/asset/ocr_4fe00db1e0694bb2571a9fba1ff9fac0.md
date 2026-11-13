```
==
(if (< 2 (inf (list 1 0))) 2 (inf (list 1 0)))
```

At this point we can generalize the pattern and summarize it in a table:

| original expression | requires two evaluations of |
|---|---|
| (inf (list 3 2 1 0)) | (inf (list 2 1 0)) |
| (inf (list 2 1 0)) | (inf (list 1 0)) |
| (inf (list 1 0)) | (inf (list 0)) |

In total, the hand-evaluation requires eight recursive steps for a list of four items. If we added 4 to the front of the list, we would double the number of recursive steps again. Speaking algebraically, inf needs on the order of 2^n recursive steps for a list of n numbers when the last number is the maximum, which is clearly the worst case for inf.

Stop! If you paid close attention, you know that the above suggestion is sloppy. The inf program really just needs 2^{n-1} recursive steps for a list of n items. What is going on?

Remember that we don't really measure the exact time when we say “on the order of.” Instead we skip over all built-in predicates, selectors, constructors, arithmetic, and so on and focus on recursive steps only. Now consider this calculation:

```
2^{n-1} = \frac{1}{2} \cdot 2^n .
```

It shows that 2^{n-1} and 2^n differ by a small factor: 2, meaning “on the order of 2^{n-1} steps” describes inf in a world where all basic operations provided by *SL run at half the speed when compared to an inf program that runs at “the order of 2^n steps.” In this sense, the two expressions really mean the same thing. The question is what exactly they mean, and that is the subject of the next section.

**Exercise 484.** While a list sorted in descending order is clearly the worst possible input for inf, the analysis of inf’s abstract running time explains why the rewrite of inf with local reduces the running time. For convenience, we replicate this version here: