A domain of a binary predicate is a class to which its subject must belong, and a range of a binary predicate is a class to which its object must belong. In Manchester syntax, a predicate may be declared as an ObjectProperty, and its domain(s) and ranges(s) specified after “Domain:” and “Range:” respectively. For example:

```
ObjectProperty: isFatherOf
Domain: MalePerson
Range: Person
```

A predicate may be assigned multiple domains and ranges, in which case the subject must belong to the intersection of the predicate’s domains and the object must belong to the intersection of the predicate’s ranges.

# Some OWL 2 Taxonomy

Fig. 18.22 shows a UML class diagram for several concepts in OWL 2. This diagram is based on https://www.w3.org/TR/owl2-syntax/. What we called “resources” in our discussion of RDF are called “entities” in OWL. OWL entities may be named individuals, classes, properties (binary predicates), or data types. This differs from the use of the term “entity” in ORM and ER, where all entities are nonlexical individuals (not types or classes).

![](bbox=[0.107, 0.482, 0.861, 0.68])

FIG. 18.22 Class diagram of basic OWL 2 concepts (based on the OWL 2 specification).

In OWL, entities are identified by IRIs, but unlike some approaches, OWL does not adopt the Unique Name Assumption (UNA). So, in OWL the same entity may be assigned different IRIs, even within the same document. Hence, the multiplicity constraint of 1 on entityIRI in Fig. 18.22 should instead be 1..* (1 or more). As discussed earlier, OWL includes the SameAs predicate to indicate when two different IRIs denote the same entity (e.g., DownUnder SameAs Australia).

Literals (data values such as names or numerals) are not treated as individuals. This practice differs from formal logic, where literals do count as individuals. Only OWL individuals (not literals) may be members of OWL classes.