
## 4. Data Model

To further guide the modelling of object provenance information, we investigate this in the form of a case study concerning six ethnographic objects that are described in two different provenance reports “Provenance #1” [26] and “Provenance #2” [27], issued by the Dutch National Museum of World Cultures (NMVW)⁷ to embed provenance of artworks into its practice and policy. They describe objects with rich provenance information elicited by extensive provenance research on these objects.

⁷ [http://wereldculturen.nl/](http://wereldculturen.nl/)

One object, RV-1148-1 is an elephant tusk that was part of the extensive provenance research on collections from Benin City. This provenance research aimed to assess the strength of connection to the military campaign led by British forces against Benin City in early February 1897; the research can be found in the report “Provenance #2” [27]. The rest of the objects (RV-2584-169a, RV-2334-1, RV-2334-2, RV-2334-3 and RV-2334-1) are from “Provenance #1” [26], where two different types of provenance information are found. On one side, RV-2584-169a is an interesting case-study because of having different possible theories of the acquisition and/or origin of the object, which left the researcher incapable of concluding on one theory with a high degree of certainty. On the other hand, the objects with id RV-2334-* are insightful because of their complicated chain of custody and links to different archival material. Despite the diversity in information, what is common in all the objects is that there have been discovered possible links to important historical events or time-periods, which projects unethical acquisition in the objects’ chain of custody. The diversity in information, possible links to different historical events and time-periods, and available connections to different archival materials make these objects an ideal case study for the current research. These objects not only refer to the requirements identified by the previous section but also represent the complex nature of such knowledge. In the following subsection, we will describe our modelling choice for the proposed data model.

The first step is to reconstruct the information of these objects to identify essential statements related to the object’s provenance from the textual report. This information is translated to provenance data that illustrates the key components considered necessary for representing the artefact’s provenance. For this research, we investigated the use of CIDOC-CRM to ensure reusability.

### 4.1. Object

Our requirements indicate there are various types of knowledge about the object to represent. First-level object information is essential even if detailed provenance is unknown. As one respondent (R1) mentioned, the origin can be identified by knowing the materials used or the creation or collection date. CIDOC-CRM allows an object- and event-centric approach to co-exist by connecting instances directly to an object and also without an intermediary event. The domain experts call for representations of objects’ inventory number, title, category or classification, material, collection and origin. Additionally, they request the possibility of attaching comments and descriptive notes.

Based on the participants’ requirement of object description, this research reuses the specification mentioned for the function to express object collection information by CIDOC-CRM guideline⁸, with adjustments based on use-case requirements. The collection object itself is an instance of E24 Physical Human-Made Thing⁹, with the following properties (and object classes).

- Inventory Id & Title: P1 is identified by (E41 Linguistic Appellation & E42 Identifier)
- Object classification: P2 has type (E55 Type)
- Textual Description: P3 has note (Literal)
- Related Person or Organization: P49 has former or current keeper, P52 has current owner (E39 Actor)
- Object Dimension: P43 has dimension (E54 Dimension)
- Material: P45 consists of (E57 Material)
- Represented Visual Concept: P65 shows visual item (E36 Visual Item)
- Image: P138i has representation (IRI)
- Collective Name/ Group: P67i is referred to by (E33 Linguistic Object)

Additional object information is best represented through events, i.e., E7 Activity, E8 Acquisition, E12 Production or E10 Transfer of Custody. Therefore, such information is connected with representative activities that are themselves connected to the artefact. For example, P14 carried out by, P7 took place at, and P4 has time-span are properties of the E12 Production event, where the object connects this activity with property P108i was produced by. On the other hand, properties such as P28 custody surrendered by, P29 custody received by, and P30 transferred custody of are not mentioned due to the complexity of such information and are modelled as part of provenance information.

### 4.2. Provenance Information

In addition to representing basic object information, the domain experts desired representations of detailed provenance information with known actors, locations and events. An object’s provenance can be seen as a series of events where the custody of an object is transferred between different actors during time and places. The provenance of an object is mainly represented using two different entities in CIDOC-CRM. E8 Acquisition comprises the transfer of legal ownership from one or more instances of E39 Actor to another. In contrast, E8 Acquisition refers to legal ownership, thus the view that the change of owners is interpreted as a legal right, for example, object is purchased.

Common to all six objects considered here, there is at least one transfer of custody in their biography that is not seen as a legal right, namely when it was looted during the military campaign, purchased from illegal authority or receiving questionable gift. Therefore, using E8 Acquisition for modelling unethical ways of acquisition where the legal right is questioned may not be an appropriate. CIDOC-CRM separates legal ownership and physical custody. E10 Transfer of custody can be used to represent non-legal ways of acquisition, where a specific type of acquisition, such as theft, loot or gift, can be declared.

For the current modelling choice of selected objects, we used E10 Transfer of Custody to represent any illegal transfer of ownership and E8 Acquisition for legal cases. Any such activity (both E8 and E10) can further contain other activity(-ies) as the sub-activity(-ies) falls within the space-time volume of the main activity. This sub-activity is assertions made in a graph by the information providers [22]. In this case, a provenance researcher can identify a single source of knowledge containing various statements. It is up to information consumers to decide whether or not they can trust the information provider and how reliable the information is.

**PROV-DM** [28] is a conceptual model for modelling provenance, with PROV-O being a mapping to RDF^12 with proven applicability in the cultural heritage domain [21,29]. In our model it is used for attaching data provenance to a named graph URI. A typical use case for PROV-DM is to achieve data quality, traceability and trustworthiness. The **Entity**, **Activity** and **Agent** classes are the building blocks for the model. According to the model, any physical, digital or conceptual things can be a **prov:Entity**, where an **prov:Activity** is any action that occurs over a time-period, and **prov:Agent** is any actor who is responsible for the action. Therefore, in our case, the named graph containing all triples from the provenance research is of type **prov:Entity**, the provenance research activity itself is of type **prov:Activity**, and the institution or the person who are involved with this research is a **prov:Agent**. Representing provenance research and derived statements is one example of how we modelled different statements generated from different resources and activities. In Figure 2, the named graph ex:story#1 includes all data triples associated with object RV-2584-169a, which were generated during the research activity ex:provenance_research#2. This activity is an instance of **prov:Activity** in accordance with the PROV-DM ontology, enabling data provenance tracing for the generated triples.

^12 https://www.w3.org/TR/prov-o/

### 4.4. Polyvocal Modelling

Data provenance modelling and named graphs can be used to group (CIDOC-CRM) triples that conform to a particular view of acquisition and distinguish them from other statements that conform to another view. Figure 2 shows how named graphs separate different (CIDOC-CRM) triples representing specific views of acquisition and how data provenance of such named graphs is specified using the PROV-DM ontology. When querying for a particular object provenance with SPARQL 1.1, triples stating object provenance can be returned without making any distinction in acquisition theory. By using the GRAPH keyword, information from only specified (provenance) graphs can be returned. This allows attaching a source, location and/or time period to that view and responsible agents/sources for a group of statements. Each named graph or triple collection is represented as a **prov:Entity**, typically derived from (*prov:wasDerivedFrom*) another **prov:Entity** (i.e., source) or generated by (*prov:wasGeneratedBy*) a **prov:Activity** (i.e., a domain research activity).

## 5. Results and Validation

This section reflects on the RDF triples generated from converting object provenance reports using the proposed model. Six objects were initially used for modeling decisions, and five more were randomly selected from the Pilotproject Provenance Research on Objects of the Colonial Era (PPROCE)^13 project to test the model’s generalizability. The re-

^13 https://www.niod.nl/en/projects/pilotproject-provenance-research-objects-colonial-era-pproce
