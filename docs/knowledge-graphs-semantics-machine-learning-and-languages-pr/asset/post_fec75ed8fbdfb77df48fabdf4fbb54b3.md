
- [6] Nentwig M, Hartung M, Ngonga Ngomo AC, Rahm E. A survey of current link discovery frameworks. Semantic Web. 2018;8(3):419-36.

- [7] Euzenat J, Meilicke C, Stuckenschmidt H, Shvaiko P, Trojahn C. Ontology alignment evaluation initiative: Six years of experience. In: Journal on data semantics XV. Springer; 2011. p. 158-92.

- [8] Algergawy A, Faria D, Ferrara A, Fundulaki I, Harrow I, Hertling S, et al., editors. Results of the ontology alignment evaluation initiative 2019. vol. 2536; 2019.

- [9] Abd Nikoor P, Algergawy A, Amini R, Faria D, Fundulaki I, Harrow I, et al., editors. Results of the ontology alignment evaluation initiative 2020. vol. 2788. RWTH; 2020.

- [10] Pour M, Algergawy A, Amardeilh F, Amini R, Fallatah O, Faria D, et al., editors. Results of the ontology alignment evaluation initiative 2021. vol. 3063. CEUR; 2021.

- [11] Todorov K, editors. First! A Bottom-up Data Linking Paradigm; 2019.

- [12] Euzenat J. Extraction de clés de liage de données (résumé étendu). In: 16e conférence internationale francophone sur extraction et gestion des connaissances (EGC). Hermann; 2016. p. 9-12.

- [13] Atencia M, David J, Scharffe F, editors. Keys and Pseudo-Keys Detection for Web Datasets Cleansing and Interlinking. Springer; 2012.

- [14] Symeonidou D, Armant V, Pernelle N, Saïs F, editors. Sakey: Scalable almost key discovery in RDF data. Springer; 2014.

- [15] Symeonidou D, Armant V, Pernelle N. BECKEY: Understanding, comparing and discovering keys of different semantics in knowledge bases. Knowledge-Based Systems. 2020;195:105708.

- [16] Babic B, Nesic N, Miljkovic Z. A review of automated feature recognition with rule-based pattern recognition. Computers in industry. 2008;59(4):321-37.

- [17] Käfer T, Harth A. Rule-based Programming of User Agents for Linked Data. LDOW@ WWW. 2018;2073.

- [18] Wang Q, Mao Z, Wang B, Guo L. Knowledge graph embedding: A survey of approaches and applications. IEEE Transactions on Knowledge and Data Engineering. 2017;29(12):2724-43.

- [19] Dai Y, Wang S, Xiong NN, Guo W. A survey on knowledge graph embedding: Approaches, applications and benchmarks. Electronics. 2020;9(5):750.

- [20] Harispe S, Ranwez S, Janaqi S, Montmain J. Semantic similarity from natural language and ontology analysis. Synthesis Lectures on Human Language Technologies. 2015;8(1):1-254.

- [21] Klein M, editor. Combining and relating ontologies: An analysis of problems and solutions; 2001.

- [22] Bergman M. Sources and classification of semantic heterogeneities. Web Blog: AI3-Adaptive Information, Adaptive Innovation, Adaptive Infrastructure. 2006.

- [23] Plempitiwiriway C, Hammer M. A classification scheme for semantic and schematic heterogeneities in XML data sources. TR00-004, University of Florida, Gainesville, FL. 2000.

- [24] Euzenat J, Shvaiko P. Ontology matching. vol. 18. Springer; 2007.

- [25] Achichi M, Bellahsene Z, Ellefi MB, Todorov K. Linking and disambiguating entities across heterogeneous RDF graphs. Journal of Web Semantics. 2019;55:108-21.

- [26] Assi A, Mcheick H, Dhifli W. Data linking over RDF knowledge graphs A survey. Concurrency and Computation: Practice and Experience. 2020;32(19):e5746.

- [27] Lebo T, Sahoo S, McGuinness D, Belhajjame K, Cheney J, Corsar D, et al. Prov-o: The prov ontology. W3C recommendation. 2013;30.

- [28] Albertoni R, Browning D, Cox S, Beltran AG, Perego A, Winstanley P. Data catalog vocabulary (DCAT)-version 2. World Wide Web Consortium. 2020.

- [29] D’Arco B, Giasson F. Bibliographic ontology specification. Madrid: Biblioteca Nacional Española. 2009.

