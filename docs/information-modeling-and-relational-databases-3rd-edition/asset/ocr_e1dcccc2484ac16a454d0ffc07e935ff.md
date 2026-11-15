![](bbox=[0.3, 0.095, 0.68, 0.38])

FIG. 6.35 The indirect subtype connection is implied, so should be omitted.

If a subtype has two or more direct supertypes, this is called *multiple inheritance*. For example, in Fig. 6.35, FemaleAustralian inherits from both Australian and FemalePerson. In general, a subtype is at most the intersection of its supertypes. If a subtype has only one direct supertype, this is called *single inheritance*.

A supertype may have many direct subtypes, and a subtype may have many direct supertypes, so in general we have a *subtype graph* rather than a tree. The supertype and subtypes are referred to as the *nodes* of the graph. Because the arrowheads provide direction, we have a directed graph.

Because no type can be a proper subtype of itself, no cycles or loops are permitted, no matter what the length of the cycle (Fig. 6.36 shows two illegal cycles). Thus, any pattern of type-subtype relationships forms a *directed acyclic graph*.

An entity type that is not a proper subtype of any other entity type in the schema is said to be a *primitive entity type* for the schema. In Fig. 6.30, for example, Person, Gender, and Country are primitive entity types. A single conceptual schema may have many subtype graphs (e.g., one based on Person and one based on Vehicle). Each subtype graph must stem from exactly one primitive entity type (which may be an objectified association) that is the common supertype, or *root node* (or *top*) of that graph.

![](bbox=[0.265, 0.795, 0.705, 0.885])

FIG. 6.36 No cycles are permitted in a subtype graph.