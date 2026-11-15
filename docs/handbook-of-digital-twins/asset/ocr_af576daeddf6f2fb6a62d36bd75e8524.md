attributes, and relationships, the master data constitute the asset information model. Master data can be imported into the information model from the asset documentation as well as exported from the model to documents.

The most convenient storage for master data is a relational database. It provides a number of advantages, including data accuracy, integrity, flexibility, scalability, and security [23]. For example, consider a power system information model. Its core consists of a comprehensive database of installed power and control equipment: generators, transformers, electrical power consuming equipment, switches, controllers, telecommunication channels, and so on. The database tables form an inheritance hierarchy by equipment taxonomy. Each table has numerous class-specific attributes that describe the equipment in every aspect: identification, performance, operating conditions, ownership/rent, cost, control, maintenance, etc. Ancillary tables store information to which equipment database records refer: about energy facilities, grid topology, measurement, and control channels.

The main use cases for the information model as a DT component are:

+   • supplying mathematical and simulation models with master data;
+   • fine-grained binding of real-time data to the asset parts;
+   • assigning unique identifiers to parts;
+   • fine-grained part-wise data access control;
+   • collecting the history of asset changes during its lifecycle;
+   • verifying master data by comparing with the factual asset structure;
+   • attribute-based search for information about parts;
+   • generation and verification of the asset design and construction documentation;
+   • visualization of the asset structure and properties of parts in tables and hierarchy trees.

# ## 6.8 Ontological Modeling

A domain ontology is a widely recognized tool to improve interoperability between disparate models. An ontology formally describes the logical structure of the domain concepts, including their definitions, properties, and relationships with each other. When designing any model presented in the previous sections, the ontology applies as a semantically solid source of domain terms and knowledge.

The ontology is represented as a taxonomy tree of concepts that are endowed with properties of various types, associated by various relationships (equivalence, proximity, partonomy, etc.), constrained by various