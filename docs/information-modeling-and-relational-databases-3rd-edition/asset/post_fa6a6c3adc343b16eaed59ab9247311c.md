
## Chapter Notes

In contrast to our usage, frequency constraints are sometimes defined as the number of times members of an object type population must play a role—frequencies of 0 are then allowed and mean optional. Ring constraints are often discussed in logic books within the context of the theory of dyadic relations, but are rarely discussed in modeling approaches other than ORM. For further discussion of ring constraints in ORM, see Halpin and Curland (2011).

## Entity-Relationship Modeling

### Chapter Outline

- 8.1 Overview of ER
- 8.2 Barker Notation
- 8.3 Information Engineering Notation
- 8.4 IDEF1X
- 8.5 Mapping from ORM to ER
- 8.6 Summary

### 8.1 Overview of ER

The entity-relationship (ER) modeling approach views a business domain in terms of entities that have attributes and participate in relationships. For example, the fact that an employee was born on a date is modeled by a birthdate attribute of the Employee entity type, whereas the fact that an employee works for a department is modeled as a relationship between them. This world view is quite intuitive, and despite the recent rise of unified modeling language (UML) for modeling object-oriented applications, ER is still the most popular data modeling approach for database applications.

In Chapter 1, we argued that object-role modeling (ORM) is better than ER for conceptual analysis. However, ER is widely used, and its diagrams are good for compact summaries, so you should become familiar with at least some of the mainstream ER notations. This is the main purpose of this chapter. A second purpose is to have a closer look at how ORM compares to ER. To save some explanation, we assume that you have already studied the basics of ORM in earlier chapters so that we can examine ER from an ORM perspective.

The ER approach was originally proposed by Dr. Peter Chen in the very first issue of an influential journal (Chen, 1976). Fig. 8.1 is based on examples from this journal paper. Chen's original notation uses rectangles for entity types and diamonds for relationships (binary or longer). Attributes may be defined, but are excluded from the ER diagram. As in ORM, roles are defined as parts played in relationships. Role names may optionally be shown at relationship ends (e.g., Employee plays the worker role in the Proj-Work relationship).

Chen formalized relationships in terms of ordered tuples of entities, allowing the order to be dropped if role names are used (as with attribute names in the relational model). Although not displayed on the ER diagram, relationships may have attributes, but cannot play roles in other relationships. So objectified associations are not fully supported.

![](img/1344db3eba3d550e6edb009556fcd95c_334_0.png)

FIG. 8.1 The original ER notation used by Chen.

![](img/1344db3eba3d550e6edb009556fcd95c_334_1.png)

FIG. 8.2 An ambiguous ER schema.

Roles may be annotated with a maximum cardinality of 1 or many. For example, read left to right, the Proj-Mgr relation is one-to-many (each employee manages zero or more projects, and each project is managed by at most one employee).

As shown in Fig. 8.1, Chen used noun phrases for relationships, eliminating natural verbalization. Even if verb phrases are used, the direction in which relationship names are to be read is formally undecided, unless we add additional marks (e.g., arrows) or rules (e.g., always read from left to right and from top to bottom). For example, does the employee manage the project or does the project manage the employee? Although we can use our background knowledge to informally disambiguate this example, it is easy to find examples of relationships whose direction can only be guessed at by anybody other than the model's creator.

This problem is exacerbated if the verb phrase used to name the relationship is shortened to one word (e.g., "work"), unfortunately still a fairly common practice. As a simple example, is the ER diagram in Fig. 8.2 meant to capture the fact type Person killed Animal, or Animal killed Person? We could disambiguate this diagram by adding role names (e.g., "victim", "killer") but there is no requirement to do so.

Similarly, if we populate the Component relationship in Fig. 8.1 with the pair (a, b), we don't know whether this means a is a component of b, or vice versa. To disambiguate this, we need to add role names (e.g., "subpart", "superpart") or use a verb phrase (e.g., "is a component of") with a defined direction.

A rectangle with a double border denotes a weak entity type. This means that the entity type's identification scheme includes a relationship to another entity type. In Fig. 8.3(a), for example, an instance of Dependant might be identified by having the name "Eve Jones"

![](img/1344db3eba3d550e6edb009556fcd95c_335_0.png)

and being related via the Emp-Dep relation to employee 007. In ORM, this is modeled by a corereferenced object type, as in Fig. 8.3(b).

