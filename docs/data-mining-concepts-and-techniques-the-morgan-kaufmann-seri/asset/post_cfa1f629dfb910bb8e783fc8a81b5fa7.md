

bugs even if a few other statements are inserted into the pasted program code as long as such an insertion are confined to a predefined maximal gap (for sequential pattern mining).

After identification of copy-pasting blocks, the next step is to find inconsistent blocks in the pasted statements. This can be done easily by comparing the two copy-pasting blocks. If the majority occurrences of one identifier (e.g., “total”) have been changed to another one (e.g., “taken”), the minority unchanged (e.g., the retained “total”) is likely the bug. An “unchanged ratio” can be easily set to identify such “forget to change” errors.

A software bug mining program, CP-Miner, adopting the mining methodology described here, has successfully uncovered many copy-pasting bugs in Linux, Apache, and other open source programs, out of millions of lines of code.

## 5.7 Summary

- The scope of frequent pattern mining research reaches far beyond the basic concepts and methods introduced in Chapter 4 for mining frequent itemsets and associations. This chapter presented a road map of the field, where topics are organized with respect to the kinds of patterns and rules that can be mined, mining methods, and applications.

- In addition to mining for basic frequent itemsets and associations, **advanced forms of patterns** can be mined such as multilevel associations and multidimensional associations, quantitative association rules, rare patterns, and negative patterns. We can also mine high-dimensional patterns and compressed or approximate patterns.

- **Multilevel associations** involve data at more than one abstraction level (e.g., “buys computer” and “buys laptop”). These may be mined using multiple minimum support thresholds. **Multidimensional associations** contain more than one dimension. Techniques for mining such associations differ in how they handle repetitive predicates. **Quantitative association rules** involve quantitative attributes. Discretization, clustering, and statistical analysis that discloses exceptional behavior can be integrated with the pattern mining process.

- **Rare patterns** occur rarely but are of special interest. **Negative patterns** are patterns with components that exhibit negatively correlated behavior. Care should be taken in the definition of negative patterns, with consideration of the null-invariance property. Rare and negative patterns may highlight exceptional behavior in the data, which is likely of interest.

- **Constraint-based mining** strategies can be used to help direct the mining process toward patterns that match users’ intuition or satisfy certain constraints. Many user-specified constraints can be pushed deep into the mining process. Constraints can be categorized into **pattern-pruning** and **data-pruning** constraints. Properties of such constraints include *monotonicity*, *antimonotonicity*, *data-antimonotonicity*, and *succinctness*. Constraints with such properties can be properly incorporated into efficient pattern mining processes.

- Methods have been developed for mining patterns in **high-dimensional space**. This includes a pattern growth approach based on *row enumeration* for mining data sets where the number of dimensions is large and the number of data tuples is small (e.g., for microarray data), as well as mining **colossal patterns** (i.e., patterns of very long length) by a *Pattern-Fusion* method.

- To reduce the number of patterns returned in mining, we can instead mine compressed patterns or approximate patterns. *Compressed patterns* can be mined with representative patterns defined based on the concept of clustering, and approximate patterns can be mined by extracting redundancy-aware top-k patterns (i.e., a small set of k-representative patterns that have not only high significance but also low redundancy with respect to one another).

- Sequential pattern mining is the mining of frequently occurring ordered events or subsequences as patterns. The Apriori pruning principles can be used for pruning in sequential pattern mining, which leads to efficient sequential mining algorithms, such as GSP, SPADE and PrefixSpan. CloSpan is an efficient method for mining closed sequential patterns. Efficient methods have also been developed for mining multidimensional and multilevel sequential patterns and constraint-based sequential pattern mining.

- Subgraph pattern mining is the mining of frequent subgraphs in a collection of graphs. The Apriori pruning principles can be used for pruning in subgraph pattern mining, which leads to efficient subgraph mining algorithms, such as AGM, FSG and gSpan (a pattern-growth approach). CloseGraph is an efficient method for mining closed subgraph patterns. Efficient methods have also been developed for mining other frequent substructure patterns, such as directed graphs, tree structures, and disconnected graphs, mining frequent substructures with user-specified constraints, mining approximate frequent substructures, and mining coherent substructures.

- Pattern mining has broad and interesting applications. Besides popular market analysis application, this chapter discusses phrase mining from massive text and software engineering in software copy-pasting bug mining. For phrase mining, an unsupervised method ToPMine, a weakly supervised method SegPhrase and a distantly supervised method AutoPhrase are introduced. For software copy-pasting bug mining, a methodology adopted in CP-Miner is introduced.

