(c) { 1 2 2 3 3 } E { 1 1 1 2 2 3 } F

What do you deduce about the impact of any particular bit pattern on joint entropy? Do you notice any patterns that increase or decrease joint entropy?

+   5. Write an algorithm to determine the conditional entropy of the previous list pairs: (A, B), (C, D), and (E, F).

What do you deduce about the impact of any particular bit pattern on conditional entropy?
Do you notice any patterns that increase or decrease conditional entropy?

+   6. Write an algorithm to compute the mutual information for any two sets, A and B.

Show what happens when there is redundant data encoding for overcoming symbol errors.

What is the implication for redundancy given mutual information?

+   7. Write an algorithm to compute the channel capacity for the following sent and received lists of symbols.

```
{ 1 1 1 2 3 } sent
{ 1 1 1 2 } received
```

Does information rate matter?

+   8. Write an algorithm to decompress and decode the Huffman codes from our example. Recall the set of Huffman codes, as paired with their symbols as follows:

```
{ A:11 C:10 Z:011 X:010 Y:001 B:000 }
```

+   9. Write an algorithm that computes how much compression is afforded by Huffman encoding for a particular message of your choosing.