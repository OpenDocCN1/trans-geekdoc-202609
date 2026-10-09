
*   Entropy and Bayesian Methods. Kluwer, Dordrecht, 1990 (cit. on p. 42).
*   D. o. J. National Security Division. *Conspiracy to Act as Unregistered Agent of a Foreign Government*. 2010 (cit. on p. 49).
*   A. Paszke et al. ‘Automatic differentiation in PyTorch’. In: *31st Conference on Neural Information Processing Systems*. 2017 (cit. on p. 56).
*   J. Salvatier, T. V. Wiecki and C. Fonnesbeck. ‘Probabilistic programming in Python using PyMC$^3$’. In: *PeerJ Computer Science* 2 (Jan. 2016), e55 (cit. on p. 42).
*   P. Sledzinski et al. ‘The current state and perspectives of cannabinoid in cancer biology’. In: *Cancer Medicine* 7.3 (2018), pp. 765–775 (cit. on p. 56).
*   E. B. Starikov. ‘Bayesian Statistical Mechanics: Entropy Enthalpy Compensation and Universal Equation of State at the Tip of Pen’. In *Frontiers in Physics* 6 (2018), p. 2 (cit. on p. 42).

## PART III

## HIGH SCHOOL

## CHAPTER 4

## INFORMATION THEORY

> A basic idea in information theory is that information can be treated very much like a physical quantity, such as mass or energy.
> — Claude Shannon, 1985

### Contents

