
ER diagrams typically hide attribute domains. For example, the `birthdate` and `deathdate` attributes in the Barker ER model shown in [Fig. 1.7](#Ch001_1-25_B9780443237904000062.xhtml#f0040)(b) should be based on the domain `Date`, but this is not represented visually. In ER, attribute domains can be listed in another document.

In UML class diagrams, attribute domains may be listed after the attribute name and multiplicity (if shown), as in [Fig. 1.7](#Ch001_1-25_B9780443237904000062.xhtml#f0040)(c). The “\[0‥1\]” multiplicity indicates “at most one”, so the attribute is optional and single-valued. However all too often in practice, only *syntactic*, or value, domains are specified (e.g., `String`).

An ER diagram might show `population` and `elevation` as attributes of `City`, and an associated table might list the domains of these attributes simply as `Integer`, despite the fact that it is nonsense to equate a population with an elevation.

Conceptual object types, or semantic domains, provide the conceptual “glue” that binds the various components in the application model into a coherent picture. Even at the lower level of the relational data model, E.F. Codd, the founder of the relational model, argues that “domains are the glue that holds a relational database together” ([Codd, 1990](#Ch001_1-25_B9780443237904000062.xhtml#bb0235), p. 45).

The object types in ORM diagrams are the semantic domains, so the *connectedness* of a model is transparent. This property of ORM also has significant advantages for conceptual queries because a user can query the conceptual model directly by navigating through its object types to establish the relevant connections. This notion is elaborated further in later chapters.

ER and UML diagrams often fail to express relevant *constraints on, or between, attributes*. [Fig. 1.8](#Ch001_1-25_B9780443237904000062.xhtml#f0045) provides a simple example. Notice the circled dot over an “X” in the ORM model in [Fig. 1.8](#Ch001_1-25_B9780443237904000062.xhtml#f0045)(a). This specifies two constraints: the dot is a mandatory constraint over the disjunction of the two roles (each truck is either bought or leased) and the “X” indicates the roles are exclusive (no truck is both bought and leased). The two constraints collectively provide an *exclusive-or (xor) constraint* (each truck plays exactly one of the roles).

![Fig. 1.8 (a) ORM model. (b) UML model, revealing less detail.](images/B9780443237904000062/f01-08-9780443237904.jpg)

[Fig. 1.8](#Ch001_1-25_B9780443237904000062.xhtml#B-f0045) (a) ORM model. (b) UML model, revealing less detail.

Unlike most versions of ER, UML does provide an xor constraint, but only between associations. Because the UML model in [Fig. 1.8](#Ch001_1-25_B9780443237904000062.xhtml#f0045)(b) models these two fact types as attributes instead of associations, it cannot capture the constraint graphically (other than adding a note). Notice again how the ORM diagram reveals the semantic domains. For instance, `tare` may be meaningfully compared with `maximum load` (both are masses) but not with `length`. In UML, this can be made explicit by appending domain names to the attributes. At various stages in the modeling process, it is helpful for the modeler to see all the relevant information in one place.

Another ORM feature is its flexible support for *subtyping*, including multiple inheritance, based on formal subtype definitions. For example, the subtype `LargeUSCity` may be defined as a `City` that is in `Country` “US” and has a `Population` > 1,000,000. As discussed in a later chapter, subtype definitions provide stronger constraints than declarations about whether subtypes are exclusive or exhaustive.

In principle, there are infinitely many kinds of constraints, so a textual constraint language may be required for completeness to supplement the diagram. This is true for ER, ORM, and UML. However, the failure of ER and UML diagrams to include standard notations for many important ORM constraints makes it harder to develop a comprehensive model or to perform *transformations* on the model.

For example, suppose that in a movie an actor may have a starring role or a supporting role but not both. This can be modeled by two fact types: *Actor* has starring role in *Movie*; *Actor* has supporting role in *Movie*. The “but not both” condition is expressed in ORM as a pair-exclusion constraint between the fact types. Alternatively, these fact types may be replaced by a ternary: *Actor* in *Movie* has role of *RoleKind* {star, support}.

Transformations are rigorously controlled in ORM to ensure that constraints in one representation are captured in an alternative representation. For instance, the pair-exclusion constraint is transformed into the constraint that each `Actor-Movie` pair has only one `RoleKind`. The formal theory behind such transformations is easier to apply when the relevant constraints can be visualized.

Unlike UML and ER, ORM was built from a linguistic basis. To reap the benefits of verbalization and population for communication with and validation by domain experts, it’s better to use a language that was designed with this in mind. The ORM notation is easy to learn and has been successfully taught to high school students.

We are not arguing here that ER and UML have no value. They do. We are simply suggesting that you consider using ORM’s modeling techniques, and possibly its graphic notation, to facilitate your original conceptual analysis before using an attribute-based notation such as that of ER, UML, or relational tables.

After validating the conceptual model with the domain expert, you map it to a target such as a DBMS or program code for implementation. At this lower level, you may prefer an attribute-based model to give a compact picture of how facts are grouped into implementation structures. For database applications, you will want to see the table structures, foreign key relationships, and so on. Here, a relational or object-relational model offers a compact view, similar to an ER or UML model.

ORM models often take up much more space than an attribute-based model because they show each attribute as a relationship. This is ideal for conceptual analysis, where we should validate one fact type at a time. However, for logical design, we typically group facts into attribute-based structures such as tables or classes. At the logical design stage, attribute-based models are more useful than ORM models. For example, relational schema diagrams provide a simple, compact picture of the underlying tables and foreign key constraints between them. Also, UML is well suited for the logical and physical design of object-oriented code because it allows implementation detail on the data model (e.g., attribute visibility and association navigation) and can be used to model behavior and deployment.

Having used ER, ORM, and UML in practice, we’ve found that ORM often makes it easier to get the model right in the first place and to change the model as the business domain evolves. We believe in the method so strongly that we’ve made it the basis for much of the modeling discussion in this book. Once you understand ORM’s modeling principles, you’ll find it much easier to gain a proper understanding of data modeling in ER and UML.

Arguments about modeling approaches can become heated, and not everyone is as convinced of the virtues of ORM as we are. All we ask is that you look objectively at the ideas presented in this book and consider using whatever you find helpful.

Although the book focuses on ORM, it also covers data modeling in other popular notations (e.g., ER, IDEF1X, UML, and relational). These other notations have value too. Even if you decide to stay with ER or UML as your conceptual analysis approach, insight into ORM should make you a better modeler regardless.

## 1.3 Historical Background
