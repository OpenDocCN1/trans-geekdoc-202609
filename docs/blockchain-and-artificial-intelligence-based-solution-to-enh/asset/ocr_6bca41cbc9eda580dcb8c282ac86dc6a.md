# Blockchain for Digital Identity

credentials (e.g., additional public keys) that the identity holder wishes to disclose, and the corresponding network addresses. It is essential that the DID document contains no information about the owner or other person identifying information.

A DID document is typically composed of the following properties (Sporny et al., 2021):

+   - **Context**: Identifier for the standards used in the document.
- **DID subject**: Identifier or information about the DID that is described by the DID document.
- **Public keys**: Are required for digital signatures as well as encryption and decryption, which in turn serve as the basis for processes for authentication or the establishment of secure connections with service endpoints. If a DID document does not contain a public key, it can be assumed that the public key has been revoked or is invalid. Each public key must have an id and type property, where the id only be used once within the DID document.
- **Authentication**: How a DID subject can cryptographically prove its identity.
- **Authorization and delegation**: Defines how processes can be executed on behalf of the DID subject. Delegation describes what a DID subject can use to authorize others to act on its behalf.
- **Service endpoints**: Can represent any type of service, such as identity management services, authentication/authorization services, social networks, data, storage, etc.

# 2.4.3 DIDComm

Secure communication on the Internet is key. Most protocols “rely on keys, identity providers, certificate authorities, browser or app vendors, or similarly decentralized assumption” (Curren et al., 2021).

DIDComm defines a secure and private communication method that is built on decentralized identifiers. It is an agent-based approach where an agent is intended to be the user's wallet. The endpoints and public keys of the involved parties in the communication are obtained from the DIDs and DID documents. From a technology perspective, the DIDComm signed message is a JWT (JSON Web Messages) envelope.

# 2.4.4 Verifiable Credentials (VCs)

Credentials are an essential part of each identity system. VCs are digital credentials that are cryptographically secure, privacy respecting, and machine-verifiable (Sporny, Longley & Chadwick, 2021). Owners or holders of VCs can create verifiable presentations from them and present them to verifiers. VCs are signed by the issuer of the credential. It can be seen as a proof backed by evidence today statement of the claim. In order to verify the legitimacy of a VC, the verifier has access to a verifiable data registry, e.g., a blockchain storing the DIDs and DID documents of the issuer.

Various technology implementations for VCs exist today, but none has succeeded. Some of the buzzwords are JSON-JWT, JSON-LD, ZKP-CL, and JSON-LD ZKP