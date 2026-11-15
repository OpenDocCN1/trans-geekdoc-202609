

Characteristics: Functional
Individual: Poirot
Facts: isaSmoker true
Individual: Hastings
Facts: isaSmoker false
Individual: Japp
Types: Person

## Join Semantics of External Uniqueness Constraints

External uniqueness constraints with *inner join* semantics may be declared in OWL simply by using compound HasKey properties on the referenced class. Recall Fig. 18.25, where each room was identified by combining its local room number with its building, and this OWL code was used for the composite reference scheme.

```
Class: Room
SubClassOf: isInBuilding exactly 1
SubClassOf: hasRoomNr exactly 1
HasKey: isInBuilding, hasRoomNr
```

Capturing *external uniqueness constraints with outer join semantics* in OWL requires more work. Typically, this will involve *introducing a subclass for the instances that don't play the relevant optional role and then declaring a HasKey property for that subclass*. To ensure that the HasKey declarations are effective, IRIs must be included for the referenced instances.

Fig. 18.28 reproduces an example from Section 10.1. The external uniqueness constraint has outer join semantics, with the added proviso that nulls produced in the outer join are treated as actual values. Hence, in addition to being identified by its course code, each course that is offered by a department may be referenced by the combination of its course title and its department, for example, (Mechanics, PY) and (Mechanics, MA). Each course offered by no department may be identified either by its code or its title.

| PY101 | Mechanics |
| MA202 | Mechanics |
| NDC3 | Mechanics |
| NDC4 | Mechanics |

| PY101 | PY |
| MA202 | MA |

ft1 left outer join ft2

Course ( courseCode, courseTitle, [departmentCode] )

| PY101 | Mechanics | PY |
| MA202 | Mechanics | MA |
| NDC3 | Mechanics | <null> |
| NDC4 | Mechanics | <null> |

FIG. 18.28 (a) An external UC with outer join semantics; (b) the relational schema.

Adding course NDC4 with the same title "Mechanics" as course NDC3 would violate the external uniqueness constraint. Assuming the object properties and data properties are declared in the usual way, the outer join semantics of the external uniqueness constraint may be captured in Manchester syntax as shown below. The subclass NonDepartmentalCourse is added for courses offered by no department, and hasCourseTitle is declared as a HasKey property for it.

```
Class: Course
SubClassOf: hasCourseTitle exactly 1 xsd:string
SubClassOf: hasCourseCode exactly 1 xsd:string
HasKey: hasCourseCode
```

```
Class: Department
SubClassOf: hasDepartmentCode exactly 1 xsd:string
HasKey: hasDepartmentCode
```

```
Class: NonDepartmentalCourse
EquivalentTo: Course and (isOfferedBy max 0 Department)
HasKey: hasCourseTitle
```

If we add the test data shown in Fig. 18.28, this will violate the HasKey condition that nondepartmental courses can be identified by their titles because two nondepartmental courses, NDC3 and NDC4, would have the same title "Mechanics".

## Mapping ORM to OWL

Recent research efforts have investigated mapping from conceptual models in ORM, UML, and ER to OWL as well as other description logic-based languages. The direct formal semantics of OWL 2 is based on the description logic SROIQ (D). Much of ORM can be mapped cleanly to these description logics, facilitating the use of efficient DL-based theorem provers for consistency checking of ORM schemas, and interoperability with other semantic web applications. Unlike OWL 2, ORM has a clean, first-order formalization, so problems about types being instances are avoided. However, some ORM structures and constraints cannot be captured in OWL. This has both good and bad consequences.

On the plus side, ORM is capable of capturing, in a natural fashion, several complex aspects of reality that commonly occur in business domains but cannot be captured in popular description logics. Hence, ORM enables higher-fidelity models of typical business domains.

On the negative side, ORM is so expressive that its underlying logic extends a little beyond decidable fragments of first-order logic. This makes it difficult to achieve efficient automated checking of aspects such as schema satisfiability (e.g., in very large schemas with millions of constraints, checking that none of the constraints contradict one another).

