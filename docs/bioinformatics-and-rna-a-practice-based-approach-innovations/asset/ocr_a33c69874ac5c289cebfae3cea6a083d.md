![](bbox=[0.226, 0.091, 0.765, 0.21])

# FIGURE 7.6 TAG Adjunction

![](bbox=[0.226, 0.291, 0.765, 0.453])

# FIGURE 7.7 TAG Adjunction into Initial Tree

# 7.5.2 ADJUNCTION

Adjunction is for auxiliary trees. The process of TAG adjunction is as shown in Figure 7.6.

An example of the adjuncton of T into an initial tree is shown in Figure 7.7.

Tree adjoining grammars are more powerful than context free grammar but less powerful than context sensitive grammar.

A subclass of context sensitive grammars called Pair Stochastic Tree Adjoining Grammar (PSTAGs) has been used to predict pseudoknots [34]. They extended the Pair Hidden Markov models on tree structures [84] to include pseudoknots. They have defined two subclasses of TAG – Simple Linear TAG (SLTAG) and Extended Simple Linear TAG (ESLTAG). These subclasses are realized with initial trees and adjunct trees. RNA substructures can be represented with the help of these trees by applying various operations like adjion, derivation, etc. PSTAGs work on the structural alignment concept. It takes as input a pair of linear sequences and a TAG representation of a pseudoknot is produced. Using recurrence relation, a dynamic parser produces structural alignment. Based on probability assigned to all alignments of the TAG tree, the most probable alignment is computed. The advantage of this method is that no training of the model is required. The prediction accuracy of this algorithm can be enhanced by using more powerful grammatical methods at the expense of resource cost. The time complexity of the algorithm is O(KnN^4 + KmN^5), where m and n are the numbers of nodes, K is the number of states in PSTAG and N is the sequence length. Tree adjoining grammar has enough computational capacity to model pseudoknots, but it takes