*   - [Introduction](#)
*   - [Problems](#)
    *   [Logarithms in Information Theory](#)
    *   [Shannon’s Entropy](#)
    *   [Kullback-Leibler Divergence (KLD)](#)
    *   [Classification and Information Gain](#)
    *   [Mutual Information](#)
    *   [Mechanical Statistics](#)
    *   [Jensen’s inequality](#)
*   - [Solutions](#)
    *   [Logarithms in Information Theory](#)
    *   [Shannon’s Entropy](#)
    *   [Kullback-Leibler Divergence](#)
    *   [Classification and Information Gain](#)
    *   [Mutual Information](#)
    *   [Mechanical Statistics](#)
    *   [Jensen’s inequality](#)

### 4.1 Introduction

INDUCTIVE inference, is the problem of reasoning under conditions of incomplete information, or **uncertainty**. According to Shannon’s theory [2], information and uncertainty are two sides of the same coin: the more uncertainty there is, the more information we gain by removing the uncertainty. Entropy plays central roles in many scientific realms ranging from physics and statistics to data science and economics. A basic problem in information theory is encoding large quantities of information [2].

Shannon’s discovery of the fundamental laws of data compression and transmission marked the birth of information theory. In his fundamental paper of 1948, “*A Mathematical Theory of Communication*” [4], Shannon proposed a measure of the uncertainty associated with a random memory-less source, called *Entropy*.

![](img/574135cb1d7125b50cf484d943cdd676_107_0.png)

FIGURE 4.1: Mutual information

Entropy first emerged in thermodynamics in the $18^{th}$ century by Carnot, [1] in his pioneering work on steam entitled “*Reflection on the Motive Power of Fire*” (Fig. 4.2). Subsequently it appeared in statistical mechanics where it was viewed as a measure of *disorder*. However, it was Boltzmann (4.30) who found the connection between entropy and probability, and the notion of information as used by Shannon is a generalization of the notion of entropy. Shannon's entropy shares some instinct with Boltzmann's entropy, and likewise the mathematics developed in information theory is highly relevant in statistical mechanics.

# REFLECTIONS
ON THE
MOTIVE POWER OF HEAT.

FROM THE ORIGINAL FRENCH OF
N.-L.-S. CARNOT,
Graduate of the Polytechnic School.

ACCOMPANIED BY
AN ACCOUNT OF CARNOT'S THEORY.
BY SIR WILLIAM THOMSON (LORD KELVIN).

EDITED BY
R. H. THURSTON, M. A., LL.D., Dr. ENG'G;
Director of Sibley College, Cornell University;
"Officier de l'Instruction Publique de France,"
*etc., etc., etc.*

![](img/574135cb1d7125b50cf484d943cdd676_108_0.png)

The **majority** of candidates I interview fail to come up with an answer to the following question: *what is the entropy of tossing a non-biased coin?* Surprisingly, even after I explicitly provide them with Shannon's formulae for calculating entropy $(4.4)$, many are still unable to calculate simple logarithms. The purpose of this chapter is to present the aspiring data scientist with some of the most significant notions of entropy and to elucidate its relationship to probability. Therefore, it is primarily focused on basic quantities in information theory such as entropy, cross-entropy, conditional entropy, mutual information and Kullback-Leibler divergence, also known as relative entropy. It does not however, discuss more advanced topics such as the concept of active information introduced by Bohn and Hiley $[3]$.

### 4.2 Problems

#### 4.2.1 Logarithms in Information Theory

It is important to note that all numerical calculations in this chapter use the binary logarithm $\log _{2}$. This specific logarithm produces units of bits, the commonly used units of information in the field of information theory.

**PRB-67 ❓ CH.PRB- 4.1.**

*Run the following Python code ([4.3](4.3)) in a Python interpreter. What are the results?*

```python
1  import math
2  import numpy
3  print( math. log(1.0/0.98 )) # Natural log (ln)
4  print( numpy. log(1.0/0.02 )) # Natural log (ln)
5
6  print( math. log10(1.0/0.98 )) # Common log (base 10)
7  print( numpy. log10(1.0/0.02 )) # Common log (base 10)
8
9  print( math. log2(1.0/0.98 )) # Binary log (base 2)
10 print( numpy. log2(1.0/0.02 )) # Binary log (base 2)
```

![](img/574135cb1d7125b50cf484d943cdd676_109_0.png)

**PRB-68 ❓ CH.PRB- 4.2.**

*The three basic laws of logarithms:*

1.  *First law*  
    $$\log A+\log B=\log AB .$$ (4.1)
    
    *Compute the following expression:*
    
    $$\log _{10} 3+\log _{10} 4 .$$

2.  *Second law*  
    $$ \log A^{n}=n \log A . \tag{4.2}$$
    
    *Compute the following expression:*
    
    $$\log _{2} 4^{6} .$$

3.  *Third law*
    $$\log A-\log B=\log \frac{A}{B} . \tag{4.3}$$
    
    *Therefore, subtracting log B from log A results in log $\frac{A}{B}$ . Compute the following expression:*
    
    $$\log _{\mathrm{e}} 15-\log _{\mathrm{e}} 3 .$$

#### 4.2.2 Shannon’s Entropy

**PRB-69 ? CH.PRB- 4.3.**

Write Shannon’s famous general formulae for *uncertainty*.

**PRB-70 ? CH.PRB- 4.4.**

Choose exactly *one, and only one* answer.

1. For an event which is *certain to happen*, what is the entropy?
    *   (a) 1.0
    *   (b) 0.0
    *   (c) *The entropy is undefined*
    *   (d) − 1
    *   (e) 0.5
    *   (f) log$_{2} (N)$, *N* being the number of possible events

2. For *N equiprobable events*, what is the entropy?
    *   (a) 1.0
    *   (b) 0.0
    *   (c) The entropy is undefined
    *   (d) -1
    *   (e) 0.5
    *   (f) log₂(N)

**PRB-71 ❓ CH.PRB- 4.5.**
Shannon found that entropy was the only function satisfying *three natural properties*. Enumerate these properties.

**PRB-72 ❓ CH.PRB- 4.6.**
*In information theory, minus the logarithm of the probability of a symbol (essentially the number of bits required to represent it efficiently in a binary code) is defined to be the* **information** *conveyed by transmitting that symbol. In this context, the entropy can be interpreted as the expected information conveyed by transmitting a single symbol from an alphabet in which the symbols occur with the probabilities* $\pi_k$.
***Mark the correct answer:*** *Information is a/an* **[decrease/increase]** *in uncertainty.*

**PRB-73 ❓ CH.PRB- 4.7.**
*Claude Shannon’s paper* ***“A mathematical theory of communication”*** *[⁴], marked the birth of information theory. Published in 1948, it has become since the Magna Carta of the information age. Describe in your own words what is meant by the term* ***Shannon bit*** *.

**PRB-74 ❓ CH.PRB- 4.8.**
*With respect to the notion of* **surprise** *in the context of information theory:*

1.  *Define what it actually meant by being* **surprised**.
2.  *Describe how it is related to the likelihood of an event happening.*
3.  **True or False:** *The less likely the occurrence of an event, the smaller information it conveys.*

**PRB-75 CH.PRB - 4.9.** *Assume a source of signals that transmits a given message* $a$ *with probability* $P_a$. *Assume further that the message is encoded into an ordered series of ones and zeros (a bit string) and that a receiver has a decoder that converts the bit string back into its respective message.* *Shannon devised a formulae that describes the* **size** *that the mean length of the bit string can be* **compressed to** . *Write the formulae.*

**PRB-76 CH.PR B - 4.10.** *Answer the following questions:*

1.  *Assume a source that provides a constant stream of N* **equally likely** *symbols* $\big \{$ $x_1$, $x_2$, ..., $x_n$ $\big\}$. *What does Shannon's formulae* $\underline{\big(4.4\big)}$ *reduce to in this particular case?*

2.  *Assume that each equiprobable pixel in a monochrome image that is fed to a DL classification pipeline, can have values ranging from 0 to 255. Find the entropy in* **bits** .

**PRB-77 CH.PR B - 4.11.** *Given Shannon's famous general formulae for uncertainty* $\underline{\big(4.4\big)}$ .

![](img/574135cb1d7125b50cf484d943cdd676_112_0.png)

1.  *Plot a graph of the curve of probability vs. uncertainty.*
2.  ***Complete the sentence:*** *The curve is* **[symmetrical / asymmetrical]** .
