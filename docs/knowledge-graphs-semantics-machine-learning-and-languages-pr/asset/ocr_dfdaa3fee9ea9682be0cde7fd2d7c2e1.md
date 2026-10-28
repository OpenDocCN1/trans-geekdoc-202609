![](bbox=[0.18, 0.1, 0.85, 0.26])

# Figure 4. Ontologies of the TRANSRAZ Data Model

![](bbox=[0.08, 0.3, 0.95, 0.6])

# Figure 5. A part of the architectural object modeling within the TRANSRAZ Data Model

# 3.2.1. Modeling of City Architecture

The TOPORAZ relational database is the rich resource of the urban entities of the Main Market of Nuremberg. However, the representation of these entities and their relations is diverse and incomplete. In order to provide a comprehensive semantic representation of the tables in the TOPORAZ data model and further sources described in section 4.1, the following requirements have to be addressed:

+   - REQ1: Architectural objects of a city are represented hierarchically. For example, a city consists of districts, a building consists of floors. This representation may include dozens of levels, describing every small part of a building (CQ4.1-2).
+   - REQ2: Attributes of architectural objects rely on historical resources, thus, may be uncertain or incomplete. For example, for some buildings information about exact height, roof shapes, wall openings (windows, doors) and stylistic elements of the facade are provided, while for other buildings only the location area is known.