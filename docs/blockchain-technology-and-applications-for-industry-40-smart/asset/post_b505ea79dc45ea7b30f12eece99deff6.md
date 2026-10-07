
## 2.5 Decentralized applications

a mirror node in Hedera, but Hedera and community mirror nodes are available, with APIs for Hedera services.

The API endpoints in public networks commonly impose no access control to the off-chain applications. Lack of access control might seem surprising if we compare it to the API access in many Web-based applications. Nevertheless, the ledger is shared and available to all involved parties, there is no need to protect access to it. Blockchain account-related operations, which can lead to severe security vulnerabilities, are performed in the off-chain application parts. If we establish some access control for the node API, it is mainly to protect the node's computing resources.

### 2.5.1 Off-chain application examples

Off-chain applications utilize the established Web, mobile, server-side, and embedded applications technologies to provide user and machine interfaces for the DApps.

Apart from the node APIs, blockchain ecosystems usually provide off-chain libraries for different programming languages. These convenience libraries abstract much of the complexity of interacting with blockchain node APIs.

Despite a remarkable resemblance between traditional and blockchain-enabled Web interfaces, several usability problems. They are mostly related to the BC transaction latency. Therefore, users cannot count on refresh rates and response times expected in traditional Web applications. Consequently, it is a good user interface design principle to notify the user when we await a longer response than expected due to the DL network interaction. For example, we can temporarily redirect a user to chain explorer (see Section 2.6.4) for live tracking of their transactions during that period.

Another blockchain backend effect on off-chain Web, server, or embedded applications arises from blockchain API queries. We cannot form the node API requests as efficiently as in, for example, relational databases. The number of requests to a remote API might become substantial, if the client application design does not consider this possibility. This can result in increased node-resource consumption and unnecessary communication load between the client-side application and the API. The latter might be especially challenging in communication-constrained embedded lot applications.

### 2.5.1.1 Client-side web applications

Client-side Web applications run in browsers. Apart from the execution of client-side application logic, the browser must include a key wallet. A wallet enables the management of blockchain keys and identifications. It can be an integral part of a browser (e.g., Brave²) or a browser extension. Metamask³ is a popular wallet extension for Ethereum-based networks. Figure 2.10 shows the Metamask menu, where we can toggle between available Ethereum networks, including the Mainnet and various public test networks. With Metamask, we can also attach our browser to an Ethereum node running on the local computer or specify a URL to an arbitrary JSON-RPC node API. In this way, we can access, for example, private or consortium networks with the Ethereum DLT.

![](img/0a07f1fa1a7ff1beaaa3170e7e172821_100_0.png)

Fig. 2.10: Metamask wallet extension in a Web browser.

A common convention in the Ethereum Web ecosystem is for management software to expose their API via a JavaScript object on the Web page. The EIP 1193⁴ formalizes an Ethereum Provider API to promote wallet interoperability. The API is designed to be minimal, event-driven, and agnostic of connectivity and RPC protocols. Its functionality can be extended by defining new RPC methods and message event types.

- 22 https://brave.com/
- 23 https://metamask.io/
- 24 https://eips.ethereum.org/EIPS/eip-1193

In the client-side application, developers apply client libraries for BC node API interactions, for example, Web3.js2⁵ for Ethereum Web applications, and create their application-specific programming logic. Web3.js is a collection of libraries that allows us to interact with a local or remote Ethereum node using HTTP, IPC, or WebSocket. In this way we can use all the Web-interface technologies (HTML5, CSS, and JavaScript) or frontend frameworks to create rich, interactive, and modern Web user interfaces that utilize blockchain features. These user interfaces interact with blockchain networks.

### 2.5.1.2 Web-server or embedded application parts

We must arrange the blockchain key management differently, if the software running in a server or an IoT device needs to interact with a blockchain node API. No human will toggle the available blockchain networks or provide the wallet-access authorization credentials. Still, we might need a key store in an application. We usually set the DL network and the account information only during the initial configuration of the server-side application.

On the other hand, the interactions with the BC node API are very similar to the ones in client-side Web applications. If we develop, for example, a Node.js backend application or IoT device software, we include the same Web3.js library (see Section 2.5.1.1) for Ethereum Web applications. Off-chain application development for Ethereum is not limited to JavaScript. Web3.py²⁶ is a Python library for interacting with Ethereum. Originally, it was derived from Web3.js but has since evolved toward the needs of Python developers.

### 2.5.1.3 Mobile applications

A very similar approach is taken in mobile platforms, too. There are mobile Web browsers and mobile browser plug-ins available. Metamask, for example, runs on Android and iOS, too. This facilitates access to the Web-based blockchain application as for the desktop browsers.

Web3.io²⁷ is a lightweight, reactive, type-safe library for Java, Android, Kotlin, and Scala, if we develop mobile applications that do not rely on browser functionality.

- 25 https://web3js.readthedocs.io
- 26 https://web3py.readthedocs.io
- 27 http://web3.io/

## 2.5.2 Distributed ledger node APIs

Blockchain node APIs range from pure REST APIs (e.g., Hyperledger Fabric) to JSON-RPC (e.g., Ethereum) with the usual connectivity methods including HTTP, WebSocket, and IPC. Not all of them are necessarily present in DLTs or even in different implementations for the same DL network. Approaches also differ in the set of features provided through the API. But they commonly offer information about the node client, blockchain network, blocks, and transactions, provide account management, and enable the creation and submission of new transactions.

### 2.5.2.1 Ethereum JSON-RPC API

Ethereum JSON-RPC is the API for Ethereum node implementations. Not all of the implementations ensure the same feature set. In Tab 2.4, we provide a brief comparison of connectivity methods in some of the dominant nodes. The combination of JSON-RPC and HTTP is common for all of them. IPC and WebSockets are supported only in some cases. Suppose we design a decentralized application, which specifically relies on, for example, a WebSocket connection, we must account for the possibility that not network nodes will be configured for DL network access or adaptations will be needed to migrate from one blockchain network to another.

Tab 2.4: JSON-RPC support in various Ethereum node implementations.

| Cpp-ETH | Go-ETH | Py-ETH | Parity | HL Besu |
|---|---|---|---|---|
| JSON-RPC 1.0 | + | | | | |
| JSON-RPC 2.0 | + | + | + | + | + |
| HTTP | + | + | + | + | + |
| IPC | + | | | + | + |
| WebSocket | | + | | + | + |

Ethereum JSON-RPC API has a single endpoint, for example, http://localhost:8545. The API method, along with the corresponding parameters, is embedded in a JSON structure submitted to this endpoint. The Ethereum JSON-RPC API enables selecting features and gives detailed information about node status, including number and details about the connected peers. Account management returns a list of addresses owned by the client. These accounts must be enabled when we start the node. The API provides detailed information about ledger synchronization, including block and transaction details. We can create, sign and send new transactions to

28 https://eth.wiki/json-rpc/API
