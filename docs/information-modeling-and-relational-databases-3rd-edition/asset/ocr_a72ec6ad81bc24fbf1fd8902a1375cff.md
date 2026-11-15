# Table 9.3 UML map procedure.

| Step | Action |
| :--- | :--- |
| 1 | Binarize any sets of exclusive unaries |
| 2 | Model selected object types as classes, and map a selection of their n:1 and 1:1 associations as attributes. To store facts about a value type, make it a class |
| 3 | Map remaining unary fact types to Boolean attributes or sub classes |
| 4 | Map other fact types to associations, association classes, or coreferenced classes. Map objectified associations to association classes or coreferenced classes |
| 5 | Map ORM constraints to UML graphic constraints, textual constraints, or notes |
| 6 | Map subtypes to subclasses,
and if needed, subtype definitions to textual constraints |
| 7 | Map derived fact types to derived attributes/associations, and map semiderived
fact types to attributes/associations plus derivation rules |

Step 1 binarizes any sets of exclusive unaries, as shown in Fig. 9.55.

![](bbox=[0.194, 0.485, 0.847, 0.553])

# FIG. 9.55 Step 1: Replace any set of exclusive binaries by a binary fact type.

In step 2, we decide which object types to model as classes and which n:1 and 1:1 ORM associations to remodel as attributes. Typically, entity types that play functional fact roles become classes. Functional binary (n:1 and 1:1) associations from an entity type A to a value type B, or to an entity type B about which you never want to record details, usually map to an attribute of A. If you have specified role names, these can usually be used as attribute names, with the object type name becoming the attribute's domain name.

The mapping in Fig. 9.56 illustrates several of these step 2 considerations as well as step 6 (map ORM constraints to UML graphic constraints, textual constraints, or notes). The {U1} annotation for uniqueness is not standard UML. The value constraint on gender codes is captured using an enumeration type.

In rare cases, value types that are independent play an explicit mandatory role, or play a functional fact role in a 1:n fact type map to classes. The example in Fig. 9.57(a) deals with cases where we store title–gender restrictions (e.g., the title “Mr” is restricted to the male gender).

The example in Fig. 9.57(b) uses a multivalued attribute to store all the genders applicable to a title (e.g., the title “Dr.” applies to both male and female genders). The Title class gives fast access from title to applicable gender, but slow access from gender to title. As discussed earlier, multivalued attributes should be used sparingly.