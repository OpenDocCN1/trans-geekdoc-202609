
Imagine a document requiring multiple signatures for approval. In Fabric, transactions are endorsed by peer nodes, indicating their validity. These endorsements are collected and validated by peers, ensuring that only valid transactions are added to the ledger. This endorsement policy adds an extra layer of trust to the network, as shown in Figure 5.5:

![](images/Figure_5.5.jpg)

## Modular and pluggable design

Hyperledger Fabric’s architecture is modular and pluggable, much like building blocks. This design allows organizations to tailor the network to their specific needs, integrating custom features and components. It promotes flexibility and extensibility.

## Real-world applications

Consider a global supply chain consortium aiming to enhance transparency and traceability. Hyperledger Fabric’s architecture allows the consortium to create a custom network with multiple channels, ensuring that each participant can access only the relevant data. Smart contracts automate supply chain processes, and the ledger maintains an immutable record of all transactions, bolstering trust among participants.

Hyperledger Fabric’s architecture is like a well-orchestrated symphony, where each component plays a crucial role in creating a reliable and flexible blockchain network. Its modular design, channels for privacy, and support for various consensus mechanisms make it a versatile choice for a wide range of enterprise applications.

## Components of Hyperledger Fabric

In this module, we embark on a journey to dissect the intricate architecture of Hyperledger Fabric. Like a skilled anatomist exploring the human body, we shall explore the various components that make up this robust blockchain framework. Hyperledger Fabric, much like a well-orchestrated symphony, comprises several key components that work harmoniously to enable the creation of secure, scalable, and flexible blockchain networks.

### Peer nodes: The workhorses of the network

Peer nodes are the backbone of any Hyperledger Fabric network, serving as the engine that powers the blockchain. These nodes, much like skilled artisans, maintain the ledger, endorse and validate transactions, and execute smart contracts, also known as chaincode. Peer nodes play a pivotal role in ensuring the accuracy and integrity of the blockchain network.

### Ordering service: Orchestrating the transaction flow

The ordering service, analogous to the conductor of an orchestra, is responsible for orchestrating the flow of transactions within the network. The ordering service ensures that transactions are arranged in the correct order and added to the ledger consistently.

### Membership services: The gatekeepers

Membership services act as the gatekeepers of the Hyperledger Fabric network, managing the identities, authentication, and permissions of participants. Picture this as the gatekeeper.

Membership services ensure that only authorized participants can join the network.

### Ledger: Recording the immutable history

The ledger, much like a historical archive, stores an immutable record of all transactions that have occurred on the Hyperledger Fabric network. The ledger stores a comprehensive history of all transactions on the network, providing transparency and immutability. It maintains transparency and data integrity.

### Smart contracts

Smart contracts, also known as chaincode in Hyperledger Fabric, are the logic that governs transactions on the blockchain. Smart contracts enable automation and customization of transactions. They define the rules and logic for transactions.

### Channels for privacy

To ensure privacy in a network, Hyperledger Fabric introduces the concept of channels. Imagine a private conference room within a bustling office. Channels allow for private communication among a subset of network participants. Transactions within a channel are visible only to those who are part of it, ensuring confidentiality.

### Consensus mechanisms

Hyperledger Fabric offers flexibility in choosing a consensus mechanism. Much like different decision-making methods in a boardroom, Fabric supports various consensus algorithms, including PBFT and Raft. Consensus ensures that all network participants agree on the order and validity of transactions.

## MSPs: The guardians of identity

In the intricate Fabric of a Hyperledger network, Membership Service Providers (MSPs) emerge as the guardians of identity and the keepers of trust. In this section, we shall embark on a journey to unravel the significance of MSPs in Hyperledger Fabric and understand their pivotal role in shaping the network’s security and authenticity.

### Role of MSPs

Much like vigilant sentinels, MSPs are responsible for managing the identities of participants within the Hyperledger Fabric network. Their primary roles include:

* Identity verification: MSPs verify the identity of participants by issuing digital certificates. These certificates act as digital passports, allowing individuals and entities to access the network securely.
* Authentication: MSPs ensure that only authorized participants can join the network. They verify the authenticity of certificates during the connection process, safeguarding against unauthorized access.
* Permission management: MSPs control access to the network by defining and enforcing permissions. They determine which participants can perform specific actions, maintaining granular control over network operations.
* Revocation: In the unfortunate event of a security breach or a participant’s departure, MSPs have the power to revoke certificates, immediately denying access to the network.

### MSP configuration in Fabric

Configuring an MSP within Hyperledger Fabric involves defining its structure, roles, and policies. Configuration includes specifying:

* Root CA and intermediate CAs: Identifying the authorities responsible for issuing certificates.
* Admins and endorsers: Designating network participants with administrative privileges and endorsement capabilities.
* Revocation policies: Defining the conditions under which certificates may be revoked.
* Signing policies: Specifying the conditions for approving transactions or changes to the network.

## Chaincode

A following code is a chaincode sample which shows a crud operation for storing car information:

```go
package main

import (
	"encoding/json"
	"github.com/hyperledger/fabric/core/chaincode/shim"
	"github.com/hyperledger/fabric/protos/peer"
	"time"
)

type Car struct {
	ID        string
	Title     string
	Owner     string
	UpdatedAt time.Time
}

type SimpleChaincode struct{}

func (t *SimpleChaincode) Invoke(stub shim.ChaincodeStubInterface) peer.Response {
	f, args := stub.GetFunctionAndParameters()
	switch f {
	case "RegisterCar":
		return t.RegisterCar(stub, args)
	case "GetCar":
		return t.GetCar(stub, args)
	case "ListCars":
		return t.ListCars(stub)
	default:
		return shim.Error("Invalid function name.")
	}
}

func (t *SimpleChaincode) RegisterCar(stub shim.ChaincodeStubInterface, args []string) peer.Response {
	if len(args) != 3 {
		return shim.Error("Incorrect number of arguments. Expecting 3.")
	}
	car := Car{ID: args[0], Title: args[1], Owner: args[2], UpdatedAt: time.Now()}
	carJSON, _ := json.Marshal(car)
	stub.PutState(car.ID, carJSON)
	return shim.Success(nil)
}

func (t *SimpleChaincode) GetCar(stub shim.ChaincodeStubInterface, args []string) peer.Response {
	carJSON, _ := stub.GetState(args[0])
	return shim.Success(carJSON)
}

func (t *SimpleChaincode) ListCars(stub shim.ChaincodeStubInterface) peer.Response {
	resultsIterator, _ := stub.GetStateByPartialCompositeKey("CAR", []string{})
	defer resultsIterator.Close()
	var cars []Car
	for resultsIterator.HasNext() {
		var car Car
```
