These multiple noun constructions can be combined with adjectival phrases and cardinal numbers, leading to a large number of additional productions.

Recursive noun phrase productions include coordination, prepositional phrase attachment, subordinate clauses, and verb phrase adjuncts:

+   - NP → NP Cc NP e.g., the red and the black [9.37]
+   - NP → NP PP e.g., the President of the Georgia Institute of Technology [9.38]
+   - NP → NP SBAR e.g., a whale which he had wounded [9.39]
+   - NP → NP VP e.g., a whale taken near Shetland [9.40]

These recursive productions are a major source of ambiguity, because the VP and PP non-terminals can also generate NP children. Thus, the the President of the Georgia Institute of Technology can be derived in two ways, as can a whale taken near Shetland in October.

But aside from these few recursive productions, the noun phrase fragment of the Penn Treebank grammar is relatively flat, containing a large of number of productions that go from NP directly to a sequence of parts-of-speech. If noun phrases had more internal structure, the grammar would need fewer rules, which, as we will see, would make parsing faster and machine learning easier. Vadas and Curran (2011) propose to add additional structure in the form of a new non-terminal called a nominal modifier (NML), e.g.,

(9.6) a. (NP (NN crude) (NN oil) (NNS prices)) (PTB analysis) b. (NP (NML (NN crude) (NN oil)) (NNS prices)) (NML-style analysis).

Another proposal is to treat the determiner as the head of a determiner phrase (DP; Abney, 1987). There are linguistic arguments for and against determiner phrases (e.g., Van Eynde, 2006). From the perspective of context-free grammar, DPs enable more structured analyses of some constituents, e.g.,

(9.7) a. (NP (DT the) (JJ white) (NN whale)) (PTB analysis) b. (DP (DT the) (NP (JJ white) (NN whale))) (DP-style analysis).

# Verb phrases

Verb phrases describe actions, events, and states of being. The PTB tagset distinguishes several classes of verb inflections: base form (VB; she likes to snack), present-tense third-person singular (VBZ; she snacks), present tense but not third-person singular (VBP; they snack), past tense (VBD; they snacked), present participle (VBG; they are snacking), and past participle (VBN; they had snacked). Each of these forms can constitute a verb phrase on its

9This tagset is specific to English: for example, VBP is a meaningful category only because English morphology distinguishes third-person singular from all person-number combinations.