# 2.5 Off-chain applications

# 2.5.2 Distributed ledger node APIs

Blockchain node APIs range from pure REST APIs (e.g., Hyperledger Fabric) to JSON-RPC (e.g., Ethereum) with the usual connectivity methods including HTTP, WebSocket, and IPC. Not all of them are necessarily present in DLTs or even in different implementations for the same DL network. Approaches also differ in the set of features provided through the API. But they commonly offer information about the node client, blockchain network, blocks, and transactions, provide account management, and enable the creation and submission of new transactions.

# 2.5.2.1 Ethereum JSON-RPC API

Ethereum JSON-RPC is the API for Ethereum node implementations. Not all of the implementations ensure the same feature set. In Tab. 2.4, we provide a brief comparison of connectivity methods in some of the dominant nodes. The combination of JSON-RPC and HTTP is common for all of them. IPC and WebSockets are supported only in some cases. Suppose we design a decentralized application, which specifically relies on, for example, a WebSocket connection, we must account for the possibility that not all network nodes will be configured for DL network access or adaptations will be needed to migrate from one blockchain network to another.

Tab. 2.4: JSON-RPC support in various Ethereum node implementations.
| Cpp-ETH | Go-ETH | Py-ETH | Parity | HL Besu |
|---|---|---|---|--|
| JSON-RPC 1.0 | + | | | | |
| JSON-RPC 2.0 | + | + | + | + | + |
| HTTP | + | + | + | + | + |
| IPC | + | | | + | + |
| WebSocket | | + | | + | + |

Ethereum JSON-RPC API has a single endpoint, for example, http://localhost:8545. The API method, along with the corresponding parameters, is embedded in a JSON structure submitted to this endpoint. The Ethereum JSON-RPC API enables selecting features and gives detailed information about node status, including number and details about the connected peers. Account management returns a list of addresses owned by the client. These accounts must be enabled when we start the node. The API provides detailed information about ledger synchronization, including block and transaction details. We can create, sign and send new transactions to

28 https://eth.wiki/json-rpc/API