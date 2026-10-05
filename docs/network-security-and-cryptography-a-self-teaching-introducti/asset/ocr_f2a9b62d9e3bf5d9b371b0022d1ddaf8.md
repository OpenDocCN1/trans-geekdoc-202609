Example 8.5: (DSA) Construct an element of order 103 in the multiplicative group of residues mod 1237

Here, $p = 1237$

```
$q = 103; q$ divides $q, (p)$
```

Let $h = 2$

Then the element of 103 (mod 1237) = $g = (h) \Phi^{p(q)} \mod p$

= (2)^{1236/103} \mod 1237$

= (2)^{12} \mod 1237$

= 385

# 8.9 EXERCISES

+   1. Differentiate between Source Authentication and Source Non-Repudiation. Can Source Non-Repudiation be provided by Symmetric Cryptography? Justify your answer.

+   2. What are the services provided by digital signatures? Does it provide (a) Source Authentication, (b) Data Integrity, and (c) Source Non-Repudiation?

+   3. Differentiate between Message Authentication Code (MAC) and Hash Value. Which one is encrypted?

+   4. What is the strength of MAC? Is MAC a reversible function? If no, does it pose any limitation or is designed to be so?

+   5. What are the characteristics of a good Hash Function?

+   6. What is a Birthday Attack on Digital Signatures? Can it be performed by an “Outsizer”?

+   7. What is the input message size in MD5 and SHA-1?

+   8. What is the Message Digest Size in MD5 and SHA-1?

+   9. What is the number of rounds and steps per round in MD5 and SHA-1?