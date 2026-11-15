

- 5. Privacy
- 6. Rights are preserved
- 7. Inclusion

When Blockchain is applied in healthcare, it is a shared platform that decentralizes data using a high degree of security. Blockchain makes it possible to work with a care passport that contains relevant data. The use of medication can also be monitored via track and trace, which shows the quality of care over a certain period of time. By working with portable devices such as smartwatches, clients can provide real-time information for monitoring and realizing outcomes. Through the secure sharing of data, the quality of care plans is improved, thereby simplifying administrative processes and avoiding unnecessary care deployment.

Here, too, the use of smart contracts creates an audit trail with regard to the various aspects of care deployment. In Chapter 4.1, we mentioned Prescrypt. Prescrypt makes it possible for chronically ill people to get prescriptions that are secured on a Blockchain. This gives the client control over his medication and the accessibility of his information. Clients decide which healthcare professionals they want to share their data with and which pharmacy they want to send their medication overview to. This is illustrated in Figure 21.

Philips Healthcare uses Blockchain technology for welfare apps and client ID programs. Blockchain would make a central intermediary unnecessary under specific conditions, or under other preconditions could be limited to the management of partial databases (Czeschik and Stambolija 2018). Another product based on Blockchain is MyClinic.com. MyClinic makes it easy to make appointments, view medical records and schedule follow-up examinations. The objectives are accessibility and control for the client and simple contact between healthcare professional and client (Medicalchain).

![](img/7aac89a23a631ee44add9e5eff18dfe7_115_0.png)

The blockchain is a technology that enables two unknown parties to transfer a unique piece of digital property, without the need for a central authority - all in a safe, trustworthy and guaranteed way.

Figure 21. Blockchain in healthcare, Radboud UMC REshape Centre.

## Medicaid

Medicaid is a relief program in the United States that provides health insurance for about 74 million individuals and families with low income and wealth. Medicaid is co-financed by the American states and the federal government.

One problem is whether the coverage of care can be continued throughout the year; because the coverage is incomplete, there is no access to the care part of the year. In order to be able to participate, for example, an assessment of the bank's own financial position and a review by the relevant employer are required. This has created a complex bureaucracy in order to arrive at a final verification of the necessary data. This complexity is caused by distributed data files, the right balance between privacy and transparency and the verification requirements. Medicaid is therefore looking at the possibilities of Blockchain to arrive at a different working method.

Medicaid has elaborated this in a study that addresses the five most important changes that can be expected in 2040 (Deloitte 2020):

- Smart medical devices for clients to empower their own health and well-being: these are devices that manage conditions for care interventions via sensors and telehealth. Think also of programmes to promote lifestyle and medication compliance. And the creation of intelligent healthcare communities that focus on data, technology and behavioural interventions to make the central role of clients possible.

- A national database of health data: the data are interoperable between healthcare providers and healthcare professionals and fully accessible to clients. This creates a more holistic approach to clients that avoids inefficiencies.

- Shift from care providers to organizations focused on quality of life: it is increasingly about prevention and self-management of health.

- Personalized behavioural interventions (preventive healthcare): precision engagement connects data, artificial intelligence, algorithms and behavioural expertise to come up with behavioural interventions that are most effective.

- Local care hubs where facilities are brought together: these are centres for prevention, treatment and a more holistic approach to care and quality of life.

## Blockchain for the Electronic Health Record

From the perspective of Blockchain, the design of an Electronic Health Record (ECD) requires the seven process steps (Nichol 2018).

- 1. Receiving a token: a healthcare transaction is received by the Blockchain as a collection of actions recorded in the form of tokens.
- 2. Determining a base block: the last confirmed block is checked, including an identifier for the block used to create a new block.
- 3. Ensuring a peer review: the token is validated (the collection of care transactions, diagnosis and treatment protocols) and sent to peers to review.
- 4. The validation of the block: the digital signature of the validators is added to the block; the block is hashed.
- 5. Token expansion: the initial token is expanded with the validation token to confirm the handling actions.
- 6. Creating a block: based on the validation token, digital signatures, peer reviews and a collection of care tokens, the block is created by miners.
- 7. Sending the block: the combined blocks (collection of care actions) are sent to peers.

![](img/7aac89a23a631ee44add9e5eff18dfe7_117_0.png)

Source: MedRec.
Figure 22. Many mutual contacts.

However, a major problem in healthcare is the lack of interoperability between domains. It turns out to be difficult to unlock and share data. The core of every ECD is that privacy and security are guaranteed. The aim is to provide clients with their own data via an ECD or EHR. The MIT Media Lab has developed the MedRec project for this purpose. Clients have to deal with different healthcare professionals and care providers who also have contacts with each other, as can be seen in Figure 22.

![](img/7aac89a23a631ee44add9e5eff18dfe7_118_0.png)

## Figure 23. The three contracts of MedRec.

Clients (and their informal caregivers) are therefore connected to different care providers. MedRec offers a combination of a social need and a technological solution. The first implementation of MedRec was developed by using Ethereum Blockchain. The system of smart contracts ensures connection between clients and care providers. MedRec does not store the data, but encodes metadata that make it possible for clients to securely access care data in different domains. The metadata contain information about ownership, releasing data and integrity of the data requested. MedRec 2.0 is being tested. Smart contracts are considered agreements to execute a certain code (source of medical information) under certain conditions. MedRec has three types of smart contracts, see also Figure 23.

- The registration contract binds participating parties (clients, care providers, health insurers) to their identity as recorded in Blockchain. Only registered parties can add information.

- The summary contract provides insight into the relationships between the different parties. It provides references to the client care provider contracts: current and past connections to different nodes in the system. The acceptance or deletion of these relationships is determined by the client. Each participant in the system can locate a summary of their relationship with other participants. The acceptance or deletion of contacts is checked by the client.

- The client-care provider relationship contract connects two nodes in the system where one records medical data for the other.

![](img/7aac89a23a631ee44add9e5eff18dfe7_119_0.png)

Source: MedRec.

Figure 24. From request for access to the message from the healthcare professional.

MedRec works within a private Blockchain: a private peer-to-peer network of reliable, validated nodes. In order to limit risks related to privacy, the following approach is being worked on. A care provider submits a request for access to the care provider. The Electronic Health Manager ensures an update via the database and MedRec. The Blockchain creates a summary contract and identifies the patient. After completing the entire process, the patient receives a message from the healthcare professional, as can be seen in Figure 24.

### Realizing a Good Transfer

Developments in recent years, such as the Landelijk Schakelpunt (‘National Exchange Point’), have mainly focused on curative care. Connections with long-term care providers and the social domain remain complicated. For example, general practitioners still indicate that electronic information exchange with home care, district nursing care, nursing homes and social support is almost impossible in a standardised manner, although they would like to do so.

Although data is increasingly recorded digitally, nurses and caregivers are still unable to make sufficient use of the benefits of digital recording. Data are stored in separate systems and are also not unambiguous. As a result, there is no exchange between systems

