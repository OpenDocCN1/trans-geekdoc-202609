
The simplest kind of object is a `value` (e.g., character string). `Entities` are real or abstract objects that are identified by their relationships to other objects (typically values). For example, a country may be identified by its name.

`Static constraints` determine the allowable populations of fact types. `Dynamic constraints` restrict transitions between these populations. For example, each city is the capital of at most one country, and no adult may become a child.

Each fact in a conceptual database is typically `elementary`. The addition or deletion of a fact is a simple update. In a `compound transaction`, several simple updates may be included; in this case, constraints apply only to the net effect of the complete update sequence, not to each individual update. Updates and queries on a conceptual database or conceptual schema are responded to by the CIP.

Each DBMS conforms to a `logical` data model (e.g., network, hierarchic, or relational). If a relational DBMS is chosen for the implementation, the conceptual schema is mapped to a `relational schema`, or relational database schema. Here, all the stored facts are placed in named `tables`, with named columns and unnamed rows. Each row of a relational table typically corresponds to one or more elementary facts. Each cell (row-column position) contains at most one value. Within a table, no row may be duplicated.

The population of a relational table may be changed by inserting, deleting, or modifying a row. Most conceptual constraints and derivation rules can be expressed within the relational DBMS language or by interfacing to another language.

The `information systems life cycle` typically involves the following stages: feasibility study; requirements analysis; conceptual design of data and processes; logical design; basic physical design; basic external design; prototyping; implementation of production version; testing and validation; release of software, documentation, and training; and maintenance. Feedback from a later stage may indicate a need to rework earlier stages.

Careful attention to earlier stages reduces the overall effort involved, as does the reuse of design strategies used previously on similar applications. For large projects, an iterative approach to development is generally recommended, where the life cycle is applied to one component before moving onto another component.

Various frameworks for information system architecture exist. The Zachman framework is composed of five rows that view the system from different perspectives (scope, enterprise model, system model, technology model, and details) and six columns with a different focus (data, function, network, people, time, and motivation). The extended four-schema framework uses the same six columns, but has six rows for conceptual, external, logical-persistent, logical-transient, physical-persistent, and physical-transient perspectives. Other well-known system architectures include TOGAF, MDA, and RM-ODP.

### Chapter Notes

The classic discussion of the conceptual, internal, and external schemas of an information system is given in [van Griethuysen (1982)](#Ch002_27-57_B9780443237904000128.xhtml#bb1280). Some people who worked on this ISO standard also worked on the FRISCO report ([Falkenberg et al., 1998](#Ch002_27-57_B9780443237904000128.xhtml#bb0435)). Along with many other authors (e.g., [Elmasri and Navathe, 1994](#Ch002_27-57_B9780443237904000128.xhtml#bb0365)), we consider the relational model of data to be a `logical` model rather than a conceptual model, mainly because it is too distant from natural language. From this viewpoint, a relational schema represents the logical portion of an internal schema (omitting details specific to the chosen DBMS, and storage and access details such as indexes). [Codd (1990, pp. 33–34)](#Ch002_27-57_B9780443237904000128.xhtml#bb0235) proposes an alternative interpretation of the three-level architecture, in which the base relations of a relational database provide the conceptual schema, and views provide an external schema.

A standard reference on requirements analysis is the ANSI/IEEE standard 830-1984. A comparative review of different approaches to information system work is given in [Olle et al. (1991)](#Ch002_27-57_B9780443237904000128.xhtml#bb1045). An informative overview of key issues in information systems modeling is provided by [Mylopoulos (1998)](#Ch002_27-57_B9780443237904000128.xhtml#bb1020). [Pohl (1994)](#Ch002_27-57_B9780443237904000128.xhtml#bb1075) gives a detailed treatment of the specification, representation, and agreement dimensions of requirements engineering. [Bubenko (2007)](#Ch002_27-57_B9780443237904000128.xhtml#bb0130) provides a historical perspective on information systems modeling.

Data model patterns for various business domains are available in a number of books, including [Hay (1996](#Ch002_27-57_B9780443237904000128.xhtml#bb9035), [2006)](#Ch002_27-57_B9780443237904000128.xhtml#bb0830) and [Silverston (2001a](#Ch002_27-57_B9780443237904000128.xhtml#bb1180), b). These sample models are usually expressed in one of the ER notations covered later in this book.

[Zachman (1987)](#Ch002_27-57_B9780443237904000128.xhtml#bb1325) introduces his architectural framework (see [https://en.wikipedia.org/wiki/Zachman_Framework](https://en.wikipedia.org/wiki/Zachman_Framework)). [Hay (2003)](#Ch002_27-57_B9780443237904000128.xhtml#bb0825) provides an extensive discussion of the Zachman framework, and argues that some of the row descriptors should be renamed.

Details on TOGAF may be accessed online at [www.opengroup.org/togaf/](http://www.opengroup.org/togaf/) and at [http://en.wikipedia.org/wiki/TOGAF](http://en.wikipedia.org/wiki/TOGAF). For resources on the MDA approach of the OMG, see [http://www.omg.org/mda/](http://www.omg.org/mda/). For the ISO RM-ODP standard, see [http://committee.iso.org/sites/jtc1sc7/home/projects/flagship-standards/isoiec-10746.html](http://committee.iso.org/sites/jtc1sc7/home/projects/flagship-standards/isoiec-10746.html). For further details on RM-ODP, see [https://en.wikipedia.org/wiki/RM-ODP](https://en.wikipedia.org/wiki/RM-ODP) and [https://rm-odp-new.lcc.uma.es/](https://rm-odp-new.lcc.uma.es/).

## References[⁴](#fn4)

*   [Bubenko J.](#Ch002_27-57_B9780443237904000128.xhtml#B-bb0130)  From information algebra to enterprise modelling and ontologies—a historical perspective on modelling for information systems. In: Krogstie J., Opdahl A., Brinkkemper S., eds. *Conceptual Modelling in Information Systems Engineering.* Berlin: Springer; 2007:1–18.

*   [Codd E.](#Ch002_27-57_B9780443237904000128.xhtml#B-bb0235) * The Relational Model for Database Management: Version 2.* Reading, MA: Addison-Wesley; 1990.

*   [Elmasri R., Navathe S.](#Ch002_27-57_B9780443237904000128.xhtml#B-bb0365) * Fundamentals of Database Systems.* second ed. Redwood City, CA: Benjamin/Cummings; 1994.

*   [Falkenberg E., Hesse W., Lindgreen P., Nilson B., Oei J., Rolland C., Stamper R., Van Assche F., Verrijn-Stuart A., Voss K.](#Ch002_27-57_B9780443237904000128.xhtml#B-bb0435) * A Framework of Information System Concepts: The FRISCO Report (Web Edition).* IFIP; 1998. Available online by anonymous [ftp://ftp.leidenuniv.nl/pub/rul/fri-full.zip](ftp://ftp.leidenuniv.nl/pub/rul/fri-full.zip).

*   Hay D. * Data Model Patterns: Conventions of Thought.* New York: Dorset House; 1996.

*   [Hay D.](#Ch002_27-57_B9780443237904000128.xhtml#B-bb0825) * Requirements Analysis.* New Jersey: Pearson Education; 2003.

*   Hay D. * Data Model Patterns: A Metadata Map.* Morgan Kaufmann; 2006.

*   [Jarke M., Mylopoulos J., Schmidt J., Vassiliou Y.](#Ch002_27-57_B9780443237904000128.xhtml#B-bb0850)  DAIDA: An Environment for Evolving Information Systems. *ACM Trans. Inform. Syst.* 1992;10(1):1–50.