The arrow tip at the Dependant end of the ER relationship indicates that Dependant is existence dependent on Employee (its existence depends on the existence of the other). Given that Dependant is weak, this is basically redundant.

A far better approach is to introduce the concept of a mandatory role, as in ORM and many other ER versions (e.g., **Each Dependant is a dependant of at least one Employee**). This ability to establish a minimum multiplicity of at least one for any given role was absent from Chen's original notation.

Over time, many variant notations developed. Chen's ER-Designer tool uses hexagons instead of diamonds. One problem with ER is that there are so many versions of it, with no single standard. In industry, two of the most popular versions of pure ER are the Barker and information engineering (IE) notations. These are discussed in the next two sections.

Another popular data modeling notation is IDEF1X, which is a hybrid of ER and relational notation, so it is not a pure ER notation. Nevertheless, many people talk of IDEF1X as a version of ER, so we cover it in this chapter.

The best way to develop an ER or IDEF1X model is to derive it from an ORM model; we briefly discuss mapping from ORM later in the chapter. The UML class diagram notation may be regarded as an extended version of ER, but because of the importance of UML, it is considered separately in the next chapter.

### 8.2 Barker Notation

We use the term “Barker notation” for the ER notation discussed in the classic treatment by Richard Barker (Barker, 1990a). Originating in the late 1980s at CACI in the United Kingdom, the notation was later adopted by Oracle Corporation in its computer-aided software engineering (CASE) design tools. Oracle now supports UML as an alternative to the Barker ER notation. For database applications, many modelers still prefer ER over UML. Embarcadero has basic support for the Barker notation in its EA/Studio product. Although dozens of ER dialects exist, we consider the Barker notation to be the best ER notation with wide support in industry.

Dave Hay, an experienced modeler and fan of Barker notation, argues that “UML is ... not suitable for analyzing business requirements in cooperation with business people” (Hay, 1999b). While UML class diagrams are less than ideal for data modeling, ER, like UML, is attribute-based. As discussed in Chapter 1, using attributes in a conceptual model adds complexity and instability, and makes it harder to validate models using verbalization and sample populations.

Attributes are great for logical design because they allow compact diagrams that directly represent the implementation data structures (e.g., tables or classes). However, for conceptual analysis, we just want to know what the facts and rules are about the business and to communicate this information in sentences so that the model can be understood by the domain experts. Whether some fact ends up in the design as an attribute should not be a conceptual issue.

![](img/1344db3eba3d550e6edb009556fcd95c_336_0.png)

FIG. 8.4 A simple ER model in the Barker notation.

In defense of ER, it can be useful to view a conceptual schema in attribute style to gain a compact but still high-level view of the business domain. For this reason, we value ER, and the NORMA tool for ORM is currently being extended to provide ER diagrams as live views of underlying ORM schemas.

But, as Ron Ross (1998, p. 15) says, “Sponsors of business rule projects must sign off on the sentences—not on graphical data models. Most methodologies and CASE tools have this more or less backwards”. ORM allows the domain expert to inspect ORM models fully verbalized into sentences with examples, making validation much easier and safer.

Now that we've stated our bias up front, let's examine the Barker notation itself. The basic conventions are illustrated in Fig. 8.4. Entity types are shown as soft rectangles (rounded corners) with their name in capitals. Attributes are written below the entity type name. Some constraint information may appear before an attribute name. An octothorpe “#” indicates that the attribute is, or is a component of, the primary identifier of the entity type.

A “*” or heavy dot “•” indicates that the attribute is mandatory (i.e., each instance in the database population of the entity type must have a nonnull value recorded for this attribute). A “◦” indicates the attribute is optional. Some modelers also use a period “.” to indicate that the attribute is not part of the identifier.

Relationships are restricted to binaries (no unaries, ternaries, or longer relationships) and are shown as lines with a relationship name at the end from which that relationship name is to be read. This name placement overcomes the ambiguous direction problem mentioned earlier. Both forward and inverse readings may be displayed for a binary relationship, one on either end of the line. This makes the Barker notation superior to UML for verbalizing relationships.

From an ORM perspective, each end (or half) of a relationship line corresponds to a role. Like ORM, Barker treats role optionality and cardinality as distinct, orthogonal concepts instead of lumping them together into a single concept (e.g., multiplicity in UML).
