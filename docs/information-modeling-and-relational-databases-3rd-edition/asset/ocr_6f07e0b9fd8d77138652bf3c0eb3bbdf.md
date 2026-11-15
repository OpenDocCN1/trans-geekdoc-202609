ExactCardinality restrictions other than 1 are allowed. For example, the following OWL 2 code may be used to state that Asimov authored exactly 506 books.

```
ObjectProperty: authored
Domain: Person
Range: Book
Individual: Asimov
Types: Person
authored exactly 506 Book
```

Database systems typically identify countries by country codes or country names. Many country names contain embedded spaces (e.g., “Czech Republic”) so can’t be used directly as IRIs (though modified names using underscores or hyphens for spaces could be).

In practice, many OWL ontologies use meaningless, automatically generated identifiers as IRIs just as some relational database designers prefer artificial, surrogate keys for their table schemas. Human-readable labels can be associated with IRIs using rdfs: label annotation properties, and OWL software tools such as Protégé (http://protege. stanford.edu/) can be configured to display labels instead of IRIs to make the ontologies more readable.

Constraints specified in data models are not translated into actual constraints in OWL, but rather logical propositions that are understood in terms of open world semantics where some individuals may be unnamed. For example, the subclass restriction “hasPoliticianName min 1” for Politician simply says that each politician has a politician name—it doesn’t require the system to know what that code is.

# ## Union, Intersection, and Complement

Recall that the union of sets A and B is the set of all elements in A or B or both. The union operator is supported in all versions of OWL, except for OWL Lite, and may be applied to classes or data ranges (e.g., datatypes or other collections of literals). The complex class expression or data range expression resulting from a union may be used anywhere a simple class or data range may be used. The union of two or more classes contains all the individuals that occur in at least one of those classes. In Manchester syntax, the union operator appears as “or”, placed in infix position. This is an inclusive-or operator. For example, we may define a promising student as a student who is either bright or industrious (or both) as follows:

```
Class: PromisingStudent EquivalentTo: BrightStudent or IndustriousStudent
```

This implies that BrightStudent and IndustriousStudent are subclasses of PromisingStudent. Inferences may be drawn about membership in the superclass. For example, given Individual: Hermione Types: BrightStudent, IndustriousStudent, we may infer Individual: Hermione Types: PromisingStudent.