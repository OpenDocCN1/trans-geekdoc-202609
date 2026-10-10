
Also inferred from the Byzantine fault tolerant algorithm, this algorithm introduces the use of speculation to both minimise the cost and simplify the design compared with traditional Byzantine fault tolerant algorithms. The validators respond automatically to any request, skipping the three phases commit protocol proposed in PBFT. Therefore, they follow the order of the so called ‘primary’; thus, because the three-phase commit protocol is never executed, the network communications are reduced to theoretical minimums. However, some inconsistencies may come up that must be addressed by the validators and devices.

### 7.3.2.3 New transaction acceptance

As opposed to the public blockchain algorithms or other permissioned consensus algorithms, there are extra factors that may be considered when accepting new transactions and thus creating new blocks, particularly when facing highly constrained and heterogeneous scenarios. Let’s assume an edge scenario, where different edge devices should be endowed with security guarantees. In this scenario, an edge device must not blindly accept any transaction because this would make the system insecure. A solution to handle this issue would require this device to check for each transaction, what consequently requires a centralised service performing the checks, driving again towards a centralised solution, which is not good at all. In fact, the edge must follow a distributed system architecture, while at the same time providing security. Aligned to that statement, edge systems must be careful around the policies applied when adding a new transaction to check both the new transaction does not to violate any security requirement and the issuer of the transaction has the right to perform the operation. Ideally, this information should be stored in the blockchain, too, so any lookup becomes a local query, making the edge really distributed with no need to rely on the cloud or any other centralised agent. However, when this is not the case and a third party should be also considered, the requests should be kept to a minimum, only demanding a really small set of operations, aimed at minimising the centralised dependence of such request.

## 7.4 BLOCKCHAIN SERVICES IN EDGE COMPUTING

This section introduces several possible solutions aimed at providing security to devices at the edge. All solutions described in this section leverage blockchain technologies, considering a blockchain putting together all devices in the network, and each device associated with a profile, including the device public key. The section starts by presenting a method to create a secure device profiling over the blockchain. Afterwards, a method for authentication using the blockchain device profiles is presented. Finally, a method for sharing signed data with the blockchain using the previously described profiles is shown.

Figure 7.5 presents the most basic blockchain edge network among those described in this chapter. Indeed, devices and profiles are included inside the blockchain network, and each device has a copy of the data (all the other profiles). Consequently, each device will be able to locally verify any other device through the blockchain using the profiles, with no need to rely on any other entity or third party.

![Figure 7.5 Blockchain network example with profiles.](images/fig7_5_B.jpg)

*Figure 7.5 Blockchain network example with profiles.*

### 7.4.1 Secure device profiling

Providing security at the edge requires all edge devices to be identified and secured. To that end, the edge, as a system, requires an element responsible for helping other devices identify the components in the edge network and access its profiles. This is certainly critical because the profiles are stored in the cloud, and this is largely known not to be feasible or scalable for edge scenarios. Therefore, the edge requires a technology that allows us to store those profiles in a distributed way, over the edge, and this technology may be blockchain.

Blockchain provides us with the distribution of data and the immutability of that data. Following these properties, the edge can distribute a device profile using the blockchain in a secure manner. The profile can be stored in the blockchain inside a transaction, and it can be exposed as a device ID (see Figure 7.6). With this data structure, the blockchain will store the session state of the edge devices, this session would be composed of device identifiers and data, and it would maintain all blockchain properties.

![Figure 7.6 Session example with devices profiles in form of transactions on the blockchain.](images/fig7_6_B.jpg)

*Figure 7.6 Session example with devices profiles in form of transactions on the blockchain.*

To offer trust on the blockchain profiles, the transaction must be verified and partially controlled, so no malicious device can introduce malicious profiles. Therefore, it seems that a permissioned consensus algorithm in a hybrid architecture may be the proper option for a successful blockchain deployment at the edge.

Once the transactions and profiles are trusted, the device IDs are required to be trusted. To do that, the profiles will require a key pair. Elliptic curve cryptography (ECC) will perform better than RSA because the former has better performance with less key size. Then, the private key of the pair will be held by the device and the public key will be stored on the blockchain. With this strategy the public key will become the device ID, and the profile will only be verified to the device owning the private key.

Although this storage by itself does not do much in terms of security because the transactions and blocks have to be approved by the validators, the edge can actually use the blockchain to perform a public key distribution of approved devices at the edge. This will act as the edge session that will tell other elements that a given key belongs to the edge and should be trusted, as seen in Figure 7.7.

But again, this structure alone does not provide any flexibility at all because the public key cannot be associated with anything, which is also motivates that every transaction should have a rule-set. Indeed, a rule-set is defined as a set of actions that are applied to the session for a given ID (public key). For example, when a device registers into the session providing its public key, a rule-set of registration will be added. Afterwards, this profile may be used, for example, when choosing devices to execute edge services or simply when performing machine-to-machine connections, so a device can know if is connected to another device.

When performing a registration, the device to be registered will provide its edge profile, including the device capabilities and sensors. The capabilities are defined as what a device is, for example, as shown in Figure 7.8: Vendor, OS, CPU, RAM, GPU, battery, or AC power. Certainly, this is just an example, and many other different characteristics and attributes may be included in the edge profile. These capabilities will be used to select the set of resources best suiting what a particular service demands to be successfully executed. Hence, in short, the profile will keep a register of the device attached sensors and will help other devices to know what the device sensors are and what they can provide.

![Figure 7.7 Session example with devices profiles in form of transactions on the blockchain, containing a public key and a rule-set.](images/fig7_7_B.jpg)

*Figure 7.7 Session example with devices profiles in form of transactions on the blockchain, containing a public key and a rule-set.*