Implementation of new obligations on the entities processing personal data, the European Commission published a document establishing its *strategy for data*, including a package of new regulation proposals to legislate the usage of non-personal and public data, the activity of digital services and digital markets and the development of *common European data spaces* [2]. While putting the data in the centre of this transformation, by making it available to all and facilitating its flow between sectors, the interests of data subjects and data holders will be kept by having clear data-sharing policies to govern the usage and access to data and trusted entities that enable said sharing while enforcing compliance with the new regulations.

In particular, the Regulation of the European Parliament and of the Council on European data governance, the Data Governance Act (DGA), was proposed to improve the availability of public data, promote trust in data intermediation service providers and data altruism organisations as enablers of data-sharing between data holders and data users for purposes of general interest, and to establish a new supra-national authority charged with overseeing the activities of such entities, the European Data Innovation Board [3]. The DGA, along with the proposed visions for an European Health Data Space [4] and the Data Act [5], put an emphasis on the altruistic reuse of data – in the Health Data Spaces case to address the challenges of access and sharing to electronic health data – currently trapped within various institutions in the EU and unavailable to be used by all. The key challenges to be addressed to realise these visions are related to the:

- Ch1. *Availability / Discovery of datasets*: without the promotion and technical support for the development of common data spaces and trusted data sharing entities, data subjects and data holders will not have automated tools to share their data to be reused for common good purposes, nor solutions to support them in the exercising of their rights, and data users will not have tools to search for the data they seek.

- Ch2. *Establishment of conditions for usage and access to data*: without standards and metadata vocabularies to express interoperable, machine-readable policies, the establishment of conditions for usage and access to personal, non-personal and public-sector data, based not only on legal but also on ethical, organisational and social norms, will provoke interoperability issues between entities providing and seeking access to data.

- Ch3. *Production of Documentation*: without keeping records of their activities in a structured format, data intermediation service providers and data altruism organisations will rely on manual processes to produce documentation that demonstrates their accountable and responsible practices.

Therefore, Semantic Web vocabularies, such as the W3C’s Data Privacy Vocabulary (DPV)¹, Open Digital Rights Language (ODRL)² or Data Catalog Vocabulary (DCAT)³, have an important role to play in these processes as they are interoperable and form common standards that enable machine-readable tools to be used for the automation of tasks. DCAT and ODRL are W3C Recommendations to describe data catalogues published on the Web and to express usage rules

¹ https://w3id.org/dpv
² https://www.w3.org/TR/odrl-model/, https://www.w3.org/TR/odrl-vocab/
³ https://www.w3.org/TR/vocab-dcat-2/

over digital datasets, respectively. DPV is a W3C Community Group Report, which has recently published a stable version 1, aimed at providing a complete, open-access set of taxonomies to express machine-readable metadata about the use and processing of personal data, such as taxonomies for legal entities, purposes, types of processing activities, legal basis, types of data, rights or technical and organisational measures. By combining the usage of these standards and specifications to automate the discovery of datasets (Ch1), specify policies for the reuse and sharing of data (Ch2), and comply with legal obligations (Ch3), such as sending notifications to the competent authorities under the DGA, this work will enable organisations to gradually move from completely manual processes to ones based on utilising automation and technologies to assist in ensuring correctness and scalable architectures on the data-sharing services ecosystem.

In order to address the identified challenges, we determined what reuse conditions are necessary to specify *how* to share data, *who* are the new involved stakeholders, and *what* documents are required to comply with the new law. Therefore, the following research objectives are presented as the basis of this work:

- RO1. Identify the stakeholders, information items and information flows relevant for the sharing of data compliant with the DGA.

- RO2. Identify terms missing from W3C’s specifications for representing data-sharing policies and consent terms.

- RO3. Generate registers of altruistic and data intermediary activities which can be queried by the competent authorities.

Moreover, the principal contributions of this paper are summarised as follows:

- C1. Identification of DGA entities and how data flows between them.

- C2. Identification of Use Cases where the usage of semantic vocabularies will assist in the automation of tasks.

- C3. Development of ad-hoc vocabulary for representing data-sharing policies, consent and permission terms and registries of activities.

- C4. Demonstration of representation of DGA-related information using the mentioned semantic web technologies and the developed vocabulary.

This paper is organized as follows: Section 2 describes the entities and flows of data between entities defined by the DGA in which the usage of semantic technologies can promote the automation of tasks, while Section 3 discusses the state of the art in semantic models for data governance. Section 4 provides an identification of vocabulary terms that can be reused for the purposes of providing examples for policies for the reuse and sharing of data, querying registries of activities and specifying data altruism form terms. Section 5 discusses the impact of our approach on compliance with DGA and its limitations and the last section presents conclusions and future lines of work.

## 2. Information Flows in the DGA

As the DGA promotes the availability and regulates the sharing of data, a set of information flows, related to the information that needs to be exchanged between
