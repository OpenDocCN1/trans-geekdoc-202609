
inheritance. Some of the major commercial systems support extended data types by allowing modules to be plugged in. Such modules may be developed by the vendor or a third party. These modules are variously called “relational extenders”, “datablades”, or “data cartridges”.

The SQL standard has been progressively extended significantly to include several object-oriented features (e.g., user-defined types and functions, encapsulation, support for oids, subtyping, triggered actions, and computational completeness) as well as deductive features (e.g., recursive union).

Given the massive installed base of relational DBMSs, the ongoing extensions to these products, the cost of porting applications to a new data model, and the widespread adoption of the SQL standard, it may well be that the next generation of DBMSs will evolve out of current relational products. Just as Hinduism absorbed features from other religions that threatened its existence, the relational model can probably absorb the interesting features of the object-oriented faith without being replaced by it.

It’s debatable whether all the transformations taking place in SQL-based DBMSs are actually desirable. While the use of extended data types (spatial, video, etc.) is clearly a step forward, the use of constructors (arrays, multisets, etc.) is questionable in many cases because they can make it harder to design efficient databases for ad hoc queries and updates, and they complicate the task of writing good optimizers.

For a detailed critique of the way in which many OO features have been grafted onto the relational model, see Date (2000) and Date and Darwen (1998). At any rate, relational and object-relational systems currently dominate commercially, and other contenders such as object database systems are struggling to gain any significant market share.

SQL includes arrays, row types, and multisets. One challenge then is to model such collections and provide mapping algorithms to implement them efficiently. Various constructors (e.g., for sets, bags, sequences, and schemas) have been added to some versions of ORM and ER. In addition, both ORM and UML allow some kinds of collections to be expressed as mapping annotations on the conceptual schema. Although the use of collection types in conceptual models can facilitate mapping to equivalent implementation structures, it is typically much harder to model complex objects directly at the conceptual level, and they are extremely awkward to validate by verbalization and population. Complex objects also tend to be overused, and simpler solutions are overlooked. For further discussion on collection types, see Chapter 10.

Nowadays, many applications are built using a third-generation language (3GL) such as C# or Java to specify an object model for the transient, in-memory storage, and using SQL to specify a relational or object-relational database for the persistent storage. As data must be moved between the object model and the relational model, considerable effort is spent on the object-relational mapping. Using a tool such as NORMA to generate both object and relational models from ORM models simplifies the task of creating an object-relational mapping process.

## Deductive Database Systems

Logic programming languages such as Prolog are declarative languages based on first-order predicate logic. Facts and derivation rules (including recursive rules) may be declared concisely, with built-in backtracking support.

Datalog combines features from relational database systems and a safe subset of logic programming languages. Unlike Prolog, queries in Datalog are guaranteed to execute in a finite time. Datalog has been used for natural language processing and as a query language for deductive database systems.

Deductive databases offer elegant and powerful ways of managing complex data in a declarative way, especially for information that is derived by use of recursion. This gives them a strong rule enforcement mechanism with built-in backtracking and excellent support for recursive rules. For example, the isAncestorOf relation can be derived from a base parent relation and the following two rules in Horn clause notation:

```
X isAncestorOf Y :- X isParentOf Y.             (basis clause)
X isAncestorOf Y :- X isParentOf Z, Z isAncestorOf Y. (recursive clause)
```

Here, the “:-” between the head and body of the rule means “if”, and the comma “,” in the body of the rule means “and”. Individual variables in the head of the rule are assumed to be universally quantified, and variables introduced in the body are assumed to be existentially quantified, so the rules are equivalent to the following formulae in predicate logic:

```
∀x,y ( x isAncestorOf y if x isParentOf y )
∀x,y [ x isAncestorOf y if ∃z(x isParentOf z and z isAncestorOf y) ]
```

In contrast, SQL-92 cannot express recursive queries at all. SQL:1999 introduced a recursive union operator, but its syntax is more complex and its execution does not enjoy built-in backtracking.

Various deductive database systems based on or influenced by Prolog or Datalog have been developed, such as LogiQL (Halpin and Rugaber, 2015) and Soufflé (https://github.com/souffle-lang). LogiQL was developed by LogicBlox, but is no longer available since the acquisition of LogicBlox by Predictix in December 2014. Soufflé is an open-source, parallel, logic programming language that includes both an interpreter and a compiler that targets parallel C++.

An extremely powerful programming language that supports deductive database features as well as knowledge graphs is under development by RelationalAI (https://relational.ai), with a likely release date around mid-2024. The system, called RAI, is cloud-based, and its language is called Rel, as its data structures are centered on relations (sets of ordered tuples).

The recursive rule for ancestorhood ∀x,y [ x isAncestorOf y if ∃z(x isParentOf z and z isAncestorOf y) ] may be expressed in Rel by means of the following definition: def isAncestorOf(x, y): exists((z) | isParentOf(x, z) and isAncestorOf(z, y)).

As an indication of the power of Rel, a team of RelationalAI programmers has written a program in Rel that automatically transforms ORM models captured in the free, public-domain version of the NORMA tool into structures in Rel. This transformation is able to map extremely complex ORM models, and can capture essentially all alethic constraints in ORM. At the time of writing, deontic constraints are not supported.

The rest of this section provides a brief overview of the main logical features of the Rel language, and uses examples to illustrate how constraints may be formulated. Table 17.5 summarizes the basic *logical operators* between propositions supported in the Rel language. Multiple syntaxes are supported for each operator. Here, “implies” is used for the *material implication* operator of propositional logic, so “p implies q” is equivalent to “not p or q”.

This differs significantly from the English meaning of “if p then q” because a false proposition materially implies any proposition whatsoever, and a true proposition is materially implied by any proposition. For example, the proposition “Earth is a star” materially implies the proposition “Earth has 10 moons”, and the proposition “Mars is a star” materially implies the proposition “Mars is a planet”.

### Table 17.5 Summary of basic logical operators in the Rel language.

| Symbol | Meaning |
|---|---|
| not | it is not the case that |
| and | and |
| or | inclusive or |
| implies | implies |
| xor | exclusive or |
| iff | if and only if |

We’ll use the ORM schema in Fig. 17.17 to illustrate how mandatory role and uniqueness constraints may be formulated in Rel. Constraint formulations start with “ic” (for “integrity constraint”), followed by a parenthesized list of the individual variables involved and then the detailed constraint expression in braces “{}”.

Assuming the ORM fact type Country has CountryName has been declared in Rel using the binary predicate hasCountryName, the ORM *mandatory role* constraint **Each** Country has **some** CountryName may be expressed as follows:

```
ic (c) { Country(c) implies hasCountryName(c, _) }
```

The head variable c is universally quantified, and the underscore character “_” denotes the anonymous variable, so the constraint expression is equivalent to the following predicate logic formula:

```
∀x [Country(x) → ∃y(x hasCountryName y)].
```
