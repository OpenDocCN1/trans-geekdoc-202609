![](bbox=[0.145, 0.068, 0.852, 0.283])

Figure 1. Student design.

certificates. Students and Recruiters will be able to view and download the certificate using the IPFS link. The recruiter can filter the students with the help of student ID or based on their departments as we

# 4 IMPLEMENTATION AND RESULTS

# 4.1 Technologies used

+   - **Blockchain** - served as the base for the entire project, is best understood as an immutable database. It offers a reliable setting where what has been stored is concise and unchangeable.
- **IPFS** - A distributed file system can be used to store and share data utilizing the Inter Planetary File System protocol and peer-to-peer distributed network.
- **Smart Contracts** - programs that are saved on a blockchain and are only activated under specific circumstances. In most cases, they are utilized to automate contract execution so that all parties can be confident in the result away right, without the requirement for an intermediary or additional time.
- **Solidity** - The object-oriented programming language Solidity is used to create smart contracts. It is applied when placing smart contracts on different Blockchain systems. Although it has more particular data types, it is similar to Typescript.
- **MetaMask** - With the help of the MetaMask browser plugin, distributed programs, or Daps, are on the browser. To enable Daps to read from the blockchain, the add-on injects the web3 API into the JavaScript context of every webpage.
- **Node.js** - used to create backends and oversee user authentication, serving frontend, and frontend pages. Additionally, it enables web3, which in turn enables to run the solidity code.
- **Mongo DB** – Users’ personal information, session data, and encrypted authentication records are kept in MongoDB, which is a NoSQL database.

# 4.2 IPFS

The fundamental steps in the upload and access of files via IPFS are displayed in the Figure 2(b). The user uploads the file, and the file is sent to IPFS. In IPFS it is broken down into multiple parts and hash of each of the fragments is combined into a single CID which is returned to the system for storage.