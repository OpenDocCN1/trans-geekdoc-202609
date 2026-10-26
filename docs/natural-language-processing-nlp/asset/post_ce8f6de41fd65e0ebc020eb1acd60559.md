
where count(u, v) is the count of instances in which word v was aligned to word u in the training set, and count(u) is the total count of the target word u. The smoothing techniques mentioned in chapter 6 can help to reduce the variance of these probability estimates.

Conversely, if we had an accurate translation model, we could estimate the likelihood of each alignment decision,

q_m(a_m | w^(s), w^(t)) ∝ p(a_m | m, M^(s), M^(t)) × p(w_m^(s) | w_{a_m}^(t)), [18.18]

where q_m(a_m | w^(s), w^(t)) is a measure of our confidence in aligning source word w_m^(s) to target word w_{a_m}^(t). The relative frequencies could then be computed from the expected counts,

θ̂_{u→v} = E_q[count(u, v)] / count(u) [18.19]
E_q[count(u, v)] = Σ_m q_m(a_m | w^(s), w^(t)) × δ(w_m^(s) = v) × δ(w_{a_m}^(t) = u). [18.20]

The expectation-maximization (EM) algorithm proceeds by iteratively updating q_m and θ̂. The algorithm is described in general form in chapter 5. For statistical machine translation, the steps of the algorithm are:

- 1. **E-step**: Update beliefs about word alignment using Equation 18.18.
- 2. **M-step**: Update the translation model using Equations 18.19 and 18.20.

As discussed in chapter 5, the expectation maximization algorithm is guaranteed to converge, but not to a global optimum. However, for IBM Model 1, it can be shown that EM optimizes a convex objective, and global optimality is guaranteed. For this reason, IBM Model 1 is often used as an initialization for more complex alignment models. For more detail, see Koehn (2009).

## 18.2.3 Phrase-based translation

Real translations are not word-to-word substitutions. One reason is that many multiword expressions are not translated literally, as shown in this example from French:

(18.3) Nous allons prendre un verre
We will take a glass
We’ll have a drink

![](img/ba66a8f6f22adeb28512d560b999a231_457_0.png)

Figure 18.4: A phrase-based alignment between French and English, corresponding to example (18.3)

The line we will take a glass is the word-for-word gloss of the French sentence; the translation we’ll have a drink is shown on the third line. Such examples are difficult for word-to-word translation models, since they require translating prendre to have and verre to drink. These translations are only correct in the context of these specific phrases.

Phrase-based translation generalizes on word-based models by building translation tables and alignments between multiword spans. (These “phrases” are not necessarily syntactic constituents like the noun phrases and verb phrases described in chapters 9 and 10.) The generalization from word-based translation is surprisingly straightforward: the translation tables can now condition on multi-word units, and can assign probabilities to multi-word units; alignments are mappings from spans to spans, ((i,j),(k,ℓ)), so that

p(w^(s) | w^(t),A) = ∏_{((i,j),(k,ℓ))∈A} P_{w^(s)|w^(t)}({w^(s)_{i+1},w^(s)_{i+2},…,w^(s)_j} | {w^(t)_{k+1},w^(t)_{k+2},…,w^(t)_ℓ}). [18.21]

The phrase alignment ((i,j),(k,ℓ)) indicates that the span w^(s)_{i+1:j} is the translation of the span w^(t)_{k+1:ℓ}. An example phrasal alignment is shown in Figure 18.4. Note that the alignment set A is required to cover all of the tokens in the source, just as in word-based translation. The probability model p_{w^(s)|w^(t)} must now include translations for all phrase pairs, which can be learned from expectation-maximization just as in word-based statistical machine translation.

## 18.2.4 *Syntax-based translation

The Vauquois Pyramid (Figure 18.1) suggests that translation might be easier if we take a higher-level view. One possibility is to incorporate the syntactic structure of the source, the target, or both. This is particularly promising for language pairs that have consistent syntactic differences. For example, English adjectives almost always precede the nouns that they modify, while in Romance languages such as French and Spanish, the adjective often follows the noun: thus, *angry fish* would translate to *pez (fish) enojado (angry)* in Spanish. In word-to-word translation, these reorderings cause the alignment model to be overly permissive. It is not that the order of *any* pair of English words can be reversed when translating into Spanish, but only adjectives and nouns within a noun phrase. Similar issues arise when translating between verb-final languages such as Japanese (in which verbs usually follow the subject and object), verb-initial languages like Tagalog and classical Arabic, and verb-medial languages such as English.

