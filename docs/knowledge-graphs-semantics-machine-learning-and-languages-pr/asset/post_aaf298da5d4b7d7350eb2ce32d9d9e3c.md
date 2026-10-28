
data-sharing entities can be described. In this context, an information flow specifies the information that has to be transmitted from one entity to another or that needs to be kept in a document, such as a record of activity or a public register, to fulfil a certain DGA requirement. Figure 1 displays a diagram of the identified entities and information flows.

![](img/5368dd329bd72fa0bf97ac91d6cef632_228_0.png)

Figure 1. Flows of information between DGA-specified stakeholders. The concepts surrounded by a black box represent (legal) entities and the ones surrounded by an orange box represent newly introduced documents, to be created and maintained by the identified entities. The direction of the arrows represents the direction of the information flow between entities. A simple description of each information flow is provided on the right side of the Figure.

The identified entities can be classified as a data holder, data subject, data user, data intermediation service provider – or data intermediary –, data altruism organisation, legal representative, national or competent authority, single information point provider, public sector body, or competent body. Information flows including the soon-to-be-created European Data Innovation Board and European Commission are also displayed in Figure 1. Their definitions are presented below:

- **Data Subject** Individual whose personal data is being processed
- **Data Holder** An entity who has the right to grant access to or to share certain personal data or non-personal data
- **Data User** An entity who has the right to use personal or non-personal data for commercial or non-commercial purposes
- **Data Intermediation Service Provider** An entity who establishes commercial relationships for the data sharing between data subjects and data holders on the one hand and data users on the other
- **Data Altruism Organisation** A non-profit organisation that collects and shares data for altruistic purposes
- **Public Sector Body** An entity or association of entities governed by public law formed by one or more State, regional or local authorities
- **Legal Representative** A representative of a legal entity designated to act on behalf of a data intermediation service provider or altruism organisation
- **Competent Body** An entity designated by a public sector body to provide legal and technical support on the access and reuse of public sector data
- **Single Information Point Provider** An entity who is responsible for receiving and transmitting requests for the re-use of public data
- **Competent Authorities** Authorities in charge of supervising the activity of data intermediation service providers and data altruism organisations and maintaining a public register of said entities
- **European Data Innovation Board** An authority tasked with overseeing the activities of data intermediaries and data altruism organisations

For instance, the data intermediary shares the conditions for data access under an open or commercial licence with the data user (flow represented in Figure 1 with a red arrow) and keeps a record of its activities (flow represented in Figure 1 with the (K) arrow). This diagram is derived from an analysis of Chapters II (‘Re-use of certain categories of protected data held by public sector bodies’), III (‘Requirements applicable to data intermediation services’), IV (‘Data altruism’) and VI (‘European Data Innovation Board’) of the DGA. Each article in these chapters was manually studied to search for interactions between the identified entities and, when a flow of information was identified between more than one entity, the respective interaction was recorded in the diagram. In addition, requirements related to the production of compliance documentation are also recorded in the diagram as they require the recording of information which can be automated with the usage of semantic technologies.

In the next three subsections, we focus on the information flows related to the conditions for the re-use of public data (subsection 2.1), with keeping registers of altruistic and intermediary activities (subsection 2.2), and with data altruism activities (subsection 2.3), where the usage of semantic technologies can best assist the involved entities in automating their flow-related tasks. For each example use case, a methodical study of the involved information flows, and respective items of information that need to be exchanged, was manually performed for each identified flow and systematised in the following subsections.

## 2.1. Use Case U1: Conditions for the Reuse of Public Data

DGA’s Chapter II is dedicated to the ‘Re-use of certain categories of protected data held by public sector bodies’, including the specification of what categories of data it refers to (Article 3), the information conditions that public sector bodies need to document in order to provide such services (Article 5 and 6) and the description of single information point providers and how they are used by data users to search for and request datasets for re-use (Article 8 and 9). The information that public sector bodies need to provide, and a list of the DGA’s source articles where it is mentioned, is available in Table 1. This information, which can be specified with the assistance of a competent body (as represented by the (A) arrow in Figure 1), needs to be shared with the single information point provider (as represented by the (B) arrow in Figure 1), so that data users can search datasets ((C) arrow) and send a request for re-use of data through the single information point ((D) arrow). Single information point providers must also maintain and make available a data asset list (represented by the (V) arrow), including information on available resources and the conditions for their re-use.

### Table 1. Information items about public sector bodies' services.

| Article | Information items |
|---|---|
| 2.9 | Data user/categories of users |
| 5.1 | Public sector body information |
| 5.1 | Competent body information |
| 5.2 | Categories of data |
| 5.2 | Purposes for usage and access |
| 5.2, 5.3(a) | Nature of data |
| 5.3(b), 5.3(c) | Processing environment |
| 5.5 | Measures to prevent re-identification of data holders/subjects |
| 5.9 | Third party recipients |
| 6.2 | Fees |
| 8.2 | Data format |
| 8.2 | Data size |
| 9 | Procedure to request reuse |

## 2.2. Use Case U2: Registers of Altruistic and Intermediation Activities

DGA’s Chapter III and IV is dedicated to the requirements applicable to entities who wish to provide data intermediation or data altruism services. As for the former, and as is defined in DGA’s Article 11, the entities who wish to provide data intermediation as a service need to notify their competent national authority of said intentions (as represented by the (F) arrow in Figure 1), which in turn must publish and maintain an updated public register of intermediaries (as represented by the (J) arrow). The conditions required to perform such service are depicted in Article 12, such as the requirement to appoint a legal representative if the data intermediation entity is not established in the EU (as represented by the (G) arrow), to provide information about the commercial terms of the service, including pricing, date and time of the creation of the data and its geolocation, the format of the data and which formats it can be converted, and about the tools and measures used by the intermediary to facilitate the exchange of data, to protect and ensure its interoperability, and to ease the exercising of data holders and data subjects’ rights, including the tools to obtain and withdraw permissions and consent, respectively. In addition to these conditions, the data intermediation service provider must also keep a log record of its activities (as represented by the (K) arrow), which in addition to the previously mentioned conditions, must also contain the entity-related information which is made available in the public register of intermediation providers, including name, public website, legal status,
