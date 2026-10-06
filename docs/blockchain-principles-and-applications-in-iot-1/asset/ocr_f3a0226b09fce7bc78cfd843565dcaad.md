# Access Control and Data Security

Another model proposed in [59]P41 involves the usage of multiple blockchain structures for the following purposes:

+   * Storage of public credentials and relationships between entities (Relationships)
* Contextual data obtained from sensors (Contextual)
* History of permissions and denies for auditing (Accountability)
* Access control policies defined by the owners (Rules)

The novelty introduced in this paper involves defining relationships between devices or any other entities. Attributes and characteristics could be assigned to a pair of devices and could be used in the access control policy. The paper also suggests storing information judged to be important in limited power devices, such as only rules associated with the device. Another option would be find another device with sufficient power and define a relationship in the blockchain.

To overcome the limitations of processing in the IoT devices, [60-62]P34 opts for a blockchain-based architecture where the blockchain is stored on the IoT gateway nodes rather than the IoT devices. By including the blockchain on the gateway nodes, the problem of heterogeneity of the devices is also taken care of.
[60]P34 defines a model using multiple smart contracts:

+   * Access control contracts which contain the policy for subject-resource pair
* Judge contract to facilitate dynamic access validation by checking misbehaviour reports and assigning penalties if required
* Register contract that is used to define the two types of contracts

Here, IoT gateways act as agents for their local IoT devices and enforce the access control models for them. The paper introduces the ability to perform dynamic validation that can protect from attacks such as denial of service which can arise from requests to access an unauthorized resource. However one limitation that the paper doesn't solve is that the interactions between the gateway and the IoT devices are assumed to secure. IoT devices can be accessed with a single gateway or sometimes be dynamic and link to any gateway; thus, a mechanism has to be developed to secure these interactions. Additionally, gateways are assumed to be trusted devices managing access control for their local IoT devices.

[63]P1 describes yet another model using blockchain and smart contracts for enforcing access control. However, the policies in this model are stored on the owner's local database while a URL is provided on the blockchain to access this. Any user requesting the resource must load this policy and to a defined smart contract along with his public key for authorization. An advantage of this system is that it is easy for a user to update the policy easily as it is available with them. The model also enables dynamic policy creation whose addresses are stored on a private blockchain and are specific only to users who requested them. However, the access policies defined on the public blockchain are visible to all which is one limitation of this model. Another limitation is that the access policies stored on the users' local database need to be made available at all times for the authorization contract.

[47]P58 uses the blockchain to store only capability tokens in the form of delegation certificates. The proposed method is developed to create an authorization delegation