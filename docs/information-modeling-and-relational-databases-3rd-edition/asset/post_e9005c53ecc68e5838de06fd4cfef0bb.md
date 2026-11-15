
Some authors allow changeability to be specified for a class, as an abbreviation for declaring this for all its attributes and opposite association ends (Booch et al., 1999, p. 184). For instance, all the {readOnly} constraints in Fig. 9.50 might be replaced by a single {readOnly} constraint below the name “Transaction”. While this notation is neater, it would be rarely used. Even in this example, we would probably want to allow for the possibility of adding nonfrozen information later (e.g., a transaction might be audited by zero or more auditors).

![](img/1344db3eba3d550e6edb009556fcd95c_412_0.png)

FIG. 9.50 All attributes of Transaction are readOnly.

Changeability settings are useful in the design of program code. Although changeability settings are not yet supported in ORM, which focuses on static constraints, they are being considered in extensions to support dynamic constraints (see next chapter). In the wider picture, being able to completely model security issues (e.g., who has the authority to change what) would provide extra value.

UML allows {ordered} and {unique} properties to be specified for multivalued attributes and association ends. Because {unique} is true by default, the use of {ordered} indicates an ordered set (a sequence with no duplicates). For example, Fig. 9.51(a) shows one way of modeling authorship of papers in UML. Each paper has a list of authors, each of whom may appear at most once on the list.

This may be modeled in flat ORM by using a Position object type to store the sequential position of authors on the list, as shown in Fig. 9.51(b). The uniqueness constraint on the first two roles declares that for each paper an author occupies at most one position; the constraint covering the first and third roles indicates that for any paper, each position is occupied by at most one author. The textual constraint notes that the list positions are numbered sequentially from 1.

![](img/1344db3eba3d550e6edb009556fcd95c_412_1.png)

FIG. 9.51 An ordered set modeled in (a) UML and (b) ORM.

Although this ternary representation may appear awkward, it is easy to populate and it facilitates any discussion involving position (e.g., who is the second author for paper 21?). From an implementation perspective, an ordered set structure could still be chosen.

An ordered set is an example of a collection type. As discussed in Chapter 10, some versions of ORM allow collections to be specified as mapping annotations in a similar way to UML, and some ORM versions allow collections to be modeled directly as first-class objects.

UML 2 introduced the notion of *association redefinition*. This concept applies to generalizations as well as associations. One main use of it is to specify stronger constraints on an association that specializes an association involving a supertype. For example, in Fig. 9.52(a) the `executiveCar` role redefines the `assignedCar` role, applying a stronger multiplicity constraint that applies only to executives. Effectively, the association Executive is assigned CompanyCar is treated as a specialization of the Employee is assigned CompanyCar association. The stronger multiplicity constraint may be expressed in ORM by a textual constraint as in Fig. 9.52(b), or by a subset constraint involving the subtyping link (see Section 10.8).

Now let's consider *derived data*. In UML, derived elements (e.g., attributes, associations, or association-roles) are indicated by prefixing their names with "/". Optionally, a *derivation rule* may be specified as well. The derivation rule can be expressed as a constraint or note, connected to the derived element by a dashed line. This line is actually shorthand for a dependency arrow, optionally annotated with the stereotype name «derive».

![](img/1344db3eba3d550e6edb009556fcd95c_413_0.png)

Because a constraint or note is involved, the arrow tip may be omitted (the constraint or note is assumed to be the source). For example, Fig. 9.53(a) includes area as a derived attribute. Fig. 9.53(b) shows the ORM schema.

The UML dependency line may also be omitted entirely, with the constraint shown in braces next to the derived element (in this case, it is the modeling tool's responsibility to maintain the graphical linkage implicitly). The example in Fig. 9.54(a) expresses unclehood as a derived association. For illustration purposes, rolenames are included for association ends. The corresponding ORM schema is shown in Fig. 9.54(b), with the derivation rule specified in relational style.

![](img/1344db3eba3d550e6edb009556fcd95c_414_0.png)

![](img/1344db3eba3d550e6edb009556fcd95c_414_1.png)

Although precise role names are not always elegant, the use of role names in derivation rules involving a path projection can facilitate the concise expression of rules, as shown here in the UML model. By adding role names to the ORM schema, the derivation rule may be specified compactly in attribute style thus: * define uncle of Person as brother of parent of Person. More complex derivation rules can be stated informally in English or formally in a language such as OCL.

One advantage of ORM's approach to derivation rules is that it is more stable because it is not impacted by schema changes such as attributes being later remodeled as associations.

## 9.8 Mapping from ORM to UML

The UML map procedure in Table 9.3 provides basic guidelines for mapping ORM schemas to UML class diagrams. Selected entity types and value types map to object classes and data types, including attribute domains when associations are replaced by attributes. We now illustrate this procedure.

Table 9.3 UML map procedure.

| Step | Action |
| :--- | :--- |
| 1 | Binarize any sets of exclusive unaries |
| 2 | Model selected object types as classes, and map a selection of their n:1 and 1:1 associations as attributes. To store facts about a value type, make it a class |
| 3 | Map remaining unary fact types to Boolean attributes or subclasses |
| 4 | Map other fact types to associations, association classes, or coreferenced classes. Map objectified associations to association classes or coreferenced classes |
| 5 | Map ORM constraints to UML graphic constraints, textual constraints, or notes |
| 6 | Map subtypes to subclasses, and if needed, subtype definitions to textual constraints |
| 7 | Map derived fact types to derived attributes/associations, and map semiderived fact types to attributes/associations plus derivation rules |

Step 1 binarizes any sets of exclusive unaries, as shown in Fig. 9.55.

![](img/1344db3eba3d550e6edb009556fcd95c_415_0.png)

FIG. 9.55 Step 1: Replace any set of exclusive binaries by a binary fact type.

In step 2, we decide which object types to model as classes and which n:1 and 1:1 ORM associations to remodel as attributes. Typically, entity types that play functional fact roles become classes. Functional binary (n:1 and 1:1) associations from an entity type A to a value type B, or to an entity type B about which you never want to record details, usually map to an attribute of A. If you have specified role names, these can usually be used as attribute names, with the object type name becoming the attribute's domain name.

The mapping in Fig. 9.56 illustrates several of these step 2 considerations as well as step 6 (map ORM constraints to UML graphic constraints, textual constraints, or notes). The {U1} annotation for uniqueness is not standard UML. The value constraint on gender codes is captured using an enumeration type.

In rare cases, value types that are independent play an explicit mandatory role, or play a functional fact role in a 1:n fact type map to classes. The example in Fig. 9.57(a) deals with cases where we store title–gender restrictions (e.g., the title “Mr” is restricted to the male gender).

The example in Fig. 9.57(b) uses a multivalued attribute to store all the genders applicable to a title (e.g., the title “Dr.” applies to both male and female genders). The Title class gives fast access from title to applicable gender, but slow access from gender to title. As discussed earlier, multivalued attributes should be used sparingly.
