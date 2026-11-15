
**Bit-flipping:** Note that xor'ing a bit with 0 has no effect, while xor'ing with 1 flips that bit. You can think of \( x \oplus y \) as: "starting with \( x \), flip the bits at all the positions where \( y \) has a 1." So if \( y \) is all 1's, then \( x \oplus y \) gives the bitwise-complement of \( x \). If \( y = 1010 \cdots \) then \( x \oplus y \) means "(the result of) flipping every other bit in \( x \)." Many concepts in this course can be understood in terms of bit-flipping. For example, we might ask "what happens when I flip the first bit of \( x \) and send it into the algorithm?" This kind of question could also be phrased as "what happens when I send \( x \oplus 1000 \cdots \) into the algorithm?" Usually there is nothing special about flipping just the first bit of a string, so it will often be quite reasonable to generalize the question as "what happens when I send \( x \oplus y \) into the algorithm, for an arbitrary (not-all-zeroes) string \( y \)?"

**Addition mod-2:** xor is just addition mod 2 in every bit. This way of thinking about xor helps to explain why "algebraic" things like \( (x \oplus y) \oplus z = x \oplus (y \oplus z) \) are true. They are true for addition, so they are true for xor. This also might help you remember why \( x \oplus x \) is all zeroes. If instead of xor we used addition, we would surely write \( x + x = 2x \). Since \( 2 \equiv_2 0 \), we get that \( 2x \) is congruent to \( 0x = 0 \).

Definition 0.6 (||, concatenation) We write \( x||y \) to denote the result of **concatenating** \( x \) and \( y \).

## 0.4 Functions

Let \( X \) and \( Y \) be finite sets. A function \( f : X \to Y \) is:

**injective** (1-to-1) if it maps distinct inputs to distinct outputs. Formally: \( x \neq x' \Rightarrow f(x) \neq f(x') \). If there is an injective function from \( X \) to \( Y \), then we must have \( |Y| \geq |X| \).

**surjective** (onto) if every element in \( Y \) is a possible output of \( f \). Formally: for all \( y \in Y \) there exists an \( x \in X \) with \( f(x) = y \). If there is a surjective function from \( X \) to \( Y \), then we must have \( |Y| \leq |X| \).

**bijective** (1-to-1 correspondence) if \( f \) is both injective and surjective. If there is a bijective function from \( X \) to \( Y \), then we must have \( |X| = |Y| \).

## 0.5 Probability

Definition 0.7 (Distribution) A **(discrete) probability distribution** over a set \( X \) of **outcomes** is usually written as a function "Pr" that associates each outcome \( x \in X \) with a probability \( \text{Pr}[x] \). We often say that the distribution **assigns** probability \( \text{Pr}[x] \) to outcome \( x \). For each outcome \( x \in X \), the probability distribution must satisfy the condition \( 0 \leq \text{Pr}[x] \leq 1 \). Additionally, the sum of all probabilities \( \sum_{x \in X} \text{Pr}[x] \) must equal 1.

Definition 0.8 (Uniform) A special distribution is the **uniform distribution** over a finite set \( X \), in which every \( x \in X \) is assigned probability \( \text{Pr}[x] = 1/|X| \).

We also extend the notation Pr to **events**, which are collections of outcomes. If you want to be formal, an event A is any subset of the possible outcomes, and its probability is defined to be $\Pr[A] = \sum_{x \in A} \Pr[x]$. We always simplify the notation slightly, so instead of writing $\Pr[\{x \mid x \text{ satisfies some condition}\}]$, we write $\Pr[\text{condition}]$.

**Example** A 6-sided die has faces numbered $\{1, 2, \dots, 6\}$. Tossing the die (at least for a mathematician) induces a uniform distribution over the choice of face. Then $\Pr[\text{3 is rolled}] = 1/6$, and $\Pr[\text{an odd number is rolled}] = 1/2$ and $\Pr[\text{a prime is rolled}] = 1/2$.

### Tips & Tricks

Knowing one of the probabilities $\Pr[A]$ and $\Pr[\neg A]$ (which is “the probability that A doesn’t happen”) tells you exactly what the other probability is, via the relationship

