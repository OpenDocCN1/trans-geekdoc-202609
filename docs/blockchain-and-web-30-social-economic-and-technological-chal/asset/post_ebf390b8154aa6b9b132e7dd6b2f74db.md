
that are important for a blockchain remote inspector: privacy, extendibility, pluggability, consistency, reusability, and instrumentation. We detail the characteristics as follows:

- **Privacy:** Inspection should not breach or compromise data privacy by exposing data to unauthorized users. When considering smart contracts, a lack of privacy is dangerous, as it could be exploited by malicious users to acquire illicit advantages and resources.

- **Extendibility:** The inspector can be extended for other technologies. Ideally, a debugger or inspector should rely on a middleware that is extensible. For smart contracts, the inspector should be extensible over different smart contract languages and blockchain technologies.

- **Pluggability:** The inspector can be used on existing objects without the need to re-instantiate the objects or the system. For contracts, this means we can inspect existing deployed contracts without any dependency on the contract side or the need to redeploy the contract. An unpluggable approach has the disadvantage of requiring the redeployment of a contract, which has nontrivial transactional costs.

- **Consistency:** The representation used by the inspector must reveal the information in a consistent manner, i.e., the inspection must reflect the current state of the deployed contract.

- **Reusability:** The inspector can be reused for different contracts. Lack of reusability would require a developer to spend time redefining the inspection for each individual contract.

- **Instrumentation:** The inspector can alter the semantics of a process to assist in debugging. Basically, this is the mechanism to halt the process and inspect it at that point (e.g., breakpoints and watchpoints). This characteristic is not possible in blockchain platforms, as we cannot modify the deployed contract code to halt a function in the middle of its execution in the blockchain.

We analyzed SmartInspect and two other inspectors (Remix and Etherscan) according to the aforementioned characteristics for inspectors. We also compared two practices for accessing contract data: ad-hoc decoder and getter methods (Table 13.1).

Table 13.1 Related techniques comparison

| Characteristic | SmartInspect | Remix | Etherscan | Decoder | Getter |
|---|---|---|---|---|---|
| Privacy | Yes | Yes | No | Yes | No |
| Extendibility | Yes | No | No | No | No |
| Pluggability | Yes | Yes | Yes | Yes | No |
| Consistency | Yes | Yes | Yes | Yes | Yes |
| Reusability | Yes | Yes | Yes | No | No |
| Instrumentation | No | No | No | No | No |

As we can see from Table 13.1, SmartInspect's only characteristic flaw is related to instrumentation for remote debugging. However, this is a limitation imposed by the Ethereum blockchain technology rather than a design flaw in our approach.

Remix [Eth18b] is a suite of tools designed by the Ethereum Foundation for Solidity developers. Remix IDE is probably the most used tool in its suite. In the Remix tool suite, there is a full transaction debugger with inspection capabilities. Remix inspector only falls short in extendibility and instrumentation. It was designed specifically for Solidity and Ethereum, and as such, it is not extensible to other platforms. As we previously explained, instrumentation is not possible due to the characteristics of the Ethereum platform.

Etherscan is an analytics platform for Ethereum. It provides live information from Ethereum on blocks, transactions, contracts, etc. If a developer publishes his/her contract source code on Etherscan, then it will be possible to inspect the contract's data. However, by doing so, the developer will expose his contract source code and internal data to anyone, in a very easy way to access it. That is the reason why Etherscan inspection lacks privacy (unlike SmartInspect and Remix, which can expose the data to the developer only). Etherscan provides an API to access its services, but it is not extensible. Just like SmartInspect and Remix, Etherscan's inspector cannot support instrumentation.

An ad-hoc decoder uses the Ethereum API on the memory slots to manually fetch the data. This is a complex task, since it demands a deep understanding of the memory layout of each contract a developer plans to inspect. It also requires a developer to know the type of each attribute and code the ad-hoc decoder accordingly. Its advantages are that it allows access to data without loss of privacy and without the need to redeploy the contract. In fact, SmartInspect uses this concept of decoding memory layouts as a part of its inspection process.

Getter methods are a simple solution since they are cheap to implement and easy to test. The developer does not need to know the memory layout of a contract to create getter methods. However, if the developer forgets to make a getter for a given attribute, he/she will need to redeploy the contract and, most often, lose the data from the previous instance. Solidity does not support the return of many complex types (e.g., structs, mappings) on its functions. Therefore, a developer might need to adapt his/her data or function to provide access to a complex type. Moreover, the easy access to the data may cause a loss of privacy, since getter methods are a public part of the contract binary encoding.

## Related work

Chis et al. [CNSG15] performed an exploratory study to better understand what developers expect from object inspectors, and based on that feedback, they propose a novel inspector model. The authors interviewed 16 developers for a qualitative study, and a quantitative study conducting an online survey where 62 people responded. Both studies were used to identify four requirements needed in an inspector. Then they propose the Moldable Inspector, which indicates a new model to address multiple types of inspection needs. We followed the lessons taken by the Moldable Inspector when creating SmartInspect. We deem noteworthy the multiple views aspect, as SmartInspect can present its inspected data in four different views (REST, Pharo U.I., JSON, and HTML).

Papoulis [PBD+15] gives a deep analysis of remote debugging. As discussed by the author, remote debugging is especially important for devices that cannot support local development tools. The author identifies four important characteristics for remote debugging: interactivity, instrumentation, distribution, and security. Based on the identified properties, Papoulis proposed a remote debugging model called Mercury. Mercury employs a mirror-based approach and an adaptable middleware. We used Papoulis research as an inspiration to create SmartInspect, especially relying on a mirror for remote inspection.

Salvaneschi and Mezini [SM16] propose a methodology, called RP Debugging, to debug reactive programs more effectively. The authors discuss the idea that reactive programming is more customizable and easier to understand than its alternative, the observer design pattern. The authors also present the main problems and challenges to debug reactive programs and the main design decisions when creating their methodology. Although our inspector is from a different application domain, the RP Debugging design served as an inspiration to plan our own inspecting approach.

Srinivasan and Reps [SR14] developed a reverse engineering tool to recover class hierarchical information from a binary program file. Their tool also extracts composition relationships. They use dynamic analysis to obtain object traces, and then they identify the inheritance and composition information among classes on those traces. The authors' experiments show that their recovered information is accurate according to their metrics. The author's tool contrasts with SmartInspect, as we use static analysis and they use dynamic analysis.

## Chain navigation and query language

Ethereum and other blockchains store a massive amount of heterogeneous data. In early 2017, Ethereum was estimated to have approximately 300GB of data [BLPB17]. Retrieving information from this massive amount of data is not an easy task. Moreover, the Ethereum platform only allows direct access to its first-class data elements, which includes blocks, transactions, accounts, and contracts [Eth14]. Therefore, if we search for a particular piece of information inside a data element, we would need a unique identifier (i.e., either the number or its hash) to access the block containing such information. Another alternative would be to directly access one block and sequentially access its parents to search for a data. Moreover, the information returned by the Ethereum platform when we access its blocks is encoded into a JSON-like structure that we need to interpret to acquire a specific item. Therefore, the Ethereum platform does not provide a semantic way to search for information nor an easy form to present such information.
