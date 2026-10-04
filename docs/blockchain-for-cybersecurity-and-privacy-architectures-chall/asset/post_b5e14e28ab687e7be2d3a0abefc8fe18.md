
# Blockchain-Based Trust and Security in CCN–Based Internet of Things

The rise of the IoT, with its myriad of connected things, will open many security breaches. Object identity is recognized as a common security concern in the perception, application, and network layers. Moreover, in terms of computer identification, machine-to-machine interaction faces a more significant challenge. Security solutions should verify the veracity of device data, device integrity, and system identity while protecting data. Since CCN relies on basic materials for content identity and authentication (public key infrastructure), effective authentication techniques should be employed for efficient and flexible trust management and secure communication.

An emerging solution is to use the blockchain technology as a distributed ledger of information to bring scalable, decentralized security and trust to IoT devices. Combining blockchain, CCN, and IoT seems like a potentially interesting approach. The combination of CCN and blockchain was also carried out by Conti et al. (2019), Labbi et al. (2018), and Zhu et al. (2018). In this chapter, we present a naming-based security model combined with blockchain technology that guarantees devices identification and authentication, data integrity, name authenticity, and relevance.

The proposed method not only considers the IoT security issue but also accounts for introducing CCN as a potential networking architecture that addresses other IoT requirements. The combination of blockchain technology and CCN-IoT is an excellent solution to manage trust and key management and avoid the dependency on a trusted third party.

This remaining chapter is organized as follows: Section 7.5 explores the feasibility and advantages of the CCN approach in the IoT, Section 7.6 introduces our approach based on the combination of CCN naming feature and blockchain technology. Section 7.7 introduces experimental results and their discussion. Finally, Section 7.8 concludes our work.

## 7.5 ADVANTAGES OF USING CCN FOR THE IoT

In recent years, the CCN approach has gained increasing attention and has emerged as a alternative networking solution to the IoT (Amadeo et al. 2014; Garcia-Luna-Aceceves 2017).

The CCN model improves the organization and retrieval of data and enhances network scalability, reliability, and security. It has the characteristic of disassociating information from its supplier, thus opening new horizons by supporting mobility and storage in the network. Owning its intrinsic features allows a decentralized and intelligent data-delivery platform to serve today’s heterogeneous IoT services that are hard to achieve over.

### 7.5.1 POWER CONSUMPTION

Connected objects use plenty of energy. How will the energy of the 200 billion connected objects be met by 2050?

# Blockchain for Cybersecurity and Privacy

One of the most relevant features of CCN is the use of cache memory at the network level. It has a positive impact on energy aspects. It provides data for various applications, without having to request the content provider. In other word, sensors could sleep more (reduce energy consumption), while their data could be available in cache nodes. In-network caching improves data gathering as well as delivery process. Experiments realized by Baccelli et al. (2014) have shown that energy savings can be accomplished through in-network caching.

### 7.5.2 Service Discovery

The IoT applications produce information using different vocabulary in various formats. As part of the Internet of the future, IoT intends to gather information and provide the right user with the right services, at the right time, in the right place, and on the right device, based on the context available.

Context awareness (Labbi, and Benadillah 2019; But et al. 2013; Kim et al. 2016; Xiao et al. 2010) will play an essential role in determining the information to be processed and reducing the number of services collected by returning only subset of potentially relevant resources in conjunction with the scope of the request.

The CCN naming has a major impact on the function of the network. Each content is identified by a name – or prefix – that has a hierarchical structure, similar to URLs. This naming has the advantage of having a semantic meaning for users. The CCN prefixes are then presented as URLs in the following form:

```
/UMP/FSO/video/video.avi
```

This naming scheme offers a defining location identity for quick and accurate access to contents.
The CCN naming scheme offers a better abstraction to fit the problems of today's communication (Table 7.2). In IoT service discovery, the use of context is very relevant.

## TABLE 7.2
CCN Hierarchical Naming for a Service Discovery Request to Get the Appropriate Service

| CCN Name Queries for Appropriate Discovery | Matching Criteria |
| :--- | :--- |
| /MyHome/ | Domain name |
| /MyHome/Garage/ | Domain name, location |
| /MyHome/Garage/Lights/ | Domain name, location, type based |
| /MyHome/Garage/Lights/ON/<signature>/ | Domain name, location, type, action, and relevant information based |

it can play the role of a filtering mechanism that determines which services should be provided to the user, based on the context of the user.

## 7.6 BLOCK-BASED CCN-IoT ARCHITECTURE

The security risks inherent in connected objects are holding back some industrial deployments to date. To maintain information privacy, IoT devices and sensors must share such authentication materials. This requires a lightweight key management system to ensure trust between different things and to be able to distribute the keys at consume the devices' minimum capabilities.

The CCN employs a mechanism based essentially on the addition of digital signatures to the content of an understandable hierarchical naming system, ensuring producer identification and relevance. However, it requires the recovery of the producer’s public key to ensure the authentication of the producer, the integrity of the data, and the authenticity of the names. The integration of blockchain without a central authority appears as a solution to the security of connected objects. Although our solution is intended to be used in wide-range context, we consider in this illustrative example the case of a smart campus. The campus is composed of several buildings; each building is composed of floors and each room contains a number of connected objects (thermometer, light, camera...).

### 7.6.1 Trust Establishment

In this section, we explain the manner of adding devices to the blockchain. Using blockchain as a trusted anchor for security has two key steps: registration and verification.

### 7.6.1.1 Registration and Publication

The registration process allows the blockchain to acquire information about IoT devices. Before a content provider publishes contents, it registers an identity with a corresponding public key. Each new object registers by sending a register message to the blockchain. The register message contains the identity of the new object jointly with its public key, which will be used during verification operation. The public key depends on the namespace where it is acceptable for verifying signatures. A rigid link between the keys and the namespaces is established. Each node of the blockchain is notified and then iterates through the blockchain and checks if identity has never been previously registered. In the case the identity is already registered, the pair is rejected. Otherwise, it performs a publication action by storing the pair in the blockchain. Once an identity has been registered, its identity and public key pair become public.

![Hierarchical naming](img/816c34830872ca25a809f80557c6d27_174_0.png)
FIGURE 7.6 Hierarchical naming.

# Algorithm 1: Registration

+   1. The identity owner generates P,K and P,K
2. The identity owner posts (ID, P,K) to the blockchain, where:
    * ID is the domain name (globally routable name segment)
    * P,K is the public key
If ID is previously registered, then
The pair is Rejected by the blockchain miner
else
add the pair
