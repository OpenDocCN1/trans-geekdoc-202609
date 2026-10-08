
## 5 Platform Independent Manufacturing Model: Manufacturing Blueprints and Meta-programming Environment

The Digital Twin Model and Meta-Programming Language are a manufacturing-specific DT model and lightweight programmable language that establishes digital threads. They encompass manufacturing domain knowledge together with the regulations of what kind of knowledge should be recorded about each manufacturing element, how these factors can be related, and how this knowledge can be aggregated and reused. In essence, the DT-KM realize the PIM model.

## 5.1 Manufacturing Blueprints: Essential Characteristics of Self-Describing Products and Production Processes

Digital Twin in this chapter amalgamates artificial intelligence, machine learning, big data, and Internet of Things technologies that are essential for smart manufacturing. The core element is DT-KM. This is essentially a knowledge-centric model that combines products, services, components, and programs by composing and analyzing product/manufacturing data to create knowledge for data-driven and fact-based decision-making. The DT-KM programmable abstraction type is called the manufacturing blueprint type (or simply blueprint). They transform traditional products into self-describing products by storing, linking, combining, and analyzing data collected throughout the product life cycle. Blueprints rely on model engineering paradigm to manage and link product data and information, including content and context, product portfolios and product families, and manufacturing assets (people, plants, machinery, production line equipment), helping to meet the constraints and requirements (features, quality, performance, time, etc.) of the entire manufacturing ecosystem.

This information can be faced in a broader operational context, forming the basis for generating “intelligence” and the steps to more factual data-driven decision-making. The DT-KM encapsulates supplier, product and production knowledge into five interleaved and extensible knowledge types, illustrated in Fig. 2. They support the three DT facets outlined in Sec. 3 as follows:

**Product facet**—captures relevant direct and indirect information about products and services through the following blueprint types:

- *Supplier blueprint*: Defines the business and technical details of the partner company, such as production capacity details and production capabilities.

![](img/accb0e713daa15f4a51070565405380d_120_0.png)
Fig. 2 Manufacturing blueprint types and its meta-programming environment

- *Product blueprint*: Represents the specification of standard or configurable products, product parts, and/or materials. This information is combined with other pertinent data such as product characteristics or order information, machine information, and any entities needed to accurately represent the product and facilitate production work. It also contains product family definitions and links them to products, components, and materials.

- *Service blueprint*: Represents the properties and attributes of services connected with the physical product (as captured in the Product blueprint), to meet the requirements of manufacturers and customers. This includes service types, service metrics, service plans, service scopes, sensors, orders constructed from service plans, compliance standards, service history data, and cost estimates.

- **Production facet**—the production process integrates the customized product facet into optimized and efficient production processes and schedules. This knowledge is modeled by the following:

- *Process blueprint facet*: Exhibits manufacturing solutions and standard assemblies associated with optimal manufacturing execution plans that embed integrated business processes into workflows and connect the events/actions of activities related to all elements of manufacturing on the factory floor. This facet supports digital threads.

- *Performance facet*: the performance facet is linked to the production facet to achieve production performance characteristics to analyze operational data/information and enhance product and service quality leading to efficient production. This facet comprises:

- **Quality assurance blueprint:** Defines product quality KPIs (metrics) and process performance to monitor production operations in (near real time and resolve operational and supply chain issues. The aim is to notify/alert human operators when significant events occur and be to take corrective action as needed.

These manufacturing blueprints enable humans and software to share a common understanding of manufacturing knowledge. They allow manufacturing knowledge to be reused and extended, explicitly specify assumptions about the manufacturing domain, separating manufacturing knowledge from operational knowledge, and support the analysis of manufacturing knowledge, leading to deep insights and fact-based, data-driven, smarter decision-making. Blueprint models are generic by nature but can be easily scaled in stages to take a form specific to a particular type of industry structure.

To support versatility and interoperability, the blueprint models and languages rely on industry-wide production, as the product description in the EXPRESS data modelling standard ISO 10303 (or STEP) for product data representation and exchange standards ISA-88/95. It will also consider the ISO/CD 23247-1 digital twin framework standard, which is under development.

The implementation of the blueprinting detailed conceptual model and its meta-programming language (discussed in detail in the following subsection) is based on the Ontology Web Language' (OWL) and SPARQL, respectively, which are formally based on Description Logic [31]. This enables the adaption of diverse types of reasoning; the verification of properties, preferences, and constraints; and the checking of the consistency of the manufacturing knowledge. The blueprinting detailed conceptual model is outside the scope of this article.

## 5.2 Blueprint Meta-programming Language

The blueprint meta-programming language launches digital threads by allowing developers to define custom behavior for fundamental language operations using the abstraction mechanisms in the DT-KM. To that end, we provide programming support, fact-based and data-driven decision-making processes, and connect all stakeholders to a centralized, searchable knowledge base. It shapes the digital twin by capturing context-specific knowledge (structure, manufacturing, quality, and sensor-specific information) about the appropriate configurations and combinations of parts, components, and materials that can be linked to the required processes that are to be performed in its production.

> ¹OWL 2: https://www.w3.org/TR/owl-features/
> ²SPARQL 1.1 Query Language: https://www.w3.org/TR/spar11-query/

The blueprint meta-programming language is implemented as a graphical DSL; however, in the following discussion, the language is presented textually. Thus, the blueprint meta-programming language provides programming support through high-level operators that process the five blueprints:

- **Blueprint definition operators**—These provide the notations needed to define the five blueprints listed. In particular, this operator is represented textually as insertIndividual(p), which inserts an instance of a specific class into the DT-KM.

- **Blueprint manipulation operators**—These provide a set of operators to save and retrieve blueprints maintained in the DT-KM and compose assemble/compose products from product assembly/composition consists of an assembly of individual parts and a production plan for each assembled/composed part. Blueprint assemblies use a “compose” operator to connect a set of compatible blueprints to end to (e.g., product-to-product or service-to-service combinations). In particular:
  - `retrieve(A)` returns all blueprints that satisfy the criteria/conditions in predicate A two instances of the same type and returns a new blueprint instance pq.
  - `compare(p, q)` compares two blueprint instances p, q of the same type and returns T if the two are equivalent and F, otherwise. Two blueprints are equivalent if their components, parts, characteristics, and materials are identical.
  - `diff(p,q)` returns the difference between two blueprints of the same type p, q.

- **Query services**—query blueprints or zoom in individual blueprints to extract valuable information for data-driven smart-making. In particular: `query(A)` returns T if query request captured by predicate A is satisfied and false otherwise. Expressive classes of query patterns are identified and formalized to require query patterns. This is outside the scope of this chapter.

## 6 Application of the Manufacturing Programming Environment on a Pilot Case

To demonstrate the DT approach in this chapter, we present a real-life “made-to-order” pilot case provided by PRIMA Industries (a leading company manufacturing laser and sheet metal machinery). The pilot case deals with “distributed production on demand,” which is a scenario in which the DT approach can enable a smart manufacturing ecosystem that is formed when different manufacturing units work together to meet customers’ needs.

This pilot case assumes that a turbine engine manufacturer orders a multi-axis 3D cutting, drilling, and welding laser system to process parts of a turbofan used
