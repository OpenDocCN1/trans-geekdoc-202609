
UCs apply to the model, and must be at least as strong as those in the real world. A combination of roles spanned by an internal UC, with no smaller UC inside it, is a `key` of its predicate. A one-role key is a `simple key`.

Because conceptual predicates are elementary, a ternary fact type cannot have a simple key. It either has a three-role UC, or one or more two-role UCs. For a predicate with `n` roles, *each internal UC must span at least n* − 1 *roles*. This *n* − 1 *rule* may be applied as a *key-length check*. Violation of this rule is a sufficient but not necessary condition for splitability.

This rule also implies the following *spanning rule: a UC on an objectified association must normally span all its roles*. Exceptions to this rule are allowed for 1:1 cases and other cases discussed in [Chapter 10](#Ch010_401-479_B9780443237904000244.xhtml).

For a given predicate, let `X` denote a combination of one or more roles (or columns) and `Y` denote a single role (or column). We say `X` functionally determines `Y`, written `X` → `Y`, if and only if for each value of `X` there is at most one value of `Y`. In this case, `Y` is said to be *functionally dependent* on `X`.

The term “*FD*” abbreviates “functional dependency”. If the conceptual schema is correct, all FDs corresponding to actual constraints are implied by UCs. If a nonimplied FD `X` → `Y` exists, the predicate should be split on the source `X`.

With experience, you can usually determine whether a fact type splits by using background knowledge of the UoD to answer the questions, “Can the fact type be rephrased as a conjunction? Is information lost by splitting the fact type?” The shortest key rule and the detection of a nonimplied FD provide simple ways of checking that our intuitions are correct here.

The *projection* on columns `a`, `c`, … of table `T`, written `T[a, c, …]`, is obtained by choosing those columns and removing any duplicate rows from the result. If we know we have a significant population for a fact type, the *projection-join check* can be used to determine whether the fact type is elementary. If we suspect that a predicate might split in a certain way, we can split its significant table in this way by projection and then recombine by natural join: if new instances now appear, the fact type cannot be split in this way. This test is of more theoretical than practical interest.

### Chapter Notes

By depicting each role as a box associated with a table column, ORM enables UCs to be portrayed in a natural way where the impact of the constraint on populations is immediately apparent. Entity relationship (ER) modeling and UML depict internal UCs on associations using a variety of notations for “cardinality constraints” or “multiplicity constraints”, as discussed later. ER and UML offer only partial graphical support for UCs on attributes. Neither ER nor UML offers any significant support for external UCs.

ORM makes minimal use of the notion of functional dependency, but this notion is central to many other methods. For a clear treatment of an ER approach as well as functional dependency theory, see [Elmasri and Navathe (1994)](#Ch004_111-158_B9780443237904000232.xhtml#bb0365).

Although it is generally wise to objectify a predicate only if it has a spanning UC, rare cases may arise where it may be useful to remove this restriction, as discussed in [Chapter 10](#Ch010_401-479_B9780443237904000244.xhtml).

## References[⁶](#fn6)

*   [Elmasri R., Navathe S.](#Ch004_111-158_B9780443237904000232.xhtml#B-bb0365) * Fundamentals of Database Systems.* second ed. Redwood City, CA: Benjamin/Cummings; 1994.

* * *

# 5 Mandatory Roles

## Abstract

This chapter provides an overview of step 5 of ORM conceptual schema design procedure, then discusses simple and disjunctive mandatory role constraints. Simple, compound, and disjunctive reference schemes are examined, and a case study is provided. A logical derivation check procedure is then discussed.

### Keywords

ORM; Mandatory role constraint; Inclusive-or constraint; Reference scheme; Logical derivation check

Chapter Outline

*   5.1 **Introduction to CSDP Step 5**

*   5.2 **Mandatory and Optional Roles**

*   5.3 **Reference Schemes**

*   5.4 **Case Study: A Compact Disc Retailer**

*   5.5 **Logical Derivation Check**

*   5.6 **Summary**

## 5.1 Introduction to CSDP Step 5

So far, we’ve learned how to proceed from familiar information examples to a conceptual schema diagram in which the elementary fact types are clearly set out, with the relevant uniqueness constraints marked on each. We also learned how to perform some checks on the quality of the schemas. In practice, other kinds of constraints and checks need to be considered also.

Next in importance to uniqueness constraints are *mandatory role constraints*. These indicate which roles *must* be played by the population of an object type and which roles are optional. Once mandatory role constraints are specified, a check is made to see if some fact types may be *logically derived* from others. This constitutes the next step in the design procedure.

The next two sections cover this step. This section discusses some basic concepts used in our treatment of mandatory roles and later constraints. Once mandatory roles are understood, we examine reference schemes in depth, especially composite reference—we do this later in the chapter.

Recall that a *type* may be equated with the set of all its possible instances. This is true for both object types and relationship types. For a given schema, types are fixed or unchanging. For a *given state* of the database and a given type `T`, we define `pop(T)`, the **population** of `T`, to be *the set of all instances of T in that state*.

We use “{ }” to denote the *null set*, or *empty set* (the set with no members). When the database is empty, the population of each of its types = { }. As the database is updated, the population may change. For example, suppose the ternary in [Fig. 5.1](#Ch005_159-209_B9780443237904000098.xhtml#f0010) stores information about medals won by countries in the next Olympic Games. The fact type and roles are numbered for easy reference.

![Fig. 5.1 A fact type for Olympic Games results.](images/B9780443237904000098/f05-01-9780443237904.jpg)

[Fig. 5.1](#Ch005_159-209_B9780443237904000098.xhtml#B-f0010) A fact type for Olympic Games results.

Initially the fact table for F1 is empty because no sporting results are known, so `pop(F1)` = { }. Now suppose the database is to be updated after each sporting event, and in the first event the gold and bronze medals are won by the United States and the silver medal by Japan. The new state of the fact table is shown in [Fig. 5.2](#Ch005_159-209_B9780443237904000098.xhtml#f0015), using “G”, “S”, and “B” for gold, silver, and bronze. The population of the fact type now contains three facts, and will grow further each time new results are entered.

![Fig. 5.2 The fact type populated with results of the first event.](images/B9780443237904000098/f05-02-9780443237904.jpg)

[Fig. 5.2](#Ch005_159-209_B9780443237904000098.xhtml#B-f0015) The fact type populated with results of the first event.

We also define the *population of a role*. Each role of a fact type is associated with a column in its fact table. Values entered in the column refer to instances of the object type that plays that role. Given any role `r` and any state of the database:

*   `pop(r)` = population of role `r`
    = set of objects referenced in the column for `r`

Typically, the objects referenced are entities, not values. For example, in [Fig. 5.2](#Ch005_159-209_B9780443237904000098.xhtml#f0015), `pop(r1)` = {The Country with code “US”, The Country with code “JP”}. The *valuation* of a role `r`, written `val(r)`, is the set of values entered in its column. For example, in [Fig. 5.2](#Ch005_159-209_B9780443237904000098.xhtml#f0015), `val(r1)` = {“US”, “JP”}.
