**Bit-flipping:** Note that xor'ing a bit with 0 has no effect, while xor'ing with 1 flips that bit. You can think of \( x \oplus y \) as: "starting with \( x \), flip the bits at all the positions where \( y \) has a 1." So if \( y \) is all 1's, then \( x \oplus y \) gives the bitwise-complement of \( x \). If \( y = 1010 \cdots \) then \( x \oplus y \) means "(the result of) flipping every other bit in \( x \)." Many concepts in this course can be understood in terms of bit-flipping. For example, we might ask "what happens when I flip the first bit of \( x \) and send it into the algorithm?" This kind of question could also be phrased as "what happens when I send \( x \oplus 1000 \cdots \) into the algorithm?" Usually there is nothing special about flipping just the first bit of a string, so it will often be quite reasonable to generalize the question as "what happens when I send \( x \oplus y \) into the algorithm, for an arbitrary (not-all-zeroes) string \( y \)?"

**Addition mod-2:** xor is just addition mod 2 in every bit. This way of thinking about xor helps to explain why "algebraic" things like \( (x \oplus y) \oplus z = x \oplus (y \oplus z) \) are true. They are true for addition, so they are true for xor. This also might help you remember why \( x \oplus x \) is all zeroes. If instead of xor we used addition, we would surely write \( x + x = 2x \). Since \( 2 \equiv_2 0 \), we get that \( 2x \) is congruent to \( 0x = 0 \).

Definition 0.6 ((||, concatenation)) We write \( x||y \) to denote the result of **concatenating** \( x \) and \( y \).

# ## 0.4 Functions

Let \( X \) and \( Y \) be finite sets. A function \( f : X \to Y \) is:

**injective** (1-to-1) if it maps distinct inputs to distinct outputs. Formally: \( x \neq x' \Rightarrow f(x) \neq f(x') \). If there is an injective function from \( X \) to \( Y \), then we must have \( |Y| \geq |X| \).

**surjective** (onto) if every element in \( Y \) is a possible output of \( f \). Formally: for all \( y \in Y \) there exists an \( x \in X \) with \( f(x) = y \). If there is a surjective function from \( X \) to \( Y \), then we must have \( |Y| \leq |X| \).

**bijective** (1-to-1 correspondence) if \( f \) is both injective and surjective. If there is a bijective function from \( X \) to \( Y \), then we must have \( |X| = |Y| \).

# ## 0.5 Probability

Definition 0.7 (Distribution) A **(discrete) probability distribution** over a set \( X \) of **outcomes** is usually written as a function "Pr" that associates each outcome \( x \in X \) with a probability \( \text{Pr}[x] \). We often say that the distribution **assigns** probability \( \text{Pr}[x] \) to outcome \( x \). For each outcome \( x \in X \), the probability distribution must satisfy the condition \( 0 \leq \text{Pr}[x] \leq 1 \). Additionally, the sum of all probabilities \( \sum_{x \in X} \text{Pr}[x] \) must equal 1.

Definition 0.8 (Uniform) A special distribution is the **uniform distribution** over a finite set \( X \), in which every \( x \in X \) is assigned probability \( \text{Pr}[x] = 1/|X| \).