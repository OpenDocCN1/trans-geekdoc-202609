+   - one
+   - one and only one
+   - zero or one
+   - many
+   - one or many
+   - zero or many

Modality in ERDs refers to the minimum number of instances of one entity that can be associated with an instance of another entity. It defines whether the participation of an entity in a relationship is optional (0) or mandatory (1).

Consider an example involving data about patients and their medical records in a medical healthcare system. Most patients will have associated medical records, but new patients or newborn children might not have any medical history, therefore this is a type of optional relationship.

On the other hand, if you are to consider an e-commerce platform, every order must be associated with a customer (you cannot become a customer unless you place an order), so that is a type of mandatory relationship.

# Modality of relationships

> > Modality: the minimum number of instances of one entity that can be associated with an instance of another entity.
> > Cardinality: the maximum number of times an instance in one entity can be associated with instances in the related entity.

The cardinality of relationships refers to the nature and extent of relationships between entities in an ERD. It specifies the number of instances of one entity that can or must be associated with each instance of another entity.

Cardinality refers to the maximum number of times an instance in one entity can be associated with instances in the related entity. It describes the “many” side of the relationship and it can be defined as:

+   - one-to-one
+   - one-to-many
+   - many-to-one
+   - many-to-many.

For example, consider a school management system that includes students and clubs as entities.
Entity STUDENT has StudentID, FirstName, LastName, Email as attributes.
Entity CLUB has ClubID, Title, TeacherID, Location as attributes.

The relationship between the two entities can be represented as “a club has many students”.
Cardinality: one student can enrol in multiple clubs (one-to-many).
Modality: a club must have at least one student enrolled (mandatory for clubs); a student might not enrol in any clubs (optional for students).

![](bbox=[0.108, 0.578, 0.425, 0.772])

Understanding both cardinality and modality is essential for accurately modelling the relationships and constraints in a database, ensuring it effectively reflects the real-world requirements and business rules.

> ### ACTIVITY
> Social skills: Support other students with application skills on practical tasks – help your classmates to analyse different database scenarios, identify entities, establish the appropriate relationships between tables and provide feedback to each other on how appropriate ERDs can be created.