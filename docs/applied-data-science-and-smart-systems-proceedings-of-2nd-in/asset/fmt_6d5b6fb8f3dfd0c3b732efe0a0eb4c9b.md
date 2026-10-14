
6. **Temperature and quality monitoring:** In industries with temperature-sensitive goods, intelligent contracts can automate the monitoring of temperature conditions during transportation (Iakovlev et al.,2021). If the pre-defined temperature range is breached, the contract can trigger alerts or take corrective actions automatically.

7. **Sustainability and carbon tracking:** Smart contracts can facilitate the tracking and recording of carbon emissions and environmental impact throughout the supply chain (Marenkovic et al., 2021). It enables companies to measure their sustainability efforts accurately and make datadriven decisions to reduce their carbon footprint.

## Related work

Metaverse and blockchain are disruptive technologies, but integrating blockchain-based metaverse technology in logistics is a relatively new era. However, some work has been done on the domain. For example, [Kamble et al. (2022](#ch44.xhtml#ref44_5)) present a review on integrating digital twins with logistics and supply chain management with digital twins. This study provided the foundation for understanding how blockchain can improve the traceability and security of logistics operations but does not integrate metaverse. [Subramanian et al. (2020](#ch44.xhtml#ref44_20)) presented a fourth-party logistics with blockchain. This study investigates the use of blockchain technology in the context of fourthparty logistics. It highlights how blockchain-based smart contracts can streamline container shipping operations and improve trust among various stakeholders, but it does explore the metaverse.

In addition, [Paliwal et al. (2020](#ch44.xhtml#ref44_13)) presented a new blockchain-based framework for robust logistics. This article discussed the potential and challenges of implementing blockchain in logistics but does not involve metaverse. [Tan et al. (2023](#ch44.xhtml#ref44_21)) designed a metaverse-based logistics and marketing. The work provides insight into how metaverse can be integrated into logistics and marketing. [Roy et al. (2023](#ch44.xhtml#ref44_17)) discussed the integration of blockchain-based metaverse in teaching, but it does not explicitly address logistics. [Table 44.1](#ch44.xhtml#tab44_1) critically analyses the related works on blockchain-based logistics in a metaverse environment. Finally, Ali et al. (2023) and [Gera et al. (2021](#ch44.xhtml#ref44_18)) proposed a blockchain-based AI metaverse in the healthcare system.

[Table 44.1.  Comparative analysis of existing work with limitations](#ch44.xhtml#R_tab44_1)

| Authors || Domain || Limitations |
| --- | --- | --- |
| [Kamble et al., 2022](#ch44.xhtml#ref44_5) || Digital twin integration with logistic supply chain || Metaverse was not integrated into the system |
| [Subramanian et al., 2020](#ch44.xhtml#ref44_20) || Blockchain smart contract-based fourth party logistics || No integration of metaverse |
| [Paliwal et al., 2020](#ch44.xhtml#ref44_13) || Blockchain-based robust framework || No integration of metaverse environment |
| [Tan et al., 2023](#ch44.xhtml#ref44_21) || Metaverse-based logistics and marketing || This work did not integrate blockchain |
| [Roy et al., 2023](#ch44.xhtml#ref44_17) || Metaverse based on teaching || This work does not focus on logistics management |
| Ali et al., 2023 || Blockchain-based and AI metaverse in the healthcare system || This work does not focus on the logistics system |

Based on this literature and related work, work needs to be done on integrating blockchain and metaverse in logistics to improve security and transparency in logistics management systems.

## Proposed work

In this section, we present the architecture of the proposed metaverse-based logistics management system integrating blockchain technology, the proposed algorithms and the experiment environment setup.

### System architecture

The proposed system provides virtual logistics services with immersive experiences for real-time tracking of goods and monitoring the warehouse remotely. [Figure 44.3](#ch44.xhtml#fig44_3) depicts the proposed system architecture. Blockchain is used to store and transfer data to maintain logistics data security. Blockchain helps to foster transparency and trust, developing trust among customers. The customers and logistics entities can be assigned user IDs after successfully registering. **Note**: LCA is a logistics company Avatar, WA; Warehouse Avatar, GA: Goods Avatar and CA: Customer Avatar.

![Figure 44.3 The architecture of blockchain-based logistics management metaverse system](images/fig44_3_C.jpg)

[Figure 44.3 The architecture of blockchain-based logistics management metaverse system](#ch44.xhtml#R_fig44_3)

The proposed architecture comprises four environments: the customer environment, the virtual or metaverse environment, the transporter, and the manufacturer environment.

***Customer environment:*** The customer registers first and is assigned with user_id. When they sign in, they can interact within the virtual environment. A blockchain is created when a customer enters the environment. All the customer records are stored in the block and linked in a blockchain. The blockchain creation for a customer is shown in Equation 1.

(1)  

*Tn* = \[*C*[*i*d*],*Ts*,*D*[*s*i*j*](*C*)\]  

where *Tn*: Transaction, *C_id:* Customer ID, *Ts*: Timestamped, *D*[Sign]*(C)*: Digital customer signature.

***Transporter environment:*** The transporter registers first and is assigned with *T*\_*id*. When they sign in, they can interact within the virtual environment. A blockchain is created when a transporter enters the environment; all the record of the customer is stored in the block and linked in a blockchain. The blockchain creation for the transporter is shown in Equation 2.

(2)  

*Tn* = \[*T*[*i*d*],*Ts*,*D*[*s*i*g*](*T*)\]  

where *Tn*: Transaction, *T*\_*id*: Transporter ID, *Ts*: Timestamped, *D*[Sign]*(T)*: Digital signature of the transporter.

***Manufacturer environment:*** The manufacturer registers first and is assigned with *M*\_*id*. When they sign in, they can interact within the virtual environment. A blockchain is created when the manufacturer enters the environment. All the customer records are stored in the block and linked in a blockchain. The blockchain creation for a manufacturer is shown in Equation 3.

(3)  

*Tn* = \[*M*\_*i*d*,*Ts*,*D*[*s*i*g*](*M*)\]  

where *Tn*: Transaction, *M*\_*id*: Manufacturer ID, *Ts*: Timestamped, *D*[Sig]*(M)*: Digital manufacturer signature.

***Metaverse environment:*** This is the primary immersive environment of the proposed system. All the logistics entities'avatar is created here. The customer inquiry about the condition and location of goods is done. Here, the goods also have their avatar. The manufacturer can request the state and condition of the warehouse, and the transporter can have a video monitoring of the goods while on the road. All data created during the transaction is stored in the blockchain repository.

### Algorithms of the proposed system

Algorithm 1: Activation of customer environment and customer inquiry

| Input: Customer, Transporter, Manufacturer,Output: Activation of Metaverse Environment and Initiation of Customer Logistics Inquiries |
| --- |
| 1: Procedure: Blockchain_LogisticMeta () |
| 2: if (C_ID== True) then |
| 3: Display the avatar of the Customer |
| 4: else |
| 5: Display customer does not exist |
| 6: if (CP= true), then |
| 7: Execute \_contract (for the Customer) |
| 8: Setup Customer Virtual Environment |
| 9: else |
| 10: return to none |
| 10: end if |
| 11: end |

```
if (condVar > someVal) {console.log("xxx")}
```
