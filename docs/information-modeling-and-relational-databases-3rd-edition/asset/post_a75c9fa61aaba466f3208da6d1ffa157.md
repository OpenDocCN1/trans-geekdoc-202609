
other than primary keys). For example, your metaschema should be able to store the following schema:

```
Employee ( empNr, empName, salary, [taxPaid] )
     ^
     |
Drives ( empNr, carRegNr )
```

- 2. Map your answer to Question 1 to a relational metaschema.
- 3. A sample UML class diagram is shown.

![](img/1344db3eba3d550e6edb009556fcd95c_1024_0.png)

Specify a metaschema in ORM notation for simplified UML class diagrams that are restricted to the following features. Classes have attributes only (e.g., no operations). Attributes have visibility (+=public, #=protected, -=private, ~=package) and multiplicity (*=0 or more, 0..1=0 or 1, 1..*=1 or more, 1=exactly 1). Associations may be binary or n-ary. No association classes or qualified associations are allowed. Association ends have multiplicity (*=0 or more, 0..1=0 or 1, 1..*=1 or more, 1=exactly 1). Role names are mandatory (whether or not they are displayed). The only constraints that may be added to a subclassing scheme are disjoint and complete. No derived attributes or derived associations are allowed. No notes are allowed. No aggregation is allowed.

No other graphic constraints (e.g., {ordered}, {xor}, {subset}) or textual constraints are allowed. Ignore our extensions (e.g., {P}, {U1}). Ignore data types. Ignore instance populations and presentation aspects (e.g., layout, or whether the display of a feature is suppressed). Your metaschema should be able to store a single class diagram like the one shown.

- 4. Specify a metaschema in ORM notation for Barker ER (as discussed in Section 8.2). Your metaschema should be able to store a single Barker ER diagram like the one shown.

![](img/1344db3eba3d550e6edb009556fcd95c_1025_0.png)

5. Specify a metaschema in ORM for deterministic, finite-state automata. Two examples of a deterministic automaton are depicted in the transition graphs shown. Each state appears as a named circle. The starting state has a no-input (unlabeled) arrow attached to it. Each automaton has one or more accepting states, depicted as named double-circles. Transitions between states are depicted as labeled arrows from a state to the next state, where the label names the action (or disjunction of actions) causing the state transition.

![](img/1344db3eba3d550e6edb009556fcd95c_1025_1.png)

A sequence of transitions is acceptable (well formed) only if it ends in an accepting state. An accepting state cannot be the start state. The examples have only one accepting state, but your metaschema should allow for multiple accepting states. A finite-state automaton is deterministic if and only if for each action applied to a state, there is only one possible resulting state. Your metaschema should be able to store the information content of single transition graphs like the examples shown.

6. In a *nondeterministic* finite-state automaton, a given action performed on a given state may result in one of many different transitions (we cannot know in advance which transition option will occur for any specific occurrence of the action being applied to the state). For instance, in the following example the action *a* performed on state *s_0_* might cause a transition to state *s_1_* at one time and to state *s′_1_* at another time. Modify your answer to (a) to cater for nondeterministic automata.

![](img/1344db3eba3d550e6edb009556fcd95c_1026_0.png)

## 18.8 Summary

*OLTP* systems are used for typical database applications involving frequent updates and queries. A *data warehouse* is updated only on a scheduled basis from online sources and is used in read-only mode for enterprise-wide analysis of trends by management. *Data marts* are departmental subsets derived from the data warehouse but focused on a single subject area. Data marts are often denormalized for performance reasons and are often based on a “*star schema*” structure with one central “fact” table, referenced by dimension tables. Data warehouses and data marts are used for *OLAP* and data mining. Often a star schema is used to construct a multidimensional structure, or *cube*, containing base and aggregated measures that can be accessed across various dimensions, including time.

Just as information systems can be modeled at different levels, so can they be queried at different levels. Conceptual query languages allow queries to be formulated either in natural language (e.g., English Query) or by selecting and constraining paths on a conceptual schema (e.g., ConQuer). Conceptual query tools automatically transform these higher-level queries into queries in a lower-level language such as SQL. Conceptual queries based on an attribute-free model such as ORM are far more stable when the schema evolves.

With large, complex schemas, there is a need for *abstraction mechanisms* to hide details that are not of immediate relevance. Modularization divides the global schema into conveniently sized subschemas. Constraint layers and textual rules may be toggled off and on as desired. We may zoom in on, or out from, a selected object type, specifying how much of its neighborhood is to be displayed.

Major object types may be identified by their importance in the global schema (e.g., due to having an explicit mandatory role), and the display suppressed for “minor” fact types (those without two roles played by major object types). This view may be refined further by focusing on its major fact types, and so on. Such bottom-up abstraction may be reversed to give top-down refinement.

Minor fact types may also be displayed in terms of attributes of major object types. In this case, ER diagrams and UML class diagrams may be generated as abstractions of ORM diagrams. While such abstractions are good for compact overviews, detailed ORM diagrams are best for developing, transforming, and evolving conceptual schemas.

Although the data model is the foundation of any information systems application, there is also a need to specify *process models* to indicate the permissible *operations* on the data and to design the *external interface*. For such purposes, various diagrams and notations may be used to supplement data model diagrams.

In early stages, informal diagrams such as cartoons can help clarify the UoD, and *function trees* and UML *use case diagrams* may be used to provide overviews of the system requirements. *Data flow diagrams* may also be used to picture information flows among processes, agents, and information stores. However, at some stage a formal connection needs to be made between processes and data. For this purpose, *data use cases* may be used to determine the data model to which processes may be bound (e.g., by defining *operations* on the *major object types*). This can also be used to generate the content (operations) of default screen forms for the external interface. Some default decisions can be made about the format and use of these screens.

Design of the HCI typically requires careful planning by humans. Access rights for different user groups need to be controlled. Users may also differ in their ability level. To make the *user interface* (UI) easy to learn and use, the interface should be consistent, simple, structured, efficient, and adapted to the user. In most cases, a GUI is preferable. The *menu* design needs to provide efficient navigation, and various levels of online and offline help are required.

In information modelling, the term “ontology” is used for a conceptual model that is specifically designed for sharing with other models. The term “semantic web” refers to an enhanced web for the future where documents on the Internet are structured in such a way as to enable automated agents to extract their semantics. Semantic web applications are typically built on top of OWL, which itself is built on top of RDF and RDF Schema, using XML Schema for the tagged textual representation and data types.

RDF breaks down information into atomic units that can be represented as simple (subject, predicate, object) triples denoting a binary relationship, using *URIs* to provide global identifiers for the resources that instantiate the subject, predicates, and object nodes in a triple. An object node may also be instantiated by a literal value (either untyped or typed).

RDF and RDFS are weakly expressive (very few constraints can be captured) but also too relaxed in allowing problematic assertions (e.g., a class may be an instance of itself). Because information on the web is often incomplete, OWL adopts the *open world*
