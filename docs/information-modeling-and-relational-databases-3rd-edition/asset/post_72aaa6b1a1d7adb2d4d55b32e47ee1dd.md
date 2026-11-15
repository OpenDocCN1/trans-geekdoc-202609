
![](img/1344db3eba3d550e6edb009556fcd95c_409_0.png)

FIG. 9.48 Attributes assigned initial values in (a) UML and (b) ORM extension.

The SQL standard treats **null** as a special instance of a default value, and this is supported in UML because the specification notes that “a multiplicity of 0..1 provides for the possibility of null values: the absence of a value”. So, an optional attribute in UML can be used to model a feature that will appear as a column with the default value of null when mapped to a relational database. Presumably, a multiplicity of [0..*] or [0..n] for any n > 1 also allows nulls for multivalued attributes, even though an empty collection could be used instead.

Currently, ORM has no explicit support for initial/default values. A possible extension could allow default values to be specified for ORM roles. At the metalevel, we add the fact type Role has default Value. At the external level, instances of this could be specified on a predicate properties sheet, or entered on the diagram (e.g., by attaching an annotation such as d: value to the role, and preferably allowing this display to be toggled on/off). For example, the role played by NrColors in Fig. 9.48(b) is allocated a default value of 1. When mapped to SQL, this should add the declaration “default 1” to the column definition for ClipArt.nrColors.

To support the composite initial values allowed in UML, composite default values could be specified for ORM roles played by compositely identified object types (coreferenced or nested). When coreferencing involves at least two roles played by the same or compatible object types, an order is needed to disambiguate the meaning of the composite value. For example, in Fig. 9.48(b) the role played by Resolution is assigned a default composite value of (640, 480). To ensure that the 640 applies to the horizontal pixel count and the 480 applies to the vertical pixel count (rather than the other way round), this ordering needs to be applied to the defining roles of the external uniqueness constraint. ORM tools often determine this ordering from the order in which the roles are selected when entering this constraint.

If all or most roles played by an object type have the same default, it may be useful to allow a default value to be specified for the object type itself. This could be supported in ORM by adding the meta fact type ObjectType has default Value and providing some notation for instantiating it (e.g., by an entry in an Object Type Properties sheet or by annotating the object type shape with d: value). This corresponds to the default clause permitted in a create-domain statement in the SQL standard. Note that an object-type default can always be expressed instead by role-based defaults, but not conversely (because the default may vary with the role).

### Specification of default general.

A proposal for providing greater support for default information in ORM is discussed in Halpin and Vermeir (1997), but this goes beyond the built-in support for defaults in either UML or SQL. Default information can be modeled informally by using a predicate to convey this intention to a human. For example, we might specify default medium (e.g., “CD”, “DVD”) preferences for delivery of soft products (e.g., music, video, software) using the 1:n fact type Medium is default preference for SoftProduct.

In cases like this where default values overlap with actual values, we may also wish to classify instances of relevant fact types as actual or default (e.g., Shipment used Medium). For the typical case where the uniqueness constraint on the fact type spans n – 1 roles, this can be achieved by including fact types to indicate the default status (e.g., Shipment was based on Choice {actual, default}), resulting in extra columns in the database to record the status. While this approach is generic, it requires the modeler and user to take full responsibility for distinguishing between actual and default values.

In UML, restrictions may be placed on the changeability of attributes as well as the roles (ends) of binary associations. It is unclear whether changeability may be applied to the ends of n-ary associations. UML 2 recognizes the following four values for changeability, only one of which can apply at a given time:

- unrestricted
- readOnly
- addOnly
- removeOnly

The default changeability is “unrestricted” (any change is permitted). The value “unrestricted” was formerly called “changeable”, which itself was formerly called “none”. The other settings may be explicitly declared in braces. For an attribute, the braces are placed at the end of the attribute declaration. For an association, the braces are placed at the opposite end of the association from the object instance to which the constraint applies.

Recall that in UML, a “link” is an instance of an association. The term “readOnly” (formerly called “frozen”) means that once an attribute value or link has been inserted, it cannot be updated or deleted, and no additional values/links may be added to the attribute/association (for the constrained object instance).

The term “addOnly” means that although the original value/link cannot be deleted or updated, other values/links may be added to the attribute/association (for the constrained object instance). Clearly, addOnly is only meaningful if the maximum multiplicity of the attribute/association-role exceeds its minimum multiplicity. The term “removeOnly” means that the only change permitted for an existing attribute value or link is to delete it.

![](img/1344db3eba3d550e6edb009556fcd95c_411_0.png)

FIG. 9.49 Changeability of attributes and association roles.

As a simple if unrealistic example, see Fig. 9.49. Here employee number, birthdate, and country of birth are readOnly for Employee, so they cannot be changed from their original value. For instance, if we assign an employee the employee number 007, and enter his/her birthdate as 02/15/1946 and birth country as “Australia”, then we can never make any changes or additions to that.

For each employee, the set of languages and the set of countries visited are addOnly. Suppose that for employee 007, we initially set his/her languages to {Latin, Japanese} and countries visited to {Japan}. As long as employee 007 is referenced in the database, these facts can’t be deleted. However, we may add to these (e.g., later we might add the facts that employee 007 speaks German and visited India).

By default, the other properties are changeable. For example, employee 007 might legally change his name from “Terry Hagar” to “Hari Seldon”, and the countries he wants to visit might change from {Ireland, USA} to {Greece, Ireland}.

Some traditional data modeling approaches also note some restrictions on changeability. The Barker ER notation includes a diamond to mark a relationship as nontransferable (once an instance of an entity type plays a role with an object, it cannot play this role with another object). Although changeability restrictions can be useful, in practice their application in database settings is limited.

One reason for this is that facts entered into a database might need to be changed. With snapshot data, this is the norm, but even with historical data changes can occur. The most common occurrence is to allow for corrections of mistakes, which might be because we were told the wrong information originally or because we carelessly made a misspelling or typo when entering the data.

In exceptional cases, we might require that mistakes of a certain kind be retained in the database (e.g., for auditing purposes) but be corrected by entering later facts to compensate for the error. This kind of approach makes sense for bank transactions (see Fig. 9.50). For example, if a deposit transaction for $100 was mistakenly entered as $1000, the record of this error is kept, but once the error is detected it can be compensated for by a bank withdrawal of $900. The balance is both derived and stored, and its readOnly status is typically implied by the readOnly settings on the base attributes, together with a derivation rule.
