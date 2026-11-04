
Hyperledger’s technical steering committees ensure robustness and interoperability between these different technologies. The hope is that the cross-industry, open-source collaboration will advance blockchain technology and deliver billions in economic value by sharing the costs of research and development across many organizations.

Hyperledger is identifying and addressing the important features and requirements missing from the blockchain technology ecosystem. It’s also fostering a cross-industry open standard for distributed ledgers and holding open space for developers to contribute to building better blockchain systems.

Hyperledger has a project life cycle similar to that of the Linux Foundation. A proposal is submitted and then the accepted proposals are brought into incubation. When a project has reached a stable state, it graduates and is moved into an active state. As of yet, all Hyperledger projects are in the proposal or incubation stage. Each of the projects is led by a large corporation or startup. For example, Fabric is led by IBM, Sawtooth by Intel, and Iroha by the startup Soramitsu.

Hyperledger, like many open-source projects, uses GitHub ( [ `www.github.com/hyperledger` ](http://www.github.com/hyperledger) ) and Slack ( [ `https://slack.hyperledger.org` ](https://slack.hyperledger.org) ) to connect with teams working on each of the projects. These are great places to get the latest updates and to check on the progress that these projects are making in development.

# Focusing on Fabric

Hyperledger’s first incubation project, Fabric, is a permissioned blockchain platform. It works like most blockchains in that it keeps a ledger of digital events. These events are structured as transactions and shared among the different participants. The transactions are executed without a cryptocurrency. An optional resource for you to dive deeper into the subject is at [ `https://trustindigitallife.eu/wp-content/uploads/2016/07/marko_vukolic.pdf` ](https://trustindigitallife.eu/wp-content/uploads/2016/07/marko_vukolic.pdf) .

All transactions are secured, private, and confidential. Fabric can only be updated by consensus of the participants. When records have been inputted, they can never be altered.

Fabric is an enterprise solution interested in scalability and being in compliance with regulations. All participants must register proof of identity to membership services in order to gain access to the system. Fabric issues transactions with derived certificates that are unlinkable to the owning participant, thereby offering anonymity on the network. Also, the content of each transaction is encrypted to ensure only the intended participants can see the content.

Fabric has a modular architecture. You can add or take way components by implementing its protocol specification. Its container technology can handle most of the mainstream languages for smart contracts development.

Bitcoin, on the other hand, allows anyone to participate anonymously and the community is always looking for ways to be censorship resistant and to enable those who have been disenfranchised. Bitcoin was also mainly engineered for the movement and security of its cryptocurrency token. For this reason, comparing the best practices of Bitcoin to those of Fabric may be unfair.

## Building your system in Fabric

A lot of work has gone into making Fabric accessible, but it’s still only approachable by people who are technically savvy.

Hyperledger has detailed several use cases that it’ll be gearing its technology toward. You’ll be able to use Fabric over the outlined use cases in the near future with intuitive user interfaces. For now, you can develop and test the listed use cases with the help of a core developer.

## Diving into chaincode development

Contracts between two parties can be translated into code on the Hyperledger Fabric via Chaincode. Chaincode is Hyperledger’s version of Ethereum’s smart contract. It automates the agreements made within a contract in a way that both parties can trust.

Chaincode is Turing complete like the smart contracts of Ethereum. Currently, you can have a Java developer build a chaincode contract for you. The Fabric team has prepared some common use cases such as digital currencies and sending text messages as part of the core framework.

The Fabric team is also exploring other interesting business use cases that were not complete at the time of this writing but may be available by the time you’re reading this.

Hyperledger is early in development and its projects are about two years behind Ethereum’s work. However, each of the projects does have substantial teams and resources devoted to it:

*   **Business contracts:** Hyperledger has come up with ways to have both public contracts and private contracts. Private contracts are between two or more parties and contain confidential information. Public contracts are viewable by anyone who takes the time to search for them within Hyperledger. For example, you might use a public contract to make a public offer to sell a product or as a way to solicit bids on a contract.

    The makeup of these contracts is more complex than traditional contracts because arbitration and third-party enforcement are removed. Additionally, the authentication of the individuals participating in the contract is needed. Plus, most contracts are unique and can’t be standardized. The more complex the contract, the more places it can be corrupted from its original intent. Hyperledger is working on creating a contract management system to help enhance the scalability of Chaincode.

*   ** Manufacturing supply chain:** Supply chain management is an exciting blockchain scheme that is being explored on Fabric. Final assemblers could manage all the component parts and supplies that they used in creating their product. This feature would enable you to be responsive to demands and be able to track back the origin of each part to the original producer. In the case of a product recall, it would be easy to find the culprit or the ability to tell the authenticity of each part before it’s utilized.

    Fabric requires more development before it’s ready for this use case because it will need to be easily accessible to everyone in the supply chain. The Fabric team is working on a standard protocol to allow every participant on a supply chain network to input and to track numbered parts that are produced and used on a specific product.

    When it’s finished, this use case would allow deep searches to be done on the production of each product at any time. This might be ten or more layers deep in the production of any one item. Consumers could then establish the provenance of any manufactured good that is made up of other component goods and supplies. This may have an interesting social impact on consumption.

*   **Securities and assets:** Securities and other assets are well suited to blockchain because they can automate many of the functions that third parties perform. Fabric will allow all stakeholders of an asset to have direct access to that asset and its makeup and history, bypassing intermediaries that now hold that information. Fabric will also speed up the settlement time on assets to near real time.

*   **Direct communication:** In the future, Fabric could also be used as a place where companies can make public announcements and offers. For example, if a company wanted to raise funds and needed to notify all shareholders of the complete details of the offer in real time, it could. Like the decentralized autonomous organization (DAO) of Ethereum, shareholders can make decisions and execute them. Their decisions will be processed and settled in real time. This will make shareholder meetings and voting much easier and faster.
