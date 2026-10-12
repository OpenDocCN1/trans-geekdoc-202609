
The method depicted in [Figure 8.1](#ch16.xhtml#f21) shows how the current taxonomy could also be used to direct system design at various stages in the design process. The decision of whether to decentralize the trust authority – or not – is the first step in the process. A blockchain is often used in cases where there is no need for a single trustworthy authority; as such, the authority may be fully or partially decentralized. Considering blockchain’s limitations, the next major decision is whether to divide computation and data storage among on-chain and off-chain components. Following that, several design decisions about blockchain configuration must be taken, including blockchain type, consensus protocol, block size and frequency. The indicators in [Figure 8.1](#ch16.xhtml#f21) only display one of the several potential design decision stages. Some decisions have a significant impact on scalability (block size and frequency), security (consensus protocol), cost-efficiency (blockchain type) and performance (like data structure). Finally, determining where to deploy the blockchain-based system’s modules is key [[25](#ch16.xhtml#r312)].

![Figure 8.1 Design process. ¶ Source: [[25](#ch16.xhtml#r312)].](html/images/9781032078243_C008_001.jpg)

[Figure 8.1](#ch16.xhtml#f21b) Design process. ¶ Source: [[25](#ch16.xhtml#r312)].

## Blockchain Application Design: Good Practices and Considerations

Good practices for designing blockchain applications begin with maintaining consistency, particularly when dealing with a new user experience. In DApp, it is impossible to revert or cancel the transaction in the blockchain once published; therefore, users should be made aware of the blockchain’s irreversibility. Moreover, users must be guided in every step while using the application as this will eventually help the users avoid mistakes and user-related frustration.

As discussed before, an important consideration in application design is user feedback. If neglected during the design process, DApps developers are likely to misjudge important user requirements needed in the blockchain applications [[11](#ch16.xhtml#r298), [12](#ch16.xhtml#r299)].

[Table 8.1](#ch16.xhtml#t13) contains a list of the important design factors that should be considered when designing a blockchain application [[21](#ch16.xhtml#r308)].

[Table 8.1](#ch16.xhtml#t13b) Blockchain Application Design Issues and Considerations

| **Blockchain** Design Considerations | Attributes |
| --- | --- |
| Performance | • The inefficiency of resources, such as high energy consumption levels related to the proof of work consensus.<br>• Excessive latency for real-time output. |
| Reliability | • As no single point of failure should occur, high availability.<br>• Reduce the probability of secondary failures.<br>• The inherent high volatility in digital currency exchange rates. |
| IT security | • User identification and authentication through appropriate asymmetric encryption.<br>• Enabling applications to track and trace (digital product memory).<br>• Blockchain-appropriate access control tools and authorizations, as applicable. |
| Scalability/extendibility | • Potential low scalability as block size is often restricted.<br>• Each transaction is broadcasted on all network nodes and requires broad data streams to be filtered and selectively processed.<br>• Extensibility relies on the Turing-complete language for scripting. |
| Compatibility/interoperability | • Due to numerous client implementations and open-source code, high compatibility is achievable. |
| Fault tolerance | • Blockchain transactions remain unchanged, therefore a fault in any node will be transparent to all other nodes. |
| Quality of service | • Quality of service (QoS) determines the system’s ability to offer its services reliably and with a response time and throughput that are satisfactory to the blockchain nodes.<br>• For vital data transactions between nodes, quality of service is a must. |
| Failure management | • The blockchain must be designed in such a way that it can survive attack-related failures.<br>• There should be systems in place that will identify the cause of a failure and initiate appropriate recovery plans, allowing the blockchain to recover from failures automatically. |

## Summary and Conclusions

This chapter has taken a look at the guiding principles and considerations related to designing a blockchain application, specifically how the application design process should start with the creation of personas. Next, user stories – based on personas –- should be created in order to help define the functional (business) requirements of the application. Based on the needed functional requirements, technical requirements and tasks will in turn be defined. In addition, various frameworks, procedures or approaches currently used to design and/or build decentralized applications (DApps) for blockchain systems are also discussed in this chapter. As such, the primary goal of this chapter is to provide auditors with a basic understanding of relevant factors that should be considered during the design phase of a blockchain application before moving on to the development phase, which is the focus of the next chapter.

## Core Concepts

*   There are a number of basic design considerations that must be considered based on user personas and user stories. These include decisions related to whether the application needs to be monolithic or modular, centralized or decentralized; or whether the application should focus on user consistency or specialization.
*   Often, maintaining consistency is a good practice when designing blockchain apps. The various types of consistency include visual, functional, internal and external consistency.
*   The main aim of software engineering for DApps is to ensure that project agreements are well defined. Numerous approaches can be used to develop decentralized application developments. The Ancile project’s main aim is to solve data protection and security issues by enabling the access of electronic records to customers and third parties in a safe and interoperable manner. The ontology-driven approach (ODA) is one of the design approaches which aims to track objects in a supply chain while enabling organizations to understand data that are spread across multiple databases. ODA is useful for both the design and development phases of a DApp.
*   The software engineering strategy entails the use of UML models to describe the requirements and design of a DApp. While the model-driven approach is useful for the design stage and behavior of blockchain applications, model-driven-based approaches do not necessarily require the use of smart contracts. User participation is essential for user-centered design which can be achieved in the user design approach. In the user design approach, users can contribute to the design process through interviews, focus groups and on-site observations.
*   The irreversibility of the blockchain should be made clear to users. During the application’s use, users must be directed through each step. This will assist users in avoiding costly or time-consuming blunders. DApps will often fail if user feedback is ignored during the design phase.
*   An application should be easy to understand and use for users. Function and design aspects of the application should often be feature-light, unless there are compelling reasons not to create a feature-light application. The user interface is the first step in making the application as easy to learn and use as possible.

## Activity for Better Understanding

Use the blockchain design knowledge acquired in this chapter to initiate a blockchain application design project in your organization. Consider the following questions:
