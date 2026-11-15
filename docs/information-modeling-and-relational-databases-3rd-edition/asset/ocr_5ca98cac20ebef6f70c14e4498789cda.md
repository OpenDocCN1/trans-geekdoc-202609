instances. One may then apply a meta constraint (e.g., antirigid properties cannot subsume rigid properties) to impose restrictions on subtyping (e.g., Patient cannot be a supertype of Person).

Guizzardi et al. (2004) proposed a UML profile to stereotype classes into kinds, subkinds, phases, roles, categories, roleMixins, and mixins, together with a set of meta constraints, to help ensure that UML class models are ontologically well formed. Guizzardi (2005) used this modeling profile in his doctoral thesis on ontological foundations for conceptual information models.

While the aforementioned research provides valuable contributions, we have some reservations about its use in industrial information systems modeling. Our experience with industrial data modelers suggests that the seven-classes scheme would seem overly burdensome to the majority of them.

A simpler alternative that we are currently considering for ORM 2 classifies each subtype as either a rigid subtype or a role subtype. A type is rigid if and only if each instance of that type must belong to that type for its whole lifetime (in the business domain being modeled). Examples include Person, Animal, and Book.

In contrast, an instance of a role type need not always be an instance of that type during its lifetime (in the business domain). Here, we use “role” liberally to include a role played by an object (e.g., Manager, Student, Patient—assuming that these are changeable in the business domain) as well as a phase or state of the object (e.g., Child, Adult, Faulty-Product—assuming changeability).

Although this rigid/role classification scheme applies to any type, we typically require this distinction to be made only for subtypes (to control subtype migration and reduce the classification burden for modelers). As an example, Fig. 10.32 depicts Dog and Cat as rigid subtypes in ORM and UML.

The rigidity notation suggested for ORM is square bracketing of the subtype name (violet for alethic; blue with “o” for deontic, e.g., changing from male to female might be possible but forbidden).

The NORMA tool does not yet support this notation to classify subtypes, but it may be informally noted in the subtype’s Note property. For UML, we chose a rigid stereotype. Rigidity is a dynamic constraint rather than a static constraint because it restricts state changes (e.g., no dog may change into a cat).

![](bbox=[0.346, 0.75, 0.656, 0.85])

FIG. 10.32 Rigid subtypes depicted in (a) ORM and (b) UML.