# Chapter 5 : Part 2

# Association Rule Learning

# Eclat

Data Types, Numbers, Operators, Type Conversion, f-strings

# 5.2.1 Eclat algorithm

Eclat stands for Equivalence Class Clustering and Bottom-Up Lattice Traversal and it is an algorithm for association rule mining (which also regards frequent itemset mining).

> Eclat: In this model, only Support value is used, which shows how frequent a set of items occur. Therefore, Eclat is a simplified version of Apriori model.

+   * Association rule mining and frequent itemset mining are easiest to understand in their applications for basket analysis: the goal here is to understand which products are often bought together by shoppers.

+   * These association rules can be used for example
    * for recommender engines (in online shopping) or
    * for store improvement for offline shopping.

> ECLAT for association rule: The Eclat algorithm is not the first algorithm for association rule mining. The foundational algorithm in the domain is the Apriori algorithm. The Apriori algorithm is the first algorithm that was proposed in the domain, it has been improved in terms of computational efficiency (i.e. it makes faster alternatives).

> ECLAT vs FP growth Apori: There are two faster alternatives to the Apriori algorithm that are state-of-the-art:
    * [1] one of them is FP growth
    * [2] the other is ECLAT.

✔✔ Between FP growth and ECLAT there is no obvious winner in terms of execution: it will depend on different data and different settings in the algorithm.

It also talks about the "people who bought also bought". So it's like kind of recommender system and similar to what we have in the Apriori algorithm.

| User ID | Movies liked |
| --- | --- |
| 46578 | Movie1, Movie2, Movie3, Movie4 |
| 98989 | Movie1, Movie2 |
| 71527 | Movie1, Movie2, Movie4 |
| 78981 | Movie1, Movie2 |
| 89192 | Movie2, Movie4 |
| 61557 | Movie1, Movie3 |
| Potential Rules: | Movie1 -> Movie2 |
| | Movie2 -> Movie4 |
| | Movie1 -> Movie3 |

Eclat Algorithm: Eclat stands for Equivalence Class Transformation. This algorithm uses a depth-first search technique to find itemsets in a transaction database. It performs faster than Apriori Algorithm.

In Apriori we use "rules" and these rules have different strengths, and based on the Lift we can judge the strength of a rule.

+   * But in Eclat we are actually going to be talking about rules. Here we are going to be talking sets.
* Here we aren't judging the rules with their strength. We're not selecting rules and we're just seeing what could potentially be and then the Eclat model is responsible for actually going through all of these combinations and telling us what we should focus on.