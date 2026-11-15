![](bbox=[0.24, 0.09, 0.73, 0.24])

FIG. 9.5 A simple reference scheme in ORM, shown (a) explicitly and (b) implicitly.

no icons. References verbalize as existential sentences, such as “There is an Employee who has the EmployeeNr 101”. Entity instances are referenced elsewhere by definite descriptions, such as, “The Employee who has the EmpNr 101”.

In a relational database, we might use the preferred reference scheme to provide value-based identity or instead use system-generated row-ids. In an object-oriented implementation, we might use oids (hidden, system-generated object identifiers). Such choices can be added later as annotations to the model. For analysis and validation purposes, however, we need to ensure that humans have a way to identify objects in their normal communication. It is the responsibility of humans (not the system) to enforce constraints on preferred reference types. Assuming humans do enforce the reference type constraints, the system may be used to enforce the elementary fact type constraints.

UML classifies instances into objects and data values. UML objects basically correspond to ORM entities, but are assumed to be identified by oids. Although UML does not require entities to have a value-based reference scheme, we should include value-based reference in any UML class to capture all the conceptual semantics. UML data values basically correspond to ORM values: they are constants (e.g., character strings or numbers) and so require no oids to establish their identity. Entity types in UML are called classes, and value types are basically data types. Note that “object” means “object instance”, not “object type”. A relationship instance in UML is called a link, and a relationship type is called an association.

# 9.3 Attributes

Like other ER notations, UML allows relationships to be modeled as attributes. For instance, in Fig. 9.6(a) the Employee class has eight attributes. The corresponding ORM diagram is shown in Fig. 9.6(b).

In UML, attributes are mandatory and single valued by default. So the employee number, name, title, gender, and smoking status attributes are all mandatory. In the ORM model, the unary predicate “smokes” is optional (not everybody has to smoke). UML does not support unary relationships, so it models this instead as the Boolean attribute “isSmoker” with possible values True or False. In UML, the domain (i.e., type) of any attribute may optionally be displayed after it (preceded by a colon). In this example, the domain is displayed only for the isSmoker attribute. By default, ORM tools usually take a closed world approach (CWA) to unaries, which agrees with the isSmoker attribute being mandatory.