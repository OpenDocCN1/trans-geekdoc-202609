![](bbox=[0.16, 0.1, 0.81, 0.33])

FIG. 18.17 A data flow diagram for part of the pharmacy subsystem.

The external schemas may now be developed for the various categories of user. It is through the interaction of users with the external interface that the original functions specified in the requirements analysis phase are ultimately executed. Hence, it is important to design the external interface in a way that naturally reflects these functions.

Fundamentally, all that happens when users interact with an information system is that elementary facts are added, deleted, retrieved, or derived. In principle, we could specify the process perspective in terms of these two update and two query operations. But this is too fine a level of granularity for humans to work with efficiently.

We need a way of grouping these elementary operations into larger units. It is often natural to think of operations being performed on significant objects, such as patients and stock items. The major object types abstracted from an ORM schema (see previous section) correspond closely to these object types, and hence provide a good basis for defining operations. The more important classes or entity types in UML class diagrams or ER diagrams provide another good choice for this.

A generic set of external update operations may now be generated with three varieties: add object, delete object, and modify object. Some generic query operations may be generated (e.g., list all facts about an object), but specific queries require an appropriate selection of the relevant fact types (stored or derived).

Users perform such operations through an external interface, typically screen forms or menus. For each screen, we need to consider content (which fact types and operations to include), format (how the screen is displayed), and use (how the operations are invoked by the user). As discussed, default decisions about screen content may be based on operations on the major object types. For example, if Patient is a major object type for the hospital system, a screen is required for it with at least the operations add Patient, modify Patient, delete Patient, show Patient.

Unlike conceptual and logical tables, forms may overlap in their content. This redundancy at the external level conveniently allows users to perform an operation whenever