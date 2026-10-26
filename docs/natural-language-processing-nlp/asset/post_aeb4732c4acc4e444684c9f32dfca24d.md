
is simply the characters a-z. The composed transducer ($T_O \circ T_M$) then transduces from bake+PAST to the spelling baked. The design of $T_O$ is left as an exercise.

## Example: Hidden Markov models

Hidden Markov models (chapter 7) can be viewed as weighted finite state transducers, and they can be constructed by transduction. Recall that a hidden Markov model defines a joint probability over words and tags, p(w, y), which can be computed as a path through a trellis structure. This trellis is itself a weighted finite state acceptor, with edges between all adjacent nodes $q_{m-1,i} \rightarrow q_{m,j}$ on input $Y_m = j$. The edge weights are log-probabilities,

$\delta(q_{m-1,i}, Y_m = j, q_{m,j}) = \log p(w_m, Y_m = j \mid Y_{m-1} = i)$ [9.20]
$= \log p(w_m \mid Y_m = j) + \log \Pr(Y_m = j \mid Y_{m-1} = i).$ [9.21]

Because there is only one possible transition for each tag $Y_m$, this WFSA is deterministic. The score for any tag sequence $\{y_m\}_{m=1}^M$ is the sum of these log-probabilities, corresponding to the total log probability $\log p(w, y)$. Furthermore, the trellis can be constructed by the composition of simpler FSTs.

- First, construct a “transition” transducer to represent a bigram probability model over tag sequences, $T_T$. This transducer is almost identical to the $n$-gram language model acceptor in § 9.1.3: there is one state for each tag, and the edge weights equal to the transition log-probabilities, $\delta(q_i, j, q_j) = \log \Pr(Y_m = j \mid Y_{m-1} = i)$. Note that $T_T$ is a transducer, with identical input and output at each arc; this makes it possible to compose $T_T$ with other transducers.
- Next, construct an “emission” transducer to represent the probability of words given tags, $T_E$. This transducer has only a single state, with arcs for each word/tag pair, $\delta(q_0, i, j, q_0) = \log \Pr(W_m = j \mid Y_m = i)$. The input vocabulary is the set of all tags, and the output vocabulary is the set of all words.
- The composition $T_E \circ T_T$ is a finite state transducer with one state per tag, as shown in Figure 9.8. Each state has $V \times K$ outgoing edges, representing transitions to each of the $K$ other states, with outputs for each of the $V$ words in the vocabulary. The weights for these edges are equal to, $\delta(q_i, Y_m = j, w_m, q_j) = \log p(w_m, Y_m = j \mid Y_{m-1} = i).$ [9.22]
- The trellis is a structure with $M \times K$ nodes, for each of the $M$ words to be tagged and each of the $K$ tags in the tagset. It can be built by composition of $(T_E \circ T_T)$ against an unweighted chain FSA $M_A(w)$ that is specially constructed to accept only a given input $w_1, w_2, \dots, w_M$, shown in Figure 9.9. The trellis for input $w$ is built from the composition $M_A(w) \circ (T_E \circ T_T)$. Composing with the unweighted $M_A(w)$ does not affect the edge weights from $(T_E \circ T_T)$, but it selects the subset of paths that generate the word sequence $w$.

![](img/ba66a8f6f22adeb28512d560b999a231_226_0.png)

Figure 9.11: A context-free grammar for arithmetic expressions

- a finite set of **non-terminals** $N$;
- a finite alphabet $\Sigma$ of **terminal symbols**;
- a set of **production rules** $R$, each of the form $A \to \beta$, where $A \in N$ and $\beta \in (\Sigma \cup N)^*$;
- a designated start symbol $S$.

In the production rule $A \to \beta$, the left-hand side (LHS) $A$ must be a non-terminal; the right-hand side (RHS) can be a sequence of terminals or non-terminals, $\{n,\sigma\}^*$, $n \in N, \sigma \in \Sigma$. A non-terminal can appear on the left-hand side of many production rules. A non-terminal can appear on both the left-hand side and the right-hand side; this is a **recursive production**, and is analogous to self-loops in finite state automata. The name “context-free” is based on the property that the production rule depends only on the LHS, and not on its ancestors or neighbors; this is analogous to Markov property of finite state automata, in which the behavior at each step depends only on the current state, and not on the path by which that state was reached.

