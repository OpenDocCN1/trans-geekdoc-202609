mining may lead to interesting patterns and the “form” of the patterns or rules they want to find. They may also have a sense of “conditions” for the rules, which would eliminate the discovery of certain rules that they know would not be of interest. Thus a good option is to have users specify such intuition or expectations as constraints to confine the search space or perform constraint refinement interactively based on the intermediate mining results. This strategy is known as **constraint-based mining**. The constraints can include the following:

+   - **Knowledge type constraints:** These specify the type of knowledge to be mined, such as association, correlation, classification, or clustering.
+   - **Data constraints:** These specify the set of task-relevant data.
+   - **Dimension/level constraints:** These specify the desired dimensions (or attributes) of the data, the abstraction levels, or the level of these concept hierarchies to be used in mining.
+   - **Interestingness constraints:** These specify thresholds on statistical measures of rule interestingness such as support, confidence, and correlation.
+   - **Rule/pattern constraints:** These specify the form of, or conditions on, the rules/patterns to be mined. Such constraints may be expressed as metarules (rule templates), as the maximum or minimum number of predicates that can occur in the rule antecedent or consequent, or as relationships among attributes, attribute values, and/or aggregates.

These constraints can be specified using a high-level data mining query language or a template-based graphical user interface.

The first four constraint types have already been addressed earlier in the book. In this section, we discuss the use of *rule/pattern constraints* to focus on the mining task. This form of constraint-based mining allows users to describe the rules or patterns that they would like to uncover, thereby making the data mining process more *effective*. In the meantime, a sophisticated mining query optimizer can be used to exploit the constraints specified by the user, thereby making the mining process more *efficient*.

In some cases, a user may like to specify some syntactic form of rules (also called *metarules*) that she is interested in mining. Such syntactic forms help the user to express her expectation and also help the system to confine search space and improve mining efficiency.

For example, a metarule can be in the form of

```
P_1(X, Y) \wedge P_2(X, W) \Rightarrow buys(X, ``iPad''),
(5.11)
```

where $P_1$ and $P_2$ are **predicate variables** that can be instantiated to attributes in a given database during the mining process, $X$ is a variable representing a customer, and $Y$ and $W$ take on values of the attributes assigned to $P_1$ and $P_2$, respectively. Typically, a user can specify a list of attributes to be considered for instantiation with $P_1$ and $P_2$. Otherwise, a default set may be used.

A metarule forms a hypothesis regarding the relationships that the user is interested in probing or confirming. Following such a template, a system can then mine concrete rules that match the given metarule. Possibly, Rule (5.12) that complies with Metarule (5.11) will be returned as mining results

```
age(X, ``20..29'') \wedge income(X, ``41 K..60 K'') \Rightarrow buys(X, ``iPad'').
(5.12)
```

In order to generate interesting and useful mining results, users may have multiple ways to specify rule/pattern constraints. It is desirable for a mining system to use rule/pattern constraints to prune the search space, that is, to push such constraints deeply into the mining process while still ensure the