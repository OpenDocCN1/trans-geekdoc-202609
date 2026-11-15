
**Objectification:** Treating a relationship as an object; also called nesting. Strictly speaking, objectification in ORM 2 distinguishes the object formed by the objectification from the original relationship, and hence involves situational rather than propositional nominalization.

**Object-Role Modeling (ORM):** Conceptual modeling method that pictures a business domain in terms of objects playing roles; it provides graphical and textual languages for verbalizing and querying information as well as various design and transformation procedures.

**Population:** Set of instances present in a particular state of the database.

**Predicate:** Proposition with object-holes in it, e.g., “... works for ...”.

**Primitive object type:** Object type that is not a subtype of another object type.

**Reference:** Relationship used as the preferred way to reference or identify an object (or to provide part of the identification).

**Reference mode:** Mode or manner in which a single value references an entity; used to abbreviate simple reference schemes, such as (Code), (kg).

**Referential role:** Role in a reference (existential fact). Also known as an existential role.

**Relationship:** Property or association involving one or more objects.

**Rigid subtype:** Subtype whose instances must remain in that type for their whole lifetime (e.g., Person).

**Rmap:** Relational mapping procedure.

**Role:** Part played by an object in a relationship (unary, binary, ternary, etc.).

**Role subtype:** Subtype whose instances may leave that type during their lifetime (e.g., Child).

**Semiderived fact type:** Fact type, some of whose instances may be derived from others while some other instances may be simply asserted.

**Semiderived subtype:** Subtype, some of whose instances may be derived using a derivation rule while some other instances may be simply asserted.

**Subtype:** Object type that is properly contained in another object type (e.g., Woman is a subtype of Person).

**Type:** Set of possible instances.

**Uniqueness constraint (UC):** Repetition is not allowed in the role or role sequence spanned by the constraint; a uniqueness constraint on a single predicate is an internal UC, and a uniqueness constraint over roles from different predicates is an external UC.

**Universe of Discourse (UoD):** Business domain (the aspects of the world that we want to talk about).

**Value:** Unchangeable object that is identified by a constant. In this book, a value is either a character string or a number; sometimes called a label.

The following symbol glossary covers the main graphical symbols in ORM 2. It is based on the standard ORM 2 symbol glossary copyrighted to Terry Halpin, and is used by permission.

| Construct and Examples | Description/Notes |
| :--- | :--- |
| **Entity type**<br>Country or Country or Country | Named soft rectangle, named hard rectangle, or named ellipse. The soft rectangle shape is the default. |
| **Value Type**<br>CountryCode or CountryCode or CountryCode | Named, dashed, soft rectangle (or hard rectangle or ellipse). |
| **Entity type with popular reference mode**<br>Country(.Code) Course(.Code) Company(.Name) Building(.Nr) | Abbreviation for injective reference to value type, such as<br>Country —(has / is of)— CountryCode |
| **Entity type with unit-based reference mode**<br>Height (cm:) Mass (kg:) Salary (USD:) Price (EUR:)<br>Height (cm: Length) Salary (USD: Money) Price (EUR: Money) | Abbreviation for reference type, such as<br>Height —(has / is of)— cmValue<br>Optionally the unit type may be displayed (as shown opposite). |
| **Entity type with general reference mode**<br>Book (ISBN) Website (URL) | Abbreviation for reference type, such as<br>Book —(has / is of)— ISBN<br>Website —(has / is of)— URL |
| **Independent Object Type**<br>Country ! CountryCode ! | Instances of the type may exist, without playing any elementary fact roles. |
| **External Object Type**<br>Address^ | This notation is tentative, and is not supported by NORMA. |
| **Predicate (unary, binary, ternary, etc.)**<br>smokes [ ] was born in [ ][ ] ... speaks ... well [ ][ ]<br>... played ... for ... [ ][ ] ... in ... on ... ate ... [ ][ ][ ] | Ordered set of 1 or more role boxes with at least one predicate reading. If shown, object placeholders are denoted by “…”. If placeholders are not shown, unaries use prefix notation. Binaries use infix notation. Ternaries, etc., use mixfix notation. |
| **Duplicate type or predicate shape**<br>Person [shadowed] StateCode [dashed shadowed] was born in [ ][ ] | If an object type or predicate shape is displayed more than once (on the same page or different pages), it is shadowed. |
| **Unary fact type**<br>Person ▭ smokes<br>Person ▭ smokes [isSmoker] | Attaching a role box to an object type shape means that only instances of that object type may play that role. A role name may be added in square brackets. |
| **Binary Fact Type**<br>Person was born in Country<br>Person [employee] employs Company [employer]<br>Person made Product<br>Person reports to / manages Person<br>Car drives Person | By default, predicate readings (binary or longer) are read left to right or top to bottom. An arrow tip is used to display a different reading direction. Role names may be displayed in square brackets beside their role. Forward and inverse readings for binaries may be shown together, separated by “/”. |
| **Ternary fact type**<br>Person [player] ... played ... for ... Country ... introduced ... to ... Sport<br>Person<br>Food Cat<br>Date ... on ... ate ... Cat ... Food ... Date<br>[Cat] ate [Food] on [Date] | Role names may be added in square brackets. Arrow tips are used to reverse the default left-right or top-down reading order. Reading orders other than forward and reverse are shown using named placeholders. |
| **Quaternary fact type**<br>City Date<br>Person ... in ... on ... ate ... Food | The above notes for the ternary case apply here also. Fact types of higher arity (number of roles) are also permitted. |
| **Objectification (a.k.a. nesting)**<br>"Enrolment !"<br>Student enrolled in Course<br>resulted in Grade<br>[ Enrolment ! ] | The enrolment* fact type is objectified as an entity type whose instances can play roles. In this example, the objectification type is independent, so we can know about an enrolment before the grade is obtained. Objectification object types may also be displayed without their defining components, using an object type shape containing a small predicate shape, as shown. *Australian spelling used here. |
| **Internal uniqueness constraint (UC) on a unary fact type**<br>Diagram: Person - smokes | These examples are equivalent. By default, fact types are assumed to be populated with sets of facts (not bags of facts), so no whole fact may be duplicated. |
| **Internal UCs on a binary fact type**<br>Diagrams: Gender/Person/Country and Language/Person/Country | The examples show the four possible patterns:<br>1:n (one-to-many);<br>n:1 (many-to-one);<br>m:n (many-to-many);<br>1:1 (one-to-one). |
| **Internal UCs on a ternary fact type**<br>Diagrams: Team/Competition/Place and Person/Country/Sport | The first example has two two-role UCs: the top UC forbids ties. The other UC ensures that each team got at most one place per competition (a dotted line excludes its role from the UC). The second example has a spanning UC (many-to-many). For an n-ary (n > 2) fact type to be atomic, each UC on it must span at least n-1 roles. |
| **Simple mandatory role constraint**<br>Diagrams: Person and Country | The example constraint means that each person was born in some country. The mandatory role dot may be placed at either end of the role connector. |
| **Inclusive-or constraint**<br>Diagram: Visitor, Passport, WorkVisa, Person | An inclusive-or constraint is also called a disjunctive mandatory role constraint. The constraint is displayed as a circled dot connected to the constrained roles (or the junction of adjacent roles hosted by the same object type). The first constraint means that each visitor referenced in the model must have a passport or work visa (or both). The second example means that each person is a parent of a person or a child of a person (or both). |
