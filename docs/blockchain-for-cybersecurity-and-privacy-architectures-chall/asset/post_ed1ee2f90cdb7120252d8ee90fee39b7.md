
# Secure Anti-Counterfeiting Pharmaceuticals Supply Chain System

enable multiple actors to have access to the tokens and perform the certain supply chain processes assigned. Listing 11.1 shows the details of the ownership functions and how they are implemented.

# LISTING 11.1 NFT TOKEN OWNERSHIP FUNCTIONS

```
mapping(uint256 => address) private tokenOwners;
mapping(uint256 => bool) private tokenExists;
// Query Token Ownership
function ownerOf(uint256 _tokenId)
    constant returns (address owner) {
    require(tokenExists[_tokenId]);
    return tokenOwners[_tokenId];
}
// Transfer of token ownership
function transfer(address _to, uint256 _tokenId) {
    address currentOwner = msg.sender;
    address newOwner = _to;
    // Perform assertion before transfer
    require(tokenExists[_tokenId]);
    require(currentOwner == ownerOf(_tokenId));
    require(currentOwner != newOwner);
    require(newOwner != address(0));
    // Perform actions
    removeFromList(_tokenId);
    balances[oldOwner] -= 1;
    tokenOwners[_tokenId] = newOwner;
    balances[newOwner] += 1;
    // Record transfer event in Blockchain for auditing
    Transfer(_oldOwner, newOwner, _tokenId);
}
```

```
// Delegate authority of invoking transfer actions
function approve(address _to, uint256 _tokenId) {
    // Perform assertion before delegating
    require(msg.sender == ownerOf(_tokenId));
    require(msg.sender != _to);
    // Add delegation
    allowed[msg.sender][_to] = _tokenId;
    // Record approve event for auditing and tracing
    Approval(msg.sender, _to, _tokenId);
}
```

## 11.4.1.2 Operations of Composable NFTs

Composable NFTs provide a simple way to form composite assets on the Ethereum blockchain; those assets are still utilizing the same concept of ERC-721 but with the capability to link between parent and child tokens. The targeted use case in this work utilizes composable NFTs in tracing and tracking drugs in the supply chain goods that are either composed or decomposed along the supply chain, for example, a sealable package in a lot or a generic compound origin used in a specific drug.

Composable NFTs, according to the EIP-998, can be formed in the top-down and bottom-up approach. For this scenario, we implement a top-down approach, where the parent token is the lot and the child token is the child, with traceability feature from top-down and bottom-up directions. The need for implementing tracing in both directions is introduced to satisfy different supply chain processes.

To highlight the need for tracing in both directions, we consider two examples. A recall event will usually start by the manufacturer and with the main parameter being the lot number. In this case, the lot number is an identifier for the parent token; thus, the action could result in notifications of owners (distributors/retail/consumers) of affected packages belonging to that lot. On the other side of the chain, a customer querying about a specific package issues the query based on the child token identifier; for transparency, the customer should be able to see the transfer of ownership happening on the lot level to conform adherence to certain policies.

Our proposal to use composable NFTs to perform supply chain procedures according to the FMD and CSDA regulations is simplified in a series of actions that we describe and define hereafter, as the the key requirements for the proper operation of the proposed approach:

- 1. Access to token mining and creation is granted only to the legitimate manufacturers will assume the original ownership of a drug.
- 2. The manufacturer can create tokens in batches.
- 3. The smart contracts are able to generate the required randomness based on identifiers.
- 4. Storage of metadata is done in easily readable and accessible format.
- 5. Capability to perform operations of composition and decomposition on tokens.
- 6. The required events by both regulations enable tracing, tracking, and querying change of ownership and origin shall be recorded on-chain.
- 7. Visibility on information to all stakeholders and capability of invoking queries.

For the first item, bootstrapping the network is assumed to be performed to ensure that only legitimate manufacturers are able to create tokens and therefore ensure the provenance feature and capability to trace drug item change of ownership since the origin. This requirement is necessary to eliminate non-authorized access and combat counterfeiting. The authors assume the role of a system administrator to handle the manufacturers' registration is not within the scope of this work, but the authors envision the use of a blockchain solution based on Decentralized Identifiers (DIDs) [20], in a similar approach to the Verifiable Organization Network (VON) deployed by the Province of British Columbia in Canada to register business entities [21].

