
The `FP-tree` data structure and `FP-growth` algorithm for finding large item sets without candidate generation were introduced by [Han, Pei, and Yin (2000)](#References_705-736_B978044315888900025X.xhtml#fur246) following pioneering work by [Zaki, Parthasarathy, Ogihara, and Li (1997)](#References_705-736_B978044315888900025X.xhtml#fur587); [Han, Pei, Yin, and Mao (2004)](#References_705-736_B978044315888900025X.xhtml#fur247) give a more comprehensive description. It has been extended in various ways. [Wang, Han, and Pei (2003)](#References_705-736_B978044315888900025X.xhtml#fur549) developed an algorithm called `CLOSET+` to mine closed item sets, that is, sets for which there is no proper superset that has the same support. Finding large, closed item sets provides essentially the same information as finding the complete set of large item sets but produces few redundant rules and thus eases the task that users face when examining the output of the mining process. `GSP`, for `Generalized Sequential Patterns`, is a method based on the `Apriori` algorithm for mining patterns in databases of event sequences ([Srikant and Agrawal, 1996](#References_705-736_B978044315888900025X.xhtml#fur506)). A similar approach to `FP-growth` is used for event sequences by algorithms called `PrefixSpan` ([Pei et al., 2004](#References_705-736_B978044315888900025X.xhtml#fur432)) and `CloSpan` ([Yan, Han, and Afshar, 2003](#References_705-736_B978044315888900025X.xhtml#fur580)) and for graph patterns by algorithms called `gSpan` ([Yan and Han, 2002](#References_705-736_B978044315888900025X.xhtml#fur578)) and `CloseGraph` ([Yan and Han, 2003](#References_705-736_B978044315888900025X.xhtml#fur579)).

[Ceglar and Roddick (2006)](#References_705-736_B978044315888900025X.xhtml#fur86) provide a comprehensive survey of association rule mining. Some authors have worked on integrating association rule mining with classification. For example, [Liu, Hsu, and Ma (1998)](#References_705-736_B978044315888900025X.xhtml#fur366) mine a kind of association rule that they call a “class association rule” and build a classifier on the rules that are found using a technique they call `CBA` (Classification Based on Associations). [Mutter, Hall, and Frank (2004)](#References_705-736_B978044315888900025X.xhtml#fur408) use classification to evaluate the output of confidence-based association rule mining and find that standard learners for classification rules are generally preferable to `CBA` when run time and size of the rule sets is of concern.

## C.4 WEKA Implementations

- Decision trees
  - `J48` (implementation of `C4.5`)
  - `SimpleCart` (minimum cost-complexity pruning à la `CART`, in the `simpleCART` package)
  - `REPTree` (reduced-error pruning)

- Classification rules
  - `JRip` (`RIPPER` rule learner)
  - `Part` (rules from partial decision trees)
  - `Ridor` (ripple-down rule learner, in the `ridor` package)

- Association rules
  - `FPGrowth` (frequent pattern trees).
  - `GeneralizedSequentialPatterns` (find large item trees in sequential data, in the `generalizedSequentialPatterns` package)
  - `CBA` (mining class association rules, in the `classAssociationRules` package)

# Appendix D: Technical details of deep learning

Abstract

This appendix contains technical details and minutiae of deep learning. We cover the `backpropagation` algorithm and its use on `computation graphs` and gradient calculations for `convolutional neural network`. We then cover stochastic deep networks in detail, including using `RBMs` to pretrain `deep autoencoders`, `Boltzmann machines` and `restricted Boltzmann machines`, and models and algorithms that make use of these architectures such as `deep belief networks`.

Key Words

`Deep learning`; `gradient computations`; `backpropagation`; `computation graphs`; `stochastic deep networks`; `restricted Boltzmann machines`; `deep belief networks`

## D.1 Backpropagation Revisited
