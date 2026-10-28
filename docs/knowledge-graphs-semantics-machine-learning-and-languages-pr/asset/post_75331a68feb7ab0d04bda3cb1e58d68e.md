
- [21] Minsky M. A framework for representing knowledge. MIT, Cambridge, 1974.
- [22] Bakker F, Breteler J, van Gessel T, van Engers T, van Doesburg R. A Norm Engine Based on Semantic Web-Compliant Technology; 2023. Presented at AI4Legs 2023: AI for Legislation.
- [23] Fischer MJ, Ladner RE. Propositional modal logic of programs. In: Proceedings of the ninth annual ACM symposium on theory of computing; 1977. p. 286-94.
- [24] Bakker RM, van Drie RAN, de Boer MHT, van Doesburg R, van Engers T. Semantic Role Labelling for Dutch Law Texts. In: Proceedings of the Thirteenth Language Resources and Evaluation Conference; 2022. p. 448-57.
- [25] Bakker RM, de Boer MHT, van Drie RAN, Vos D. Extracting Structured Knowledge from Dutch Legal Texts: A Rule-based Approach. In: Companion Proceedings of the 23rd International Conference on Knowledge Engineering and Knowledge Management; 2022. p. 1-10.
- [26] van Drie RAN, Bakker RM, de Boer MHT, Tolios I, Vos D. The Dutch law as a semantic role labeling dataset. In: Nineteenth International Conference on Artificial Intelligence and the Law (ICAIL); 2023. p. 316-22.
- [27] Westhofen L, Stierand I, Becker JS, Möhlmann E, Hagemann W. Towards a Congruent Interpretation of Traffic Rules for Automated Driving: Experiences and Challenges. In: Proceedings of the International Workshop on Methodologies for Translating Legal Norms into Formal Representations (LN2FR 2022) in association with the 35th International Conference on Legal Knowledge and Information Systems (JURIX 2022); 2022. p. 8-21.

## Semantifying the PlanQK Platform and Ecosystem for Quantum Applications

Darya MARTYNIUK a, Naouel KARAM a, Michael FALKENTHAL b, Yufan DONG a and Adrian PASCHKE a,c

a Data Analytics Center DANA, Fraunhofer FOKUS, Berlin, Germany
b Anaqor AG, Berlin, Germany
c Institute for Computer Science, Freie Universität Berlin, Germany

Abstract. Quantum computing is currently experiencing rapid progress. Due to the complexity and continuous growth of knowledge in this field, it is essential to store information in a way that allows an easy access, analysis and navigation over reliable resources. Knowledge graphs (KGs) with machine-readable semantics offer a structural information representation and can enhance the capabilities of knowledge processing and information retrieval. In this paper, we extend the platform and ecosystem for quantum applications (PlanQK) for a KG. Specifically, we describe how the quantum computing knowledge, which is submitted on the platform by researchers and industry actors, is incorporated into the graph. Moreover, we outline the semantic search over the PlanQK KG.

Keywords. Knowledge Graph, Ontology, Semantic Web, Semantic Search, Faceted Search, Ontology-based Search, Quantum Computing

### 1. Introduction

Quantum computing has experienced notable growth in recent years leading to a corresponding increase of knowledge in this field. Access to a wide spectrum of scientific and business information, including publications, programming code, software, and hardware documentations is without doubt highly beneficial for further research and development of new technologies. However, it also means that finding relevant knowledge in quantum computing related sources has become an increasingly tedious and time-consuming task even when employing search engines. Knowledge graphs (KGs) have grasped significant potential for enhancing capabilities of search systems, facilitating more efficient information retrieval (IR) [1]. Representing data as a graph allows to define formal semantics and improves flexibility for integrating data from heterogeneous sources [1], [2].

In this paper, we introduce an approach for organizing and curating the information available on PlanQK¹ - a collaborative platform and an ecosystem centered on quantum-enhanced applications - in form of a knowledge graph. The mission of PlanQK is to make the research and industrial knowledge about quantum software and solutions easily accessible as well as to offer the capability to deploy, host, execute and monetize quantum services. We present a pipeline for a continuous semantification of the data submitted by user. Furthermore, we outline native semantic search and faceted semantic search, which leverage indexed parts of the PlanQK KG to improve the retrieval of relevant information.

This paper is structured as follows. In Section 2, we briefly introduce the PlanQK KG along with the underlying ontology and provide an overview of the semantification process of the platform data, i.e., its integration into the graph. In Section 3, we describe the realization of KG-based semantic search and semantic faceted search. We give an outlook on future work and a conclusion in Section 4.

![](img/5368dd329bd72fa0bf97ac91d6cef632_251_0.png)

**Figure 1.** Core knowledge artifacts of the PlanQK ontology.

### 2. PlanQK Knowledge Graph

PlanQK KG provides a structured machine-interpretable representation of the platform knowledge by organizing information into named nodes and directed edges that represent specific relations between these nodes². Following the Resource Description Framework (RDF)³ standard, each node and property is identified by a Uniform Resource Identifier (URI). To query the graph, we utilize SPARQL [3] query language, which is widely used in Semantic Web applications.

The *PlanQK Ontology* [4] serves as a formal schema of the PlanQK KG by defining selected computing concepts and relations between them in the context of the PlanQK platform. The ontology is publicly accessible to the research community including documentation and usage examples⁴. During the creation of the PlanQK ontology, we reviewed existing vocabularies that already encompass definitions of relevant concepts and reused certain ontologies, e.g., ML Schema [5], Subject Resource Application Ontology (SRAO) [6], and Software Package Data Exchange (SPDX) License List [7]. Figure 1 shows the core concepts of the PlanQK ontology, i.e., algorithms, implementations, use cases, data pools and services. Still the primary focus of the semantic annotations in PlanQK lies in describing quantum-related information, it nevertheless encompasses also knowledge related to the classical computing. The reason for this is twofold: Firstly, quantum concepts are often related to classical, e.g., quantum algorithms can be inspired by the idea of their classical counterparts, and, secondly, due to several limitations of the quantum devices in the Noisy Intermediate-Scale Quantum (NISQ) [8] era, quantum-enhanced applications are currently mostly developed in a hybrid manner, i.e., contains both quantum and classical parts [9], [10].

![](img/5368dd329bd72fa0bf97ac91d6cef632_252_0.png)

Figure 2. Overview of the platform data integration into the knowledge graph.

The semantification process of the PlanQK platform is depicted on Figure 2. The frontend of the platform allows users to create, modify and delete knowledge. For example, an user can create a new entry that describes an algorithm with a specific name and computation design, i.e., quantum, classical, or hybrid. The user can further modify the entry by filling various textual attributes, e.g., acronym, intent, and solution, and select annotations from the controlled vocabulary, e.g., problem class and application area. Once the data is submitted, the backend of the platform manages the information insertion into the relational database⁵ and triggers a request to a cloud messaging service, which publishes the message regarding the data changes to the particular channel. To receive notifications from the channel, the knowledge service requires an active subscription. If this is the case, the service obtains a message in the JSON format. The conversion of new data from JSON into RDF is facilitated by Karma [11] integration tool. Karma provides a semi-automatic approach to define a mapping model between

⁵ In the context of the PlanQK platform, the decision to use both a relational database and a knowledge graph for data storage is driven by considerations of security and component decoupling. In addition to the explicit content of the platform, the relational database contains the information about user rights. The decoupling of data storage is beneficial to facilitate the future expansion of the knowledge service for an ecosystem of similar platforms.