The second requirement is to ensure efficient operation and reduce the cost of token creation, while the third to allow portability where metadata is assigned to each token and can be retrieved from the tokenid. the token metadata representing or lot attributes are stored off-chain using off-chain database with possibility to choose a decentralized storage such as IPFS. The fourth and requirement is a mandate in the FMD regulation, and is ensured through the use of a hashing function that digits the metadata provided in addition to a timestamp to generate a random number for each token.

To ensure capability by providing trace and tracking on package and lot level, the proposed composable NFTs require that the smart contract provide two functions that perform the function of compositions and decomposition. The first will construct a composite asset from a model of child tokens to an existing composable NFT and update the.

To highlight the need for tracing in both directions, we consider two examples. A recall event will usually start by the manufacturer and with the main parameter being the lot number. In this case, the lot number is an identifier for the parent token; thus, the action could result in notifications of owners (distributors/retail/consumers) of affected packages belonging to that lot. On the other side of the chain, a customer querying about a specific package issues the query based on the child token identifier; for transparency, the customer should be able to see the transfer of ownership happening on the lot level to conform adherence to certain policies.

Our proposal to use composable NFTs to perform supply chain procedures according to the FMD and CSDA regulations is simplified in a series of actions that we describe and define hereafter, as the the key requirements for the proper operation of the proposed approach:

- 1. Access to token mining and creation is granted only to the legitimate manufacturers will assume the original ownership of a drug.
- 2. The manufacturer can create tokens in batches.
- 3. The smart contracts are able to generate the required randomness based on identifiers.
- 4. Storage of metadata is done in easily readable and accessible format.
- 5. Capability to perform operations of composition and decomposition on tokens.
- 6. The required events by both regulations enable tracing, tracking, and querying change of ownership and origin shall be recorded on-chain.
- 7. Visibility on information to all stakeholders and capability of invoking queries.

For the first item, bootstrapping the network is assumed to be performed to ensure that only legitimate manufacturers are able to create tokens and therefore ensure the provenance feature and capability to trace drug item change of ownership since the origin. This requirement is necessary to eliminate non-authorized access and combat counterfeiting. The authors assume the role of a system administrator to handle the manufacturers' registration is not within the scope of this work, but the authors envision the use of a blockchain solution based on Decentralized Identifiers (DIDs) [20], in a similar approach to the Verifiable Organization Network (VON) deployed by the Province of British Columbia in Canada to register business entities [21].

The second requirement is to ensure efficient operation and reduce the cost of token creation, while the third to allow portability where metadata is assigned to each token and can be retrieved from the tokenid. the token metadata representing or lot attributes are stored off-chain using off-chain database with possibility to choose a decentralized storage such as IPFS. The fourth and requirement is a mandate in the FMD regulation, and is ensured through the use of a hashing function that digits the metadata provided in addition to a timestamp to generate a random number for each token.

To ensure capability by providing trace and tracking on package and lot level, the proposed composable NFTs require that the smart contract provide two functions that perform the function of compositions and decomposition. The first will construct a composite asset from a model of child tokens to an existing composable NFT and update the.

## 11.4.2 Details OF SMART CONTRACT IMPLEMENTATION

This section details the implemented smart contracts that are to fulfill the mentioned requirements. The implementation requires two smart contracts: the first is the manufacturer registrar (MR) and the second is the composable NFT (CNFT).

### 11.4.2.1 MR Smart Contract

The MR smart contract implements the functions for managing the information of manufacturers, including the functions of manufacturers enrollment and manufacturer verification. The current implementation assumes a permissioned ledger, where the existence of an oversight body to act as an administrator is necessary. drug administration is the default actor that can assume the role.

The administrator role requires the validation of the submitted manufacturer information to ensure that the root of the process is intact and boost the trust relationship among all parties. By ensuring a verifiable and validated identity of the manufacturer, the origin of all tokens creation is ensured to be intact and no counterfeiting. The authors do not a fully decentralized approach, since the nature of the application requires authority oversight. However, the authors suggest in case of the existence of a DID and verifiable credential network similar to the VON network, [21], for manufacturers, the MR smart contract can leverage for validating manufacturers' requests.

# Algorithm 1: Manufacturer Smart Contract

```
Input: Manufacturer Information and Ethereum Address, Admin EA
Result: Manufacturer Ethereum Address (EA) Added to Authorized List L
procedure MRCONTRACTCREATION(AdminEA)

Owner ⇐ AdminEA;
procedure ENROLLMANUFACTURER(Manufacturer Info) Manufacturer
submit enroll request;
if information provided complete then
  if Admin Approval then
    L [L, EA];
    Event (EA, Name, Timestamp);
  else
    Ignore;
  end
else
  Ignore;
end
```