This is yet another example of the trade-off between expressibility and tractability. The more expressive the language, the harder it is to efficiently verify the logical consistency of models expressed in it. Because we ought to ensure that our models accurately reflect the business domains they are intended to model, it seems reasonable to capture the intended semantics in a language such as ORM, apply efficient automated checking where possible, and use heuristic techniques for the rest.

Examples of ORM features that can't be translated into SROIQ (D), and hence OWL DL, include uniqueness and frequency constraints spanning multiple roles (of the same or different relationships), set-comparison constraints involving multirole arguments, acyclic ring constraints, and deontic constraints. The DLRI_{ifd} description logic adds support for identifier and functional dependency constraints, so it can capture internal uniqueness constraints spanning multiple roles as well as external uniqueness constraints.

Unlike ER and UML, ORM is attribute-free and hence is easier to relate to RDF, RDFS, OWL, and description logics, which also represent all facts in the form of relationships. Although RDF and OWL use binary relationships only, it is a trivial matter to transform unary and n-ary fact types into binary form, as discussed in earlier chapters. So, there is a fairly obvious mapping of facts and fact types in binary ORM to these semantic web languages.

The only aspects lost in the mapping are those ORM constraints and derivation rules that have no counterpart in the logic underlying the target language. These can be mapped over as unambiguous verbalizations in ancillary notes.

An atomic fact type in ORM offers an ideal semantic unit for sharing semantics between different models. Such a unit is constraint-free, allowing different models to apply different constraints without altering the semantics of the fact type. For example, the fact type Person drives Car might be optional and m:n in one model, but mandatory and n:1 in another model. Using a fact-based approach instead of an attribute-based approach facilitates this kind of exchange. This is one reason why the OMG's SBVR approach for exchanging semantics of business rules is also fact-oriented.

## 18.7 Metamodeling

Modeling involves making models of business domains. *Metamodeling* involves making models of models—this time the things being modeled are themselves models. Just as recursion is one of the most elegant and powerful concepts in logic, metamodeling is one of the most beautiful and powerful notions in conceptual modeling. This section uses a simple example to convey the basic idea.

A database holds fact instances from a business domain while its conceptual schema models the *structure* of the domain. Fig. 18.29 recalls our basic view of an information system where the database conforms to the rules laid down in the conceptual schema. Essentially, a DBMS is a system for managing various databases; for each database that models some UoD, it checks that each database state agrees with the structure specified in the conceptual schema for that UoD.

![](img/1344db3eba3d550e6edb009556fcd95c_1019_0.png)

FIG. 18.29 The database must conform to the structure of the conceptual schema.

Among other things, a conceptual modeling tool is a system for managing conceptual schemas. Each valid schema diagram in this book may be thought of as an output report from this system. The trick then is to treat a schema as an instance of this higher-level system. As long as we can verbalize the diagrams into atomic facts, we can use the CSDP to develop a conceptual schema for such conceptual schemas. We would then have a conceptual *metaschema* (schema about schemas).

Suppose that Table 18.4 is part of an output report from a movie database. Other reports from the database provide further information (e.g., people's birth places).

### Table 18.4 One report extracted from a movie database.

| MovieNr | Title | Director | Stars |
|---|---|---|---|
| 1 | Wilderness | Tony O'Connor | |
| 2 | Sleepy in Seattle | Anne Withanee | Ima Dozer<br>Anne Withanee |
| 3 | Wilderness | Anne Withanee | Paul Bunyip |

![](img/1344db3eba3d550e6edb009556fcd95c_1019_1.png)

FIG. 18.30 A conceptual schema for Table 18.4.

The conceptual subschema for this report is shown in Fig. 18.30. The inclusive-or constraint on Person is shown explicitly because Person plays other roles in the global schema (e.g., as in Fig. 18.8 from an earlier section).

