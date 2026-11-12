In this sentence, *pen* has two meanings in English: (1) a certain writing utensil, (2) an enclosure where small children can play. Most English–Chinese NMT systems in use at this writing still generate a translation with the first, incorrect meaning. Bar–Hillel (1959) argues that

> > no existing or imaginable program will enable an electronic computer to determine that the word ‘pen’ in the given sentence, within the given context has the second of the above meanings, whereas every reader with a sufficient knowledge of English will do this ‘automatically’.
> 
> (p. 2)

Bar–Hillel further points out that the issue is not one that concerns *translation proper*, i.e., the transition from one language to another. Rather the issue concerns a preliminary stage of this process: the determination of the specific contextual meaning of a word that is semantically ambiguous in isolation. In other words, the challenge lies in the analyzer in the Vauquois triangle.

In the next three sections, we consider the three main MT paradigms that aim to address this problem.

# ## 4.3.2 Rule-based MT

Rule-based machine translation (RBMT) is the oldest approach, and it is still widely used for a large variety of applications for its high throughput, deterministic translations critical for some use-cases and its powerful customization ability. Generally speaking, the process of rule-based MT strictly follows the Vauquois triangle, with analysis often being very advanced, while generation is sometimes reduced to the minimum. Specifically, RBMT uses a database of rules and lexical items to which the rules apply; further, these rules and lexical items can be understood (“readable”) and modified by human interactors, e.g., computer linguists, linguists, and translators (SYSTRAN, 2016).

There are three steps in RBMT: first, the analysis of the sentence in the source language, including part of speech tagging, morphological analysis, semantic analysis, constituent analysis, and dependency analysis. Second, a transfer step creates a series of hard engineered algorithms to represent relevant rules and lexical items based on the analysis, e.g., if the system sees *pen* in English, the system converts it to 笔 (meaning “pen, pencil, writing brush and other types of writing utensils” in Chinese). Third, a generation step executes the algorithms to produce the actual target sentence from the internal representation created in the second step.

A word-for-word approach, or direct translation, was the first RBMT technology used in the Georgetown–IBM experiment. In this experiment, the process of transforming the source sentence into the target sentence, i.e., *translation proper*, was divided into three different steps: first, the words in the text were looked up in a bilingual dictionary; second, the equivalent words of the target language were selected; and third, some simple rearrangements of word order were performed and the results were printed out.