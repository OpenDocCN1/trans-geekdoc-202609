
Figure 10.1 illustrates the exchange of tokens between actors when exchanging evidence. For example, the path between vertexes 3 and 1 is directed and shows a flow of 10 tokens. Figure 10.1 indicates that there is a possibility of uneven token distribution. The distribution and issuance of tokens would have to be governed and completed by a central authority. This could lead to operational issues, e.g., the inability to submit evidence due to a token deficit. The issuance of tokens is also problematic and might have to be resolved by organisational restructuring, e.g., all Forensic Scientists might have to spend a day collecting tokens as a Custodian in the evidence store. It may seem possible to incorporate such measures into a BoC system, but these measures may be disagreeable to organisations in which the role of the user is less inter-disciplinary or in high demand.

Due to the problems outlined above, tokens will not be used in BoC. BoC is a not-for-profit permissioned blockchain application to assist in the recording of artefacts at investigations. Blockchain has a formula for cost, where `(Value created by blockchain – network operation costs > 0)` (Gaur *et al*., 2018 (Chapter 10)). However, when not-for-profit or public funds are used to cover costs the need and value of tokens diminish. When designing a blockchain application the need for tokens has to be considered and the important factors that play a role in this decision are as follows:

1. value of the token — is there any real value to the token;
2. purpose/funding of blockchain application — is the blockchain funded by the value of the tokens;
3. token issuance — how are tokens redistributed across all actors in the network;
4. uneven token distribution — does a particular type of user tend to accumulate tokens; and
5. organisational restructure — is organisational restructure required to redistribute your tokens.

### 10.3.7 Hyperledger

Participants, assets, transactions and events are the main components in a business network (Gaur *et al*., 2018 (Chapter 6)). These components can be described as follows:

**Participants:** Participants are the actors playing various roles in the business network, e.g., in BoC the actors are investigators, custodians, etc. These roles need defining and Use Case Diagrams are particularly important for identifying the participants. As pointed out in Chapter 6 of Gaur *et al*. (2018) there are three types of participants: individual, organisational and system.

**Assets:** Assets are the items of value to the network that are securely exchanged and recorded between participants. These assets need to be kept confidential, protected and secure. Much like data structures in databases, assets have properties and relationships, e.g., the ownership of an asset is a property of the asset.

**Transactions:** Transaction records change. Essentially, this is the asset lifecycle and the changing of properties, relationships and ownership are recorded and updated on the blockchain. In addition, the user that made the transaction is recorded, along with the timestamp when the transaction was made and finally, a unique hash code.

**Events:** Events represent a transition in the business network, e.g., when an artefact reaches a certain location.

## 10.4 Design

The design and development of blockchain applications is in its embryonic stages. There is no standard approach and it is proposed that using a modelling technique based on UML will help to provide a structured approach during design. The following sections explain the proposal and are centred around four aspects of blockchain: user modelling (Section 10.4.1), data modelling (Section 10.4.2), access control (Section 10.4.3) and operational logic (Section 10.4.4).

### 10.4.1 User modelling

The use case diagram in `Fig. 10.2` identifies the roles of individuals and key processes required for the operation of a chain of custody, which is an important aspect of Access Control (as explained in `Section 10.4.3`). The actors in the use case are generic and include a wide range of people in different organisations, e.g. Expert Witnesses are not included as a specific role, but can be accommodated in either Third Parties or Specialists. The issue here is that the attributes, which would be processed at run-time, allow a specific role certain access. The transactions carried out in the use cases have a direct relation to the transactions required in the blockchain, with the exception of Audit. In summary, the use case diagram helps a designer identify actors and transactions to add to the system.

![image](img/fig10.2.jpg)

**Fig. 10.2.** Use case diagram for BoC. Internal actors on right, external actors on left.

`Fig. 10.2` identifies five key use cases required: ‘Add new Investigation’; ‘Add new FRT member’; ‘Seizure’; ‘Exchange’; and, ‘Audit’. With the exception of ‘Audit’, each of these use cases requires a bespoke transaction and a flowchart detailing the sequence of events. ‘Audit’ is an exception, since it is querying the process and merely monitoring the blockchain, and since this is something that Hyperledger already provides. Of course, this is only a prototype. Future modifications may require updates to the blockchain when auditors view data, thus enabling an audit on the auditors.

### 10.4.2 Data modelling

`Fig. 10.3` illustrates the data requirements for this system. The class diagram does not include data attributes or methods since they are stored separately, the former on the blockchain and the latter in the system. It simply outlines the components required for the system and their relationships. Of particular importance is the generalised inheritence of the class `Person`, which has relationships with the classes `Custody` and `Case` (later defined as `Investigation`). The classes highlighted as external are entities outside the organisation; however, they are not external to BoC. The purpose of highlighting them as external is to demonstrate the exploitation of vendor-neutral representations with blockchain technology. Whilst each external organisation may have a different Management Information System, blockchain technology supplies a reliable, irrefutable and secure communication between any two organisations. This would be a significant challenge in system development and technology infrastructure. In summary, the classes identify the differences between assets, participants, transactions and information stored on the blockchain.

![image](img/fig10.3.jpg)

**Fig. 10.3.** Class diagram for BoC. The system includes external classes, which are accredited organisations that will have access to the permissioned blockchain. However, they have limited access. Access is controlled by an access policy at a policy enforcement point.

### 10.4.3 Access control

Access control provides participants with secure and authorised access to assets. During the embryonic development of access control, Role-Based Access Control (RBAC) (Ferraiolo *et al*., 2001) played an important part in authorising groups of users. Over time, these groups of users became dynamic and included attributes that informed authorisation. For example, a user may only be authorised whilst at work, or, whilst they have been delegated a task by a manager. Typically, more roles were added, which eventually led to a role explosion and complexity (Kuhn *et al*., 2010).
