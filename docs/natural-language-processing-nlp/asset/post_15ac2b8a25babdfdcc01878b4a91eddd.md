
## Sentences

The most common production rule for sentences is,

S → NP VP
[9.28]

which accounts for simple sentences like *Abigail ate the kimchi* — as we will see, the direct object *the kimchi* is part of the verb phrase. But there are more complex forms of sentences as well:

S → ADVP NP VP                Unfortunately Abigail ate the kimchi.        [9.29]
S → S CC S                    Abigail ate the kimchi and Max had a burger.    [9.30]
S → VP                        Eat the kimchi.                               [9.31]

where ADVP is an adverbial phrase (e.g., *unfortunately, very unfortunately*) and CC is a coordinating conjunction (e.g., *and, but*).⁸

## Noun phrases

Noun phrases refer to entities, real or imaginary, physical or abstract: *Asha, the steamed dumpling, parts and labor, nobody, the whiteness of the whale, and the rise of revolutionary syndicalism in the early twentieth century.* Noun phrase productions include “bare” nouns, which may optionally follow determiners, as well as pronouns:

NP → NN | NNS | NNP | PRP                [9.32]
NP → DET NN | DET NNS | DET NNP          [9.33]

The tags NN, NNS, and NNP refer to singular, plural, and proper nouns; PRP refers to personal pronouns, and DET refers to determiners. The grammar also contains terminal productions from each of these tags, e.g., PRP → I | you | we | …

Noun phrases may be modified by adjectival phrases (ADJP; e.g., *the small Russian dog*) and numbers (CD; e.g., *the five pastries*), each of which may optionally follow a determiner:

NP → ADJP NN | ADJP NNS | DET ADJP NN | DET ADJP NNS        [9.34]
NP → CD NNS | DET CD NNS | …                               [9.35]

Some noun phrases include multiple nouns, such as *the liberation movement* and *an antelope horn*, necessitating additional productions:

NP → NN NN | NN NNS | DET NN NN | …        [9.36]

⁸Notice that the grammar does not include the recursive production S → ADVP S. It may be helpful to think about why this production would cause the grammar to overgenerate.

These multiple noun constructions can be combined with adjectival phrases and cardinal numbers, leading to a large number of additional productions.

Recursive noun phrase productions include coordination, prepositional phrase attachment, subordinate clauses, and verb phrase adjuncts:

- NP → NP CC NP e.g., the red and the black [9.37]
- NP → NP PP e.g., the President of the Georgia Institute of Technology [9.38]
- NP → NP SBAR e.g., a whale which he had wounded [9.39]
- NP → NP VP e.g., a whale taken near Shetland [9.40]

These recursive productions are a major source of ambiguity, because the VP and PP non-terminals can also generate NP children. Thus, the President of the Georgia Institute of Technology can be derived in two ways, as can a whale taken near Shetland in October.

But aside from these few recursive productions, the noun phrase fragment of the Penn Treebank grammar is relatively flat, containing a large number of productions that go from NP directly to a sequence of parts-of-speech. If noun phrases had more internal structure, the grammar would need fewer rules, which, as we will see, would make parsing faster and machine learning easier. Vadas and Curran (2011) propose to add additional structure in the form of a new non-terminal called a nominal modifier (NML), e.g.,

(9.6) a. (NP (NN crude) (NN oil) (NNS prices)) (PTB analysis) b. (NP (NML (NN crude) (NN oil)) (NNS prices)) (NML-style analysis).

Another proposal is to treat the determiner as the head of a determiner phrase (DP; Abney, 1987). There are linguistic arguments for and against determiner phrases (e.g., Van Eynde, 2006). From the perspective of context-free grammar, DPs enable more structured analyses of some constituents, e.g.,

(9.7) a. (NP (DT the) (JJ white) (NN whale)) (PTB analysis) b. (DP (DT the) (NP (JJ white) (NN whale))) (DP-style analysis).

## Verb phrases

Verb phrases describe actions, events, and states of being. The PTB tagset distinguishes several classes of verb inflections: base form (VB; she likes to snack), present-tense third-person singular (VBZ; she snacks), present tense but not third-person singular (VBP; they snack), past tense (VBD; they snacked), present participle (VBG; they are snacking), and past participle (VBN; they had snacked). Each of these forms can constitute a verb phrase on its

9This tagset is specific to English: for example, VBP is a meaningful category only because English morphology distinguishes third-person singular from all person-number combinations.

