
A `maxCardinality` of 1 may be declared in a similar way using `max 1`, which is another way to declare that the predicate is functional. If `minCardinality = maxCardinality`, you can set both at once using `exactCardinality`. For example, the 1:1 reference scheme for `Politician` may be declared in OWL 2 as follows:

```
Class: Politician
SubClassOf: hasPoliticianName exactly 1
HasKey: hasPoliticanName
DataProperty: hasPoliticianName
Domain: Politician
Range: PoliticianName
```

As a composite identification scheme example, consider the ORM schema in [Fig. 18.25](#Ch018_935-1005_B9780443237904000104.xhtml#f0130)(a). Here, each building is identified by its building number, and each room is identified by combining its local room number with its building.

![Fig. 18.25 An ORM schema where Room has a composite reference scheme.](images/B9780443237904000104/f18-25-9780443237904.jpg)

[Fig. 18.25](#Ch018_935-1005_B9780443237904000104.xhtml#B-f0130) An ORM schema where Room has a composite reference scheme.

Now, consider the ORM schema in [Fig. 18.26](#Ch018_935-1005_B9780443237904000104.xhtml#f0135)(a). In the fact type `Employee drives Car`, the `drives` predicate is optional and *m:n*. The two textual constraints in FORML add a *restricted mandatory role constraint* (see constraint footnote 1) and a *restricted uniqueness constraint* (see constraint footnote 2). Here, the `drives` predicate is functional only with respect to `NonExecutive`, not `Employee`. We should *not* declare `drives` as a `FunctionalProperty` because that would then apply to all employees (and any other subjects of the `drives` predicate in an OWL version of the model). These restricted constraints may be declared in OWL using qualified cardinality restrictions, as shown in [Fig. 18.26](#Ch018_935-1005_B9780443237904000104.xhtml#f0135)(a) using Manchester syntax.

![Fig. 18.26 Restricted mandatory role constraint and restricted uniqueness constraint.](images/B9780443237904000104/f18-26-9780443237904.jpg)

[Fig. 18.26](#Ch018_935-1005_B9780443237904000104.xhtml#B-f0135) Restricted mandatory role constraint and restricted uniqueness constraint.

In practice, it is very rare to encounter explicit declarations for `minCardinality = 0` and `minQualifiedCardinality = 0` because these apply by default, so they may be ignored. However, setting the maximum cardinality to zero does have some use. The setting `maxCardinality = 0` means that each instance of the subject class expression `A` is related via the predicate `R` to no object instance.

The setting `maxQualifiedCardinality = 0` means that each instance of the subject class expression `A` is related via `R` to no instance of the specified range `B`. These restrictions are used mainly in defining subclasses, and the qualified version is typically used in such cases. [Fig. 18.27](#Ch018_935-1005_B9780443237904000104.xhtml#f0140)(a) and [Fig. 18.27](#Ch018_935-1005_B9780443237904000104.xhtml#f0140)(b) summarize the corresponding ORM patterns. [Fig. 18.27](#Ch018_935-1005_B9780443237904000104.xhtml#f0140)(c) provides a concrete example, and [Fig. 18.27](#Ch018_935-1005_B9780443237904000104.xhtml#f0140)(d) shows the OWL code.

![Fig. 18.27 Use of maxCardinality = 0 and maxQualifiedCardinality = 0 for subtyping.](images/B9780443237904000104/f18-27-9780443237904.jpg)

[Fig. 18.27](#Ch018_935-1005_B9780443237904000104.xhtml#B-f0140) Use of maxCardinality = 0 and maxQualifiedCardinality = 0 for subtyping.

`ExactCardinality` restrictions other than 1 are allowed. For example, the following OWL 2 code may be used to state that `Asimov` authored exactly 506 books.

```
ObjectProperty: authored
Domain: Person
Range: Book
Individual: Asimov
Types: Person
authored exactly 506 Book
```

Database systems typically identify countries by country codes or country names. Many country names contain embedded spaces (e.g., “Czech Republic”) so can’t be used directly as IRIs (though modified names using underscores or hyphens for spaces could be).

In practice, many OWL ontologies use meaningless, automatically generated identifiers as IRIs just as some relational database designers prefer artificial, surrogate keys for their table schemes. Human-readable labels can be associated with IRIs using `rdfs:label` annotation properties, and OWL software tools such as Protégé ([http://protege.stanford.edu/](http://protege.stanford.edu/)) can be configured to display labels instead of IRIs to make the ontologies more readable.

Constraints specified in data models are *not* translated into actual *constraints* in OWL, but rather logical *propositions* that are understood in terms of open world semantics where some individuals may be unnamed. For example, the subclass restriction “hasPoliticianName min 1” for `Politician` simply says that each politician has a politician name—it doesn’t require the system to know what that code is.

### Union, Intersection, and Complement

Recall that the *union* of sets `A` and `B` is the set of all elements in `A` or `B` or both. The union operator is supported in all versions of OWL, except for OWL Lite, and may be applied to classes or data ranges (e.g., datatypes or other collections of literals). The complex class expression or data range expression resulting from a union may be used anywhere a simple class or data range may be used. The union of two or more classes contains all the individuals that occur in at least one of those classes. In Manchester syntax, the union operator appears as “or”, placed in infix position. This is an *inclusive-or* operator. For example, we may define a promising student as a student who is either bright or industrious (or both) as follows:

```
Class: PromisingStudent
EquivalentTo: BrightStudent or IndustriousStudent
```

This implies that `BrightStudent` and `IndustriousStudent` are subclasses of `PromisingStudent`. Inferences may be drawn about membership in the superclass. For example, given `Individual: Hermione Types: BrightStudent, IndustriousStudent`, we may infer `Individual: Hermione Types: PromisingStudent`.

A class *partition* may be declared in OWL by adding a *disjoint classes* declaration to the union operation. In Manchester syntax, to declare two or more classes that are disjoint (i.e., mutually exclusive), simply prepend “DisjointClasses:”. Adding this to an inclusive-or operator results in an *exclusive-or* operator. For example, we may define a `Party` as either a person or an organization but not both, thus:

```
DisjointClasses: Person, PrivateCompany, PublicOrganization
Class: Party
EquivalentTo: Person or Organization
```

A partition of more than two classes may be specified in a similar way, for example,

```
DisjointClasses: Person, PrivateCompany, Organization
Class: Party
EquivalentTo: Person or PrivateCompany or PublicOrganization
```

As an alternative for declaring partitions, OWL supports the *disjoint union* operator. In Manchester syntax, this is rendered by using “DisjointUnionOf:”. For instance, the partition just discussed may be declared more concisely thus:

```
Class: Party
DisjointUnionOf: Person, PrivateCompany, PublicOrganization
```

Recall that the *intersection* of sets `A` and `B` is the set of all elements that occurs in both `A` and `B`. In OWL, the intersection operator may be applied to classes or data ranges, and the complex class expression or data range expression resulting from an intersection may be used anywhere a simple class or data range may be used. In Manchester syntax, the intersection operator appears as “and”, placed in infix position. For example, the final line of the following OWL code defines the class `StudentEmployee` as the *intersection* of `Student` and `Employee`, which are themselves subclasses of `Person`.

```
Class: Person
Class: Student
SubClassOf: Person
Class: Employee
SubClassOf: Person
Class StudentEmployee
EquivalentTo: Student and Employee
```
