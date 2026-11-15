
- (soft) real-time indication of places where important events occur;
- search for information about asset parts by topological criteria with respect to displayed relations.

## 6.6 Electronic Document Management

A document is a uniquely identified self-contained unit of information readable by a human or a machine. Each document has metadata associated with it: title, author(s), keywords, and so on. Various standards apply to define the metadata structure and semantics, preferably with references to the domain ontology [22]. For permanent storage, documents annotated with metadata are placed into an archive organized in a hierarchy of folders according to document subjects. The archive often has a paper backup, into which hard copies of electronic documents are printed and from which incoming paperwork is scanned. The paper backup helps to avoid losses and unauthorized changes. Yet, nowadays, another approach to prevent tampering with documents is available: the hash of the document is stored in a blockchain upon creation and verified upon access.

The following use cases are relevant for electronic documentation as a DT part:

- presentation of information about the asset in a self-contained semi-structured human-readable form;
- identification and verification of reasons and permissions to execute control actions;
- extraction of ontological concepts, relationships, and axioms;
- designing digital diagrams and visuals;
- updating and verification of the information model;
- updating and verification of real-time data;
- search for documents by context and metadata;
- collecting the documentation archive.

## 6.7 Master Data Management

Master data describe an asset structure and static properties, providing context for asset business transactions and operation (including parameters for mathematical models). Structured in the machine-readable form of entities, attributes, and relationships, the master data constitute the asset information model. Master data can be imported into the information model from the asset documentation as well as exported from the model to documents.

The most convenient storage for master data is a relational database. It provides a number of advantages, including data accuracy, integrity, flexibility, scalability, and security [23]. For example, consider a power system information model. Its core consists of a comprehensive database of installed power and control equipment: generators, transformers, electrical power consuming equipment, switches, controllers, telecommunication channels, and so on. The database tables form an inheritance hierarchy by equipment taxonomy. Each table has numerous class-specific attributes that describe the equipment in every aspect: identification, performance, operating conditions, ownership/rent, cost, control, maintenance, etc. Ancillary tables store information to which equipment database records refer: about energy facilities, grid topology, measurement, and control channels.

The main use cases for the information model as a DT component are:

- supplying mathematical and simulation models with master data;
- fine-grained binding of real-time data to the asset parts;
- assigning unique identifiers to parts;
- fine-grained part-wise data access control;
- collecting the history of asset changes during its lifecycle;
- verifying master data by comparing with the factual asset structure;
- attribute-based search for information about parts;
- generation and verification of the asset design and construction documentation;
- visualization of the asset structure and properties of parts in tables and hierarchy trees.

## 6.8 Ontological Modeling

A domain ontology is a widely recognized tool to improve interoperability between disparate models. An ontology formally describes the logical structure of the domain concepts, including their definitions, properties, and relationships with each other. When designing any model presented in the previous sections, the ontology applies as a semantically solid source of domain terms and knowledge.

The ontology is represented as a taxonomy tree of concepts that are endowed with properties of various types, associated by various relationships (equivalence, proximity, partonomy, etc.), constrained by various axioms, and instantiated in various individuals. It is possible to automatically infer nontrivial knowledge from axioms by applying deductive rules of the so-called descriptive logic. In a machine-readable form, the ontology is written on the OWL (Ontology Web Language) using various tools such as the interactive editor Protégé.

In ontologies useful as the semantic basis of a DT, the central role is played by the taxonomy of *Processes* to be twinned: monitoring, steering, maintenance, and so on. Taxonomies of other top-level concepts relate to them: *Events* trigger processes, *Actors* initiate processes and participate in them, equipment and other *Resources* are used/affected, and *Models* formally represent everything [24]. Axioms express physical laws, design rules, and control objectives.

For example, ontology modeling has a long history in the electric power industry [25]. A reference source of the domain concepts is the Common Information Model (CIM) specified in the standards IEC 61968, 61970, and 62325 for interoperability across electricity-related information systems. However, CIM doesn't describe energy processes, hence is insufficient for a DT. Some missing concepts are specified in the Smart Appliances REFerence (SAREF) family of ontologies designed for interaction with IoT devices, the Domain Analysis–Based Global Energy Ontology (DABGEO) that claims to be a complete semantic description of energy management scenarios, and to other relevant sources.

The ontology applies as the semantic basis of a DT in the following use cases:

- information model structure generation;
- reference data maintenance;
- communication protocols design;
- development of quality models of services;
- development of document templates and user interface forms;
- axiomatic inference and verification of design decisions;
- learning the subject domain.

## 6.9 Algebraic Approach to Digital Twin Composition

To automate the DT composition, especially when employing the generative design, a rigorous formal description and verification technique is much desired. As stated in the Introduction, such a technique is feasible to build upon the mathematical framework of category theory. Category theory allows to separate compositionality from other aspects of models by shifting the representation focus from their internal contents to behavior with respect to each other (a systems engineer’s “black box” point of view).

Recall that a category is a class of abstract objects pairwise related by morphisms (arrows). The precise definition takes just a few lines: a category C consists of a class of objects Ob C and a class of morphisms Mor C endowed with the following operations. Firstly, two objects are associated with each morphism f: a domain (arrow source) dom f and a codomain (target) codom f, so that the pair of equalities dom f=A and codom f=B is depicted as an arrow f : A → B. Secondly, for any pair of morphisms f, g that satisfies the condition codom f=dom g, the composition of morphisms g ∘ f : dom f → codom g is defined, and it is associative: for any three morphisms f, g, h such that codom f=dom g and codom g=dom h, the equality h ∘ (g ∘ f)=(h ∘ g) ∘ f holds. Thirdly, any object A has an associated identity morphism 1A : A → A such that f ∘ 1A=1B ∘ f=f for any morphism f : A → B. A classic example of a category is Set that consists of all sets and all maps between sets: the composition law for maps is defined by the standard substitution, and the identity map of a set sends each element to itself.

In the MBSE context, we denote by C a category used as a virtual “model catalog”. Objects of such a catalog category are all possible models of a certain kind. Its morphisms describe all actions that could be performed with models when composing systems from components. Depending on the kind of models, actions include variable substitution, reference resolution, embedding of a submodel, quotienting, etc. It is easy to see that C is indeed a category since it has composition of morphisms (sequential execution of actions) and identity morphisms (idle “doing nothing” action with any model). A configuration of a complex system composed of multiple models, such as a DT, is represented as a diagram in C.

For example, consider the categorical representation of an information model [26]. Here, objects are sets of typed data that populate database tables, and morphisms are generated by foreign keys as maps between tables that combine them into data sets with a complex structure. Hence, all possible information models pertaining to a certain domain constitute a subcategory of Set. A diagram in such a category shows how to compose a database.

Mathematical models, being the most important among DT components, are the most technically difficult to represent categorically. For example, a categorical representation of DERs as finite automata with states labeled by power demand regions is proposed to formalize DER aggregation and solve a power flow problem [27]. As a less involved yet apt example, consider discrete-event simulation. Recall from Section 6.3 that the simulation is a discrete sequence of typed events that represents some operational scenario. Algebraically, a scenario is represented by a set of events partially ordered by causal dependencies and labeled by event types; scenario assembling actions are defined as maps that preserve the order and the labeling (i.e. homomorphisms) [28]. All scenarios and assembly actions constitute a category denoted as Pomset.
