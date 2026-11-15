The complement of a class contains each individual that is not a member of that class. In Manchester syntax, the complement operator appears as “not”. For example, the class NonHuman may be defined as the complement of the class Human as follows:

```
Class: Human
Class: NonHuman EquivalentTo: not Human
```

The definition below of the class NonDriver is another example:

```
Class: Person
Class: Driver EquivalentTo: Person and drives min 1 Car
Class: NonDriver EquivalentTo: Person and not Driver
```

All the examples so far have used classes. In OWL 2, the union, intersection, and complement operations may also be applied to data ranges. For example:

```
Datatype: StringOrInteger EquivalentTo: xsd:string or xsd:integer
Datatype: PassGradeNr EquivalentTo: GradeNr and not FailGradeNr
```

# Reflexive, Irreflexive, Symmetric, Asymmetric, and Transitive Predicates

In OWL, all properties are binary predicates. If the domain and range are the same or compatible, one may compare subject and object instances. In ORM, such predicates are called ring predicates, and constraints that apply specifically to them (or more generally, pairs of compatible roles) are called ring constraints.

ORM includes graphical notation for several kinds of ring constraints, some of which are simply defined (e.g., irreflexive, asymmetric) while others are recursively defined (e.g., acyclic, strongly intransitive). OWL 2 supports only the following five kinds of restrictions on ring predicates: reflexive, irreflexive, symmetric, asymmetric, and transitive. Of these, OWL 1 supported only symmetric and transitive. Unlike ORM, OWL allows restrictions on ring predicates to be applied only to object property expressions, not data property expressions.

A relation R is reflexive if and only if every individual thing in the domain of R bears the relation R to itself. If the domain is owl:Thing, the only predicate likely to be reflexive is the identity relation “=”.

OWL allows object property expressions to be declared reflexive by characterizing them as reflexive properties. In Manchester syntax, we declare “Reflexive” as a characteristic. For example, if each person knows himself/herself, the “knows” predicate may be declared to be reflexive as follows:

```
ObjectProperty: knows
Domain: Person
Range: Person
Characteristics: Reflexive
```