An elegant solution is to link parsing and translation in a **synchronous context-free grammar** (SCFG; Chiang, 2007).³ An SCFG is a set of productions of the form $X \rightarrow (\alpha, \beta, \sim)$, where $X$ is a non-terminal, $\alpha$ and $\beta$ are sequences of terminals or non-terminals, and $\sim$ is a one-to-one alignment of items in $\alpha$ with items in $\beta$. English-Spanish adjective-noun ordering can be handled by a set of synchronous productions, e.g.,

NP → (DET₁ NN₂ JJ₃, DET₁ JJ₃ NN₂), [18.22]

with subscripts indicating the alignment between the Spanish (left) and English (right) parts of the right-hand side. Terminal productions yield translation pairs,

JJ → (enojado₁, angry₁). [18.23]

A synchronous derivation begins with the start symbol S, and derives a pair of sequences of terminal symbols.

Given an SCFG in which each production yields at most two symbols in each language (Chomsky Normal Form; see § 9.2.1), a sentence can be parsed using only the CKY algorithm (chapter 10). The resulting derivation also includes productions in the other language, all the way down to the surface form. Therefore, SCFGs make translation very similar to parsing. In a weighted SCFG, the log probability $\log P_{S|T}$ can be computed from the sum of the log-probabilities of the productions. However, combining SCFGs with a target language model is computationally expensive, necessitating approximate search algorithms (Huang and Chiang, 2007).

³Earlier approaches to syntactic machine translation includes syntax-driven transduction (Lewis II and Stearns, 1968) and stochastic inversion transduction grammars (Wu, 1997).

Synchronous context-free grammars are an example of **tree-to-tree translation**, because they model the syntactic structure of both the target and source language. In **string-to-tree translation**, string elements are translated into constituent tree fragments, which are then assembled into a translation (Yamada and Knight, 2001; Galley et al., 2004); in **tree-to-string translation**, the source side is parsed, and then transformed into a string on the target side (Liu et al., 2006). A key question for syntax-based translation is the extent to which phrasal constituents align across translations (Fox, 2002), because this governs the extent to which we can rely on monolingual parsers and treebanks. For more on syntax-based machine translation, see the monograph by Williams et al. (2016).

## 18.3 Neural machine translation

Neural network models for machine translation are based on the **encoder-decoder** architecture (Cho et al., 2014). The encoder network converts the source language sentence into a vector or matrix representation; the decoder network then converts the encoding into a sentence in the target language.

$$z = \text{ENCODE}(\boldsymbol{w}^{(s)})\tag{18.24}$$  $$\boldsymbol{w}^{(t)} \mid \boldsymbol{w}^{(s)} \sim \text{DECODE}(\boldsymbol{z}),\tag{18.25}$$

where the second line means that the function DECODE(z) defines the conditional probability p(\boldsymbol{w}^{(t)} \mid \boldsymbol{w}^{(s)}).

The decoder is typically a recurrent neural network, which generates the target language sentence one word at a time, while recurrently updating a hidden state. The encoder and decoder networks are trained end-to-end from parallel sentences. If the output layer of the decoder is a logistic function, then the entire architecture can be trained to maximize the conditional log-likelihood,

$$\log p(\boldsymbol{w}^{(t)} \mid \boldsymbol{w}^{(s)}) = \sum_{m=1}^{M^{(t)}} p(w_m^{(t)} \mid w_{1:m-1}^{(t)}, z)\tag{18.26}$$  $$p(w_m^{(t)} \mid w_{1:m-1}^{(t)}, \boldsymbol{w}^{(s)}) \propto \exp\left(\beta_{w_m^{(t)}} \cdot h_{m-1}^{(t)}\right)\tag{18.27}$$

where the hidden state $h_{m-1}^{(t)}$ is a recurrent function of the previously generated text $\boldsymbol{w}_{1:m-1}^{(t)}$ and the encoding $z$. The second line is equivalent to writing,

$$w_m^{(t)} \mid w_{1:m-1}^{(t)}, \boldsymbol{w}^{(s)} \sim \text{SoftMax}\left(\beta \cdot h_{m-1}^{(t)}\right),\tag{18.28}$$

where $\beta \in \mathbb{R}^{(V^{(t)} \times K)}$ is the matrix of output word vectors for the $V^{(t)}$ words in the target language vocabulary.

The simplest encoder-decoder architecture is the **sequence-to-sequence model** (Sutskever et al., 2014). In this model, the encoder is set to the final hidden state of a **long short-term**
