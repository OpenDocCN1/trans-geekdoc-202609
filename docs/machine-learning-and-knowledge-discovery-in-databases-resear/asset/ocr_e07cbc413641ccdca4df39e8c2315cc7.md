3. More importantly, we introduce PUTPUT (Probabilistic circuit Understanding Through Pruning Underlying logical Theories). This is a new method that prunes the low probability regions from the circuit (see Fig.1b), as these are less likely to be part of the intended concept, whilst also considering the impact on interpretability (the aggregated entropy). After pruning these regions, we can easily extract a matching logical formula from the circuit (see Fig.1c) that can be inspected and can function as a database query.

Our evaluation demonstrates the effectiveness of our approach on a real-world use case of music playlist generation. Furthermore, a user study shows that aggregated entropy is better fit to measure human interpretability than the standard description length and evaluation on open-source datasets confirms that the method is more generally applicable beyond this use case.

The remainder of the paper is structured as follows. First, we provide the necessary background information and the problem statement in respectively Sects. 2 and 3. Then, in Sects. 4 and 5, we introduce our new description length called aggregated entropy, and our method, called PUTPUT. The empirical evaluation of these is presented afterwards, in Sect. 6. Finally, we discuss related work in Sect. 7 and conclude in Sect. 8.

# 2 Background

We first provide a brief primer on logic formulas, probabilistic circuits and PU learning.

# 2.1 Logic Formulas

A literal is a Boolean variable v or its negation ¬v. A propositional logic formula ψ is inductively defined as a literal, the negation of logic formula ¬ψ1, the conjunction (read ‘and’) of two logic formulas ψ1 ∧ ψ2, or a disjunction (read ‘or’) ψ1 ∨ ψ2, with the expected semantics. A clause C is a literal or disjunction of literals, such as v1 ∨ ¬v2. A formula ψ is said to be in conjunctive normal form (CNF) iff it is a conjunction of clauses, such as (v1 ∨ ¬v2) ∧ (¬v1). A formula ψ is said to be in disjunctive normal form (DNF) iff it is a disjunction of conjunctions of literals, such as (v1 ∧ ¬v2) ∨ (¬v1).

We support categorical variables by admitting Boolean variables that represent equalities. That is, a Boolean variable could represent style=jazz, while another variable represents style=rock. We assume an implicit theory that forbids both variables to be true at the same time. For convenience, we may write style=jazz rather than vstyle=jazz. An example in our context is a value assignment to each categorical variable.

The dual graph Gd(ψ) of a CNF formula ψ is a graph that connects clauses iff they share the same variable [29]. In our context we slightly change this definition to reason over categorical and binary variables. More formally, two clauses C and C' are joined by an edge iff there is a categorical or binary variable that is present in both clauses.