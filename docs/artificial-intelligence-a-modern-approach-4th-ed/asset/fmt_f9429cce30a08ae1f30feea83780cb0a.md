
# Transformer Architecture and Parsing

## Architecture Description

The transformer architecture is described in five rows. The first row contains five nodes and each node is labeled `Embedding lookup`. Each word of the sentence enters one of the five nodes in the bottom row such that no node has two words entering it. The second and third rows contain five nodes each and the nodes are labeled `RNN` each. The output of the `Embedding lookup` node in each column is fed to `RNN` nodes in corresponding columns of the second and third rows. An arrow toward the right is present between any two adjacent `RNN` nodes in the second row. An arrow toward the left is present between any two adjacent `RNN` nodes in the third row. The fourth row contains ten nodes in five columns. Two nodes are in each column of the fourth row. The outputs of two `RNN` nodes in each column of the second and third rows are fed to the two nodes in the corresponding column of the fourth row. The fifth row contains five nodes labeled `Feedforward`. The outputs of the two nodes in each column of the fourth row are fed to the `Feedforward` node in the corresponding column of the fifth row. The output of the first `Feedforward` node is `class` equals `adverb`. The output of the second `Feedforward` node is `class` equals `pronoun`. The output of the third `Feedforward` node is `class` equals `past tense verb`. The output of the fourth `Feedforward` node is `class` equals `determiner`. The output of the fifth `Feedforward` node is `class` equals `noun`.

×![](images/Fig-342.jpg)

## CYK Algorithm for Parsing

Figure 24.5 The CYK algorithm for parsing. Given a sequence of words, it finds the most probable parse tree for the sequence and its subsequences. The table `P[X, i, k]` gives the probability of the most probable tree of category `X` spanning words `i:k`. The output table `T[X, i, k]` contains the most probable tree of category `X` spanning positions `i` to `k` inclusive. The function `SUBSPANS` returns all tuples `(i,j,k)` covering a span of words `i:k`, with `i ≤ j < k`, listing the tuples by increasing length of the `i:k` span, so that when we go to combine two shorter spans into a longer one, the shorter spans are already in the table. `LEXICALRULES(word)` returns a collection of `(X, p)` pairs, one for each rule of the form `X → word [p]`, and `GRAMMARRULES` gives `(X, Y, Z, p)` tuples, one for each grammar rule of the form `X → Y Z [p]`.

### Chomsky Normal Form

The CYK algorithm uses space of `O(n2m)` for the `P` and `T` tables, where `n` is the number of words in the sentence, and `m` is the number of nonterminal symbols in the grammar, and takes time `O(n3m)`. If we want an algorithm that is guaranteed to work for all possible context-free grammars, then we can’t do any better than that. But actually we only want to parse natural languages, not all possible grammars. Natural languages have evolved to be easy to understand in real time, not to be as tricky as possible, so it seems that they should be amenable to a faster parsing algorithm.

To try to get to `O(n)`, we can apply `A*` search in a fairly straightforward way: each state is a list of items (words or categories), as shown in [Figure 24.4](#Chapter24-03.xhtml#fig24-4). The start state is a list of words, and a goal state is the single item `S`. The cost of a state is the inverse of its probability as defined by the rules applied so far, and there are various heuristics to estimate the remaining distance to the goal; the best heuristics in current use come from machine learning applied to a corpus of sentences.

With the `A*` algorithm we don’t have to search the entire state space, and we are guaranteed that the first parse found will be the most probable (assuming an admissible heuristic). This will usually be faster than CYK, but (depending on the details of the grammar) still slower than `O(n)`. An example result of a parse is shown in [Figure 24.6](#Chapter24-03.xhtml#fig24-6).

Description

The model is described by nine nodes in one row. Rightward arrows point from one node to the next sequentially. The first four nodes are labeled `source LSTM` and the remaining five nodes are labeled `Target LSTM`. The four words of the sentence enter four `source LSTM` nodes. Open angular bracket start close angular bracket is input to the first `Target LSTM` node. The words in the sentence `El hombre es alto` are input to the remaining four `Target LSTM` nodes. The outputs of the `Target LSTM` nodes are `El`, `hombre`, `es`, `alto`, and open angular bracket end close angular bracket.

×![](images/Fig-343.jpg)

Figure 24.6 Parse tree for the sentence “Every wumpus smells” according to the grammar `ξ[0]`. Each interior node of the tree is labeled with its probability. The probability of the tree as a whole is `0.9 × 0.25 × 0.05 × 0.15 × 0.40 × 0.10 = 0.0000675`. The tree can also be written in linear form as `[S [NP [Article every] [Noun wumpus]] [VP [Verb smells]]]`.

Just as with part-of-speech tagging, we can use a beam search for parsing, where at any time we consider only the `b` most probable alternative parses. This means we are not guaranteed to find the parse with highest probability, but (with a careful implementation) the parser can operate in `O(n)` time and still finds the best parse most of the time.

A beam search parser with `b = 1` is called a deterministic parser. One popular deterministic approach is `shift-reduce parsing`, in which we go through the sentence word by word, choosing at each point whether to shift the word onto a stack of constituents, or to reduce the top constituent(s) on the stack according to a grammar rule. Each style of parsing has its adherents within the NLP community. Even though it is possible to transform a shift-reduce system into a `PCFG` (and vice versa), when you apply machine learning to the problem of inducing a grammar, the inductive bias and hence the generalizations that each system will make will be different (Abney et al., 1999).

**Deterministic parser**
**Shift-reduce parsing**

## 24.3.1 Dependency Parsing

There is a widely used alternative syntactic approach called `dependency grammar`, which assumes that syntactic structure is formed by binary relations between lexical items, without a need for syntactic constituents. [Figure 24.7](#Chapter24-03.xhtml#fig24-7) shows a sentence with a dependency parse and a phrase structure parse.

Description

The model is described by the nodes in two rows. Rightward arrows point from one node to the next sequentially. The first row contains five nodes and each node is labeled `source LSTM`. The five words of the sentence enter the `source LSTM` nodes. The second row contains two nodes and each node is labeled `target attentional LSTM`. Open angular bracket start close angular bracket is input to the first `target attentional LSTM` node. The word `La` is input to the second `target attentional LSTM` node. A dashed arrow from the first `target attentional LSTM` points to the first `source LSTM` node. Two dashed arrows from the second `target attentional LSTM` point to the second and third `source LSTM` nodes. The output of the first `target attentional LSTM` node is the word `La`. The output of the second `target attentional LSTM` node is the word `puerta`.

×![](images/Fig-344.jpg)

Figure 24.7 A dependency-style parse (top) and the corresponding phrase structure parse (bottom) for the sentence I detect the smelly wumpus near me.

**Dependency grammar**

In one sense, `dependency grammar` and `phrase structure grammar` are just notational variants. If the phrase structure tree is annotated with the head of each phrase, you can recover the dependency tree from it. In the other direction, we can convert a dependency tree into a phrase structure tree by introducing arbitrary categories (although we might not always get a natural-looking tree this way).