A derivation $\tau$ is a sequence of steps from the start symbol $S$ to a surface string $w \in \Sigma^*$, which is the **yield** of the derivation. A string $w$ is in a context-free language if there is some derivation from $S$ yielding $w$. **Parsing** is the problem of finding a derivation for a string in a grammar. Algorithms for parsing are described in chapter 10.

Like regular expressions, context-free grammars define the language but not the computation necessary to recognize it. The context-free analogues to finite state acceptors are **pushdown automata**, a theoretical model of computation in which input symbols can be pushed onto a stack with potentially infinite depth. For more details, see Sipser (2012).

## Example

Figure 9.11 shows a context-free grammar for arithmetic expressions such as $1+2\div3-4$. In this grammar, the terminal symbols include the digits $\{1,\ 2,\ \ldots,\ 9\}$ and the operators $\{+, -, \times, \div\}$. The rules include the $\mid$ symbol, a notational convenience that makes it possible to specify multiple right-hand sides on a single line: the statement $A \to x\mid y$

![](img/ba66a8f6f22adeb28512d560b999a231_227_0.png)

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

## Grammar equivalence and Chomsky Normal Form

A single context-free language can be expressed by more than one context-free grammar. For example, the following two grammars both define the language aⁿbⁿ for n > 0.

```
S → aSb | ab
S → aSb | aabb | ab
```

Two grammars are weakly equivalent if they generate the same strings. Two grammars are strongly equivalent if they generate the same strings via the same derivations. The grammars above are only weakly equivalent.

⁶This is a depth-first left-to-right search that prints each node the first time it is encountered (Cormen et al., 2009, chapter 12).

modify it, such as her younger brother; a verb phrase includes the verb and its modifiers, such as bought a fish and greedily ate it.

In context-free grammars, each phrase type is a non-terminal, and each constituent is the substring that the non-terminal yields. Grammar design involves choosing the right set of non-terminals. Fine-grained non-terminals make it possible to represent more fine-grained linguistic phenomena. For example, by distinguishing singular and plural noun phrases, it is possible to have a grammar of English that generates only sentences that obey subject-verb agreement. However, enforcing subject-verb agreement is considerably more complicated in languages like Spanish, where the verb must agree in both person and number with subject. In general, grammar designers must trade off between overgeneration — a grammar that permits ungrammatical sentences — and undergeneration — a grammar that fails to generate grammatical sentences. Furthermore, if the grammar is to support manual annotation of syntactic structure, it must be simple enough to annotate efficiently.

## 9.2.3 A phrase-structure grammar for English

To better understand how phrase-structure grammar works, let’s consider the specific case of the Penn Treebank grammar of English. The main phrase categories in the Penn Treebank (PTB) are based on the main part-of-speech classes: noun phrase (NP), verb phrase (VP), prepositional phrase (PP), adjectival phrase (ADJP), and adverbial phrase (ADVP). The top-level category is S, which conveniently stands in for both “sentence” and the “start” symbol. Complement clauses (e.g., I take the good old fashioned ground that the whale is a fish) are represented by the non-terminal SBAR. The terminal symbols in the grammar are individual words, which are generated from unary productions from part-of-speech tags (the PTB tagset is described in § 8.1).

This section describes some of the most common productions from the major phrase-level categories, explaining how to generate individual tag sequences. The production rules are approached in a “theory-driven” manner: first the syntactic properties of each phrase type are described, and then some of the necessary production rules are listed. But it is important to keep in mind that the Penn Treebank was produced in a “data-driven” manner. After the set of non-terminals was specified, annotators were free to analyze each sentence in whatever way seemed most linguistically accurate, subject to some high-level guidelines. The grammar of the Penn Treebank is simply the set of productions that were required to analyze the several million words of the corpus. By design, the grammar overgenerates — it does not exclude ungrammatical sentences. Furthermore, while the productions shown here cover some of the most common cases, they are only a small fraction of the several thousand different types of productions in the Penn Treebank.
