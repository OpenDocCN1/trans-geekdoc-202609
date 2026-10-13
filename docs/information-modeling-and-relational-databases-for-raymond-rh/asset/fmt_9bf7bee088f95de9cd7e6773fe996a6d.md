
# Relationships

Relationships are typically restricted to binary associations only, which are shown as named lines connecting the entity types. Relationship names are read left to right and top to bottom. As with the Barker notation, a half-line or line end corresponds to a role in ORM.

Optionality and cardinality settings are indicated by annotating the line ends. To indicate that a role is *optional*, a circle “◯” is placed at the other end of the line, signifying a minimum participation frequency of 0. To indicate that a role is *mandatory*, a stroke “|” is placed at the other end of the line, signifying a minimum participation frequency of 1. After experimenting with different notations for a cardinality of “*many*”, Finkelstein settled on the intuitive crow’s foot symbol suggested by Dr. Gordon Everest.

In conjunction with a minimum frequency of 0 or 1, a stroke “|” is often used to indicate a maximum frequency of 1. With this arrangement, the combination “◯|” indicates “*at most one*” and the combination “||” indicates “*exactly one*”. This is the convention used in this section. However, different IE conventions exist. For example, some assume a maximum cardinality of 1 if no crows foot is used, and hence use just a single “|” for “exactly one”. Clive Finkelstein uses the combination “◯|” to mean “optional but will become mandatory”, which is really a dynamic rather than static constraint; this can be combined with a crow’s foot. Some conventions allow a crow’s foot to mean that the minimum (and hence maximum) frequency is many. When using a version of IE, check which of these conventions applies.

[Fig. 8.20](#Ch008_309-346_B9780443237904000177.xhtml#f0105) shows a simple IE diagram and its equivalent ORM diagram. With IE, as you read an association from left to right, you verbalize the constraint symbols at the right-hand end. Here, each employee occupies exactly one (at least 1 and at most 1) room. Inverse predicates are not always supported in IE, but you can supply them yourself to obtain a verbalization in the other direction, for example, “Each room is occupied by zero or more employees”. As with the Barker notation, a plural form of the entity type name is introduced to deal with the many case.

![Fig. 8.20 The IE diagram (a) is equivalent to the ORM diagram (b).](images/B9780443237904000177/f08-20-9780443237904.jpg)

[Fig. 8.20](#Ch008_309-346_B9780443237904000177.xhtml#B-f0105) The IE diagram (a) is equivalent to the ORM diagram (b).

The IE notation is similar to the Barker notation in showing the maximum frequency of a role by marking the role at the other end. But unlike the Barker notation, the IE notation shows the optionality/mandatory setting at the other end as well. In this sense, IE is like UML (even though different symbols are used). As discussed earlier, there are 16 possible constraint patterns for optionality and cardinality on binary associations. [Fig. 8.21](#Ch008_309-346_B9780443237904000177.xhtml#f0110) shows these cases in IE notation together with the equivalent cases in ORM.

![Fig. 8.21 Equivalent constraint patterns in IE and ORM.](images/B9780443237904000177/f08-21-9780443237904.jpg)

[Fig. 8.21](#Ch008_309-346_B9780443237904000177.xhtml#B-f0110) Equivalent constraint patterns in IE and ORM.

An example using the different notation for IE used by Finkelstein is shown in [Fig. 8.22](#Ch008_309-346_B9780443237904000177.xhtml#f0115). The single bar on the left end of the association indicates that each computer is located in exactly one office. The circle, bar, and crow’s foot on the right-hand role collectively indicate that each office must eventually house one or more computers. Although this “optional becoming mandatory” constraint has no counterpart in ORM and is unsupported by most IE modeling tools, it could be used to refine decisions on how to group fact types into implementation structures.

![Fig. 8.22 In Finkelstein’s version, circle-bar means “optional becoming mandatory”.](images/B9780443237904000177/f08-22-9780443237904.jpg)

[Fig. 8.22](#Ch008_309-346_B9780443237904000177.xhtml#B-f0115) In Finkelstein’s version, circle-bar means “optional becoming mandatory”.

Some modeling tools support the IE notation for *n*:1, 1:*n*, and 1:1 associations but not *m:n* (many to many) associations. For such tools, four of the 16 cases in [Fig. 8.21](#Ch008_309-346_B9780443237904000177.xhtml#f0110) can’t be directly represented. In this situation, you can model the *m:n* cases indirectly by introducing an “*intersection entity type*” with mandatory *n*:1 associations to the original entity types. For example, the *m:n* case with both roles optional may be handled by introducing the object type *C*, as shown in [Fig. 8.23](#Ch008_309-346_B9780443237904000177.xhtml#f0120).

![Fig. 8.23 An m:n association remodeled as an entity type with n:1 associations.](images/B9780443237904000177/f08-23-9780443237904.jpg)

[Fig. 8.23](#Ch008_309-346_B9780443237904000177.xhtml#B-f0120) An *m:n* association remodeled as an entity type with *n*:1 associations.

In IE, this transformation loses the constraint that each *A*\-*B* combination relates to at most one *C* (unless we drop to the relational level by using two foreign keys for *C*’s primary key; see IDEF1X later). In ORM, the constraint is captured conceptually as external uniqueness, making *C* a *coreferenced* object type–the transformation is a flatten/coreference equivalence (see [Chapter 14](#Ch014_681-771_B9780443237904000189.xhtml)).

As an example, the *m:n* association Person plays Sport can be transformed into the uniquely constrained, mandatory *n*:1 associations Play is by Person; Play is of Sport. However, such a transformation is often very unnatural, especially if nothing else is recorded about the coreferenced object type. So, any truly conceptual approach must allow *m:n* associations to be modeled directly.

Some versions of IE support an *exclusive-or constraint*, shown as a black dot connected to the alternatives. [Fig. 8.24](#Ch008_309-346_B9780443237904000177.xhtml#f0125)(a) depicts the situation where each employee is allocated a bus pass or parking bay, but not both. The equivalent ORM schema is shown in [Fig. 8.24](#Ch008_309-346_B9780443237904000177.xhtml#f0125)(b). Unlike ORM, IE does not support an inclusive-or constraint. Nor does it support simple or compound exclusion constraints.

![Fig. 8.24 An exclusive-or constraint in (a) IE and (b) ORM.](images/B9780443237904000177/f08-24-9780443237904.jpg)

[Fig. 8.24](#Ch008_309-346_B9780443237904000177.xhtml#B-f0125) An exclusive-or constraint in (a) IE and (b) ORM.

Subtyping schemes for IE vary. Sometimes Euler diagrams are used, adding a blank compartment if needed for “Other”. Sometimes DAGs are used, possibly including subtype relationship names and optionality/cardinality constraints.

[Fig. 8.25](#Ch008_309-346_B9780443237904000177.xhtml#f0130) shows three different subtyping notations for partitioning Patient into MalePatient and FemalePatient. There is no formal support for subtype definitions or context-dependent reference. Multiple inheritance may or may not be supported, depending on the version.

![Fig. 8.25 Some different IE notations for subtyping.](images/B9780443237904000177/f08-25-9780443237904.jpg)

[Fig. 8.25](#Ch008_309-346_B9780443237904000177.xhtml#B-f0130) Some different IE notations for subtyping.

Although far less expressive than ORM, IE does a good job of covering basic constraints. Its founder Clive Finkelstein is an amiable Aussie who is still actively engaged in the IE discipline. He developed a set of modeling procedures to go with the notation, extended IE to enterprise engineering, and incorporated work with the extensible markup language (XML).

## 8.4 IDEF1X