$\Pr[A] = 1 - \Pr[\neg A]$.

This is one of the most basic facts about probability, but it can be surprisingly useful since one of $\Pr[A]$ and $\Pr[\neg A]$ is often much easier to calculate than the other. If you get stuck trying to come up with an expression for $\Pr[A]$, try working out an expression for $\Pr[\neg A]$ instead.

**Example** I roll a six-sided die, six times. What is the probability that there is some repeated value? Let’s think about all the ways of getting a repeated value. Well, two of the rolls could be 1, or three of rolls could be 1, or all of them could be 1, two of them could be 1 and the rest could be 2, etc. Oh no, am I double-counting repeated 2s and repeated 1s? Uhuh... An easier way to attack the problem is to realize that the probability we care about is actually $1 - \Pr[\text{all 6 rolls are distinct}]$. This complementary event (all 6 rolls distinct) happens exactly when the sequence of dice rolls spell out a permutation of $\{1, \dots, 6\}$. There are $6! = 720$ such permutations, out of $6^6 = 46656$ total possible outcomes. Hence, the answer to the question is

$1 - \frac{6!}{6^6} = 1 - \frac{720}{46656} = \frac{45936}{46656} \approx 0.9846$

Another trick is one I like to call **setting breakpoints** on the universe. Imagine stopping the universe at a point where some random choices have happened, and others have not yet happened. This is best illustrated by example:

**Example** A classic question asks: when rolling two 6-sided dice what is the probability that the dice match? Here is a standard (and totally correct way) to answer the question: When rolling two 6-sided dice, there are $6^2 = 36$ total outcomes (a pair of numbers), so each has probability $1/36$ under a uniform distribution. There are 6 outcomes that make the dice match: both dice 1, both dice 2, both dice 3, and so on. Therefore, the probability of rolling matching dice is $6/36 = 1/6$. A different way to arrive at the answer goes like this: Imagine I roll the dice one after another, and I pause the universe (set a breakpoint) after rolling the first die but before rolling the second one. The universe has already decided the result of the first die, so let’s call that value d. The dice will match only if the second roll comes up d. Rolling d on the second die (indeed, rolling any particular value) happens with probability 1/6.

This technique of setting breakpoints is simple but powerful and frequently useful. Some other closely related tricks are: (1) postponing a random choice until the last possible moment, just before its result is used for the first time, and (2) switching the relative order of independent random choices.

### Precise Terminology

It is tempting in this course to say things like “x is a random string.” But a statement like this is sloppy on several accounts.

First, is 42 a random number? Is “heads” a random coin? What is even being asked by these questions? Being “random” is not a property of an outcome (like a number or a side of a coin) but a property of the process that generates an outcome.3 Instead of saying “x is a random string,” it’s much more precise to say “x was chosen randomly.”

Second, usually when we use the word “random,” we don’t mean any old probability distribution. We usually mean to refer to the uniform distribution. Instead of saying “x was chosen randomly,” it’s much more precise to say “x was chosen uniformly” (assuming that really is what you mean).

Every cryptographer I know (yes, even your dear author) says things like “x is a random string” all the time to mean “x was chosen uniformly [from some set of strings].” Usually the meaning is clear from context, at least to the other cryptographers in the room. But all of us could benefit by having better habits about this sloppy language. Students especially will benefit by internalizing the fact that randomness is a property of the process, not of the individual outcome.

## 0.6 Notation in Pseudocode

We’ll often describe algorithms/processes using pseudocode. In doing so, we will use several different operators whose meanings might be easily confused:

- ← When D is a probability distribution, we write “x ← D” to mean “sample x according to the distribution D.”
- If A is an algorithm that takes input and also makes some internal random choices, then it is natural to think of its output A(y) as a distribution — possibly a different distribution for each input y. Then we write “x ← A(y)” to mean the natural thing: “run A on input y and assign the output to x.”

3 There is something called Kolmogorov complexity that can actually give coherent meaning to statements like “x is a random string.” But Kolmogorov complexity has no relevance to this book. The statement “x is a random string” remains meaningless with respect to the usual probability-distribution sense of the word “random.”