## 5.8 Exercises

- 5.1. Propose and outline a level-shared mining approach to mining multilevel association rules in which each item is encoded by its level position. Design it so that an initial scan of the database collects the count for each item at each concept level, identifying frequent and infrequent items. Comment on the processing cost of mining multilevel associations with this method in comparison to mining single-level associations.

- 5.2. Suppose, as manager of a chain of stores, you would like to use sales transactional data to analyze the effectiveness of your store’s advertisements. In particular, you would like to study how specific factors influence the effectiveness of advertisements that announce a particular category of items on sale. The factors to study are the region in which customers live and the day-of-the-week and time-of-the-day of the ads. Discuss how to design an efficient method to mine the transaction data sets and explain how multidimensional and multilevel mining methods can help you derive a good solution.

- 5.3. Quantitative association rules may disclose exceptional behaviors within a data set, where “exceptional” can be defined based on statistical theory. For example, Section 5.1.3 shows the association rule

```
gender = female => mean_wage = $7.90/hr (overall_mean_wage = $9.02/hr),
```

which suggests an exceptional pattern. The rule states that the average wage for females is only $7.90 per hour, which is a significantly lower wage than the overall average of $9.02 per hour. Discuss how such quantitative rules can be discovered systematically and efficiently in large data sets with quantitative attributes.

- 5.4. In multidimensional data analysis, it is interesting to extract pairs of *similar* cell characteristics associated with substantial changes in measure in a data cube, where cells are considered *similar* if they are related by roll-up (i.e., *ancestors*), drill-down (i.e., *descendants*), or 1-D mutation (i.e., *siblings*) operations. Such an analysis is called **cube gradient analysis**. Suppose the measure of the cube is *average*. A user poses a set of *probe cells* and would like to find their corresponding sets of *gradient cells*, each of which satisfies a certain gradient threshold. For example, find the set of corresponding gradient cells that have an average sale price greater than 20% of that of the given probe cells. Develop an algorithm that mines the set of constrained gradient cells efficiently in a large data cube.

- 5.5. Section 5.1.5 presented various ways of defining negatively correlated patterns. Consider Definition 5.3: “Suppose that itemsets X and Y are both frequent, that is, sup(X) >= min_sup and sup(Y) >= min_sup, where min_sup is the minimum support threshold. If (P(X|Y) + P(Y|X))/2 < epsilon, where epsilon is a negative pattern threshold, then pattern X U Y is a **negatively correlated pattern**.” Design an efficient pattern growth algorithm for mining the set of negatively correlated patterns.

- 5.6. Prove that each entry in the following table correctly characterizes its corresponding **rule constraint** for frequent itemset mining.

| Rule Constraint | Antimonotonic | Monotonic | Succinct |
|---|---|---|---|
| a. v in S | no | yes | yes |
| b. S subset V | yes | no | yes |
| c. min(S) <= v | no | yes | yes |
| d. range(S) <= v | yes | no | no |

- 5.7. The price of each item in a store is nonnegative. The store manager is only interested in mining the rules, following the constraints given below. For each of the following cases, identify the kinds of **constraints** they represent and briefly discuss how to mine such association rules using **constraint-based pattern mining**.

- a. Containing at least one Blu-ray DVD movie.

- b. Containing items with a sum of the prices that is less than $150.

- c. Containing one free item and other items with a sum of the prices that is at least $200, whereas the average price of all the items is between $100 and $500.

- 5.8. Section 5.1.4 introduced a core Pattern-Fusion method for **mining high-dimensional data**. Explain why a long pattern, if existing in the data set, is likely to be discovered by this method.

- 5.9. Section 5.2.1 defined a **pattern distance measure** between closed patterns P1 and P2 as

Pat_Dist(P1, P2) = 1 - |T(P1) ∩ T(P2)| / |T(P1) ∪ T(P2)|,

where T(P1) and T(P2) are the supporting transaction sets of P1 and P2, respectively. Is this a valid distance metric? Show the derivation to support your answer.

- 5.10. Association rule mining often generates a large number of rules, many of which may be similar, thus not containing much novel information. Design an efficient algorithm that **compresses** a large set of patterns into a small compact set. Discuss whether your mining method is robust under different pattern similarity definitions.