Adjectival phrases extend beyond bare adjectives (ADJP → JJ) in a number of ways:

| Production | Example | Ref |
|---|---|---|
| ADJP → RB JJ | *very hungry* | [9.66] |
| ADJP → RBR JJ | *more hungry* | [9.67] |
| ADJP → JJS JJ | *best possible* | [9.68] |
| ADJP → RB JJR | *even bigger* | [9.69] |
| ADJP → JJ CC JJ | *high and mighty* | [9.70] |
| ADJP → JJ JJ | *West German* | [9.71] |
| ADJP → RB VBN | *previously reported* | [9.72] |

The tags JJR and JJS refer to comparative and superlative adjectives respectively.

All of these phrase types can be coordinated:

| Production | Example | Ref |
|---|---|---|
| PP → PP CC PP | *on time and under budget* | [9.73] |
| ADVP → ADVP CC ADVP | *now and two years ago* | [9.74] |
| ADJP → ADJP CC ADJP | *quaint and rather deceptive* | [9.75] |
| SBAR → SBAR CC SBAR | *whether they want control* | [9.76] |
|  | *or whether they want exports* |  |

## 9.2.4 Grammatical ambiguity

Context-free parsing is useful not only because it determines whether a sentence is grammatical, but mainly because the constituents and their relations can be applied to tasks such as information extraction (chapter 17) and sentence compression (Jing, 2000; Clarke and Lapata, 2008). However, the ambiguity of wide-coverage natural language grammars poses a serious problem for such potential applications. As an example, Figure 9.13 shows two possible analyses for the simple sentence We eat sushi with chopsticks, depending on whether the chopsticks modify eat or sushi. Realistic grammars can license thousands or even millions of parses for individual sentences. Weighted context-free grammars solve this problem by attaching weights to each production, and selecting the derivation with the highest score. This is the focus of chapter 10.

## 9.3 *Mildly context-sensitive languages

Beyond context-free languages lie context-sensitive languages, in which the expansion of a non-terminal depends on its neighbors. In the general class of context-sensitive languages, computation becomes much more challenging: the membership problem for context-sensitive languages is PSPACE-complete. Since PSPACE contains the complexity class NP (problems that can be solved in polynomial time on a non-deterministic Turing

![](img/ba66a8f6f22adeb28512d560b999a231_236_0.png)

![](img/ba66a8f6f22adeb28512d560b999a231_236_1.png)

Figure 9.13: Two derivations of the same sentence

machine), PSPACE-complete problems cannot be solved efficiently if P ≠ NP. Thus, designing an efficient parsing algorithm for the full class of context-sensitive languages is probably hopeless.¹⁰

However, Joshi (1985) identifies a set of properties that define **mildly context-sensitive languages**, which are a strict subset of context-sensitive languages. Like context-free languages, mildly context-sensitive languages are parseable in polynomial time. However, the mildly context-sensitive languages include non-context-free languages, such as the “copy language” {*ww* | *w* ∈ Σ*} and the language *a^m b^n c^m d^n*. Both are characterized by **cross-serial dependencies**, linking symbols at long distance across the string.¹¹ For example, in the language *a^n b^m c^n d^m*, each *a* symbol is linked to exactly one *c* symbol, regardless of the number of intervening *b* symbols.

### 9.3.1 Context-sensitive phenomena in natural language

Such phenomena are occasionally relevant to natural language. A classic example is found in Swiss-German (Shieber, 1985), in which sentences such as *we let the children help Hans paint the house* are realized by listing all nouns before all verbs, i.e., *we the children Hans the house let help paint*. Furthermore, each noun’s determiner is dictated by the noun’s **case marking** (the role it plays with respect to the verb). Using an argument that is analogous to the earlier discussion of center-embedding (§ 9.2), Shieber describes these case marking constraints as a set of cross-serial dependencies, homomorphic to *a^m b^n c^m d^n*, and therefore not context-free.

¹⁰If PSPACE ≠ NP, then it contains problems that cannot be solved in polynomial time on a non-deterministic Turing machine; equivalently, solutions to these problems cannot even be checked in polynomial time (Arora and Barak, 2009).

¹¹A further condition of the set of mildly-context-sensitive languages is *constant growth*: if the strings in the language are arranged by length, the gap in length between any pair of adjacent strings is bounded by some language specific constant. This condition excludes languages such as {*a^{2^n}* | *n* ≥ 0}.
