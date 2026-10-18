
blockchain technology could be a solution to provide more security options to federated learning.

In this chapter we discuss the major data security attributes and the regulations and policies regarding personal data, as well as how federated learning contributes to AI models regarding those regulations. Then we provide a full description of federated learning, its types, and its techniques. That is followed by the current challenges and opportunities facing federated learning. In this section, we discuss how blockchain technology could be a factor to address those challenges. Finally, we provide our use case and the conclusion of the chapter.

## 12.2 DATA SECURITY AND FEDERATED LEARNING

Data security [5] is defined as the process of securing and protecting private and public sectors data and preventing them from data loss, data tampering, and unauthorized access. This represents the CIA triad, which consists of data confidentiality, integrity, and availability.

1. *Confidentiality*: Confidentiality refers to the effort to keep data private or secret from unauthorized parties. To ensure the confidentiality of the data, methods to control the data confidentiality include role-based access control (RBAC), volume/file encryption, file permissions, and encryption of data.
2. *Integrity*: This is a fundamental part of the CIA triad and is intended to protect data from deletion or alteration from any unapproved access, and it guarantees that, when an approved individual provides an incorrect update, the harm can be remedied. So it is very important to ensure that the data is secured from both ends, in terms of modification and deletion so that the data can be trusted.
3. *Availability*: This principle refers to the availability of the data, systems, and applications to authorized parties. Availability should be always consistently and readily accessible, whether impacted by either hardware, software, network failure, human error, or cyber attack. Redundancy for the servers and network, system upgrading, backup and recovery systems, and fault tolerance are methods that could be used to ensure data and applications. Intrusion detection systems, hashing, encryption, authentication systems, digital signature, and access control are all methods that can be used to maintain data integrity.

Seven principles of the GDPR specify the rules that each company or individual needs to follow in order to deal with customers’ personal data. Following [6], the principles are as follows:

1. *Lawfulness, fairness, and transparency*: The term lawfulness refers to the reasons for processing personal data, meaning that all information related to the usage of the data should be well-defined and specific. Fairness and transparency go hand in hand with lawfulness, meaning that organizations shouldn’t withhold information about what data they are collecting or why. They should be clear to the data subjects about their identity and why and how they are processing their data.
2. *Purpose limitation*: Data should be collected only for a specific reason. The purpose of processing the data needs to be well-defined to the data subjects.
3. *Data minimization*: Data users should only collect the smallest amount of data needed to complete the processing. There should be a reason to ask for specific data. For example, there is no need to ask for a phone number or address if it’s not related to the data processing.
4. *Accuracy*: It’s up to the organization to deal with data accuracy. Any data stored incorrectly or incompletely should be corrected, updated, or erased.
5. *Storage limitation*: There is a need to justify the time span during which the data is being stored. Data retention shouldn’t occur if there is no longer a need for the data.
6. *Integrity and confidentiality*: Like the CIA triad, the GDPR requires all data users to maintain the integrity and confidentiality of the collected data and to ensure its security from unauthorized access.
7. *Accountability*: This last principle means that the GDPR requires a level of accountability for all organizations. It signifies that documentation and proofs should be associated with the data processing principles. At any time, supervisory authorities can ask for this documentation.

The CCPA principles [4] are as follows:

- Consumers have the right to access all the data that an organization collects about them.
- Consumers can choose to not have their information sold to third parties.
- Consumers can demand that an organization delete their personal data.
- Consumers have the right to know to whom their data has been sold.
- Consumers have the right to know the reason for the data collection.
- Consumers can take legal action without proof of damages if they are subjected to a breach of privacy.

In all those regulations, federated learning [7] was introduced. Privacy is one of the essential properties of federated learning. This requires security models and analysis to provide meaningful privacy guarantees. The interest of federated learning is to mutually train a global model without directly sacrificing data privacy. In particular, it has provided significant privacy advantages compared to a data center training on a dataset.

## 12.3 FEDERATED LEARNING CONTEXT

In the classic centralized learning, we have data centralized in a server that is sent to a model for training. We have spent decades using that technique until we were presented with federated learning. Federated learning (FL) [8] is a machine learning method where distributed clients, such as edge devices or organizations, mutually train a model under the coordination of a central server (e.g., service provider), while keeping the training data decentralized. It embodies the principles of focused collection and data minimization and can mitigate many of the systemic privacy risks and costs resulting from traditional, centralized machine learning. Federated learning conducts machine learning in a decentralized approach [9]. It aims to provide the model to the data rather than the traditional way, in which we create a model and then provide the data. The data is distributed among different users in their edge mobiles. Each one provides its own data to train the model, leading to multiple unique training datasets rather than just one.

Only the metadata is returned to the centralized model or the global model using encrypted communication. At the same time, this provides knowledge performance for the model and enhances data privacy, since all the calculations happen within the owner’s device without any exchange of its data to a centralized server.

It is important to not confuse federated learning with distributed learning. They both follow the same schema for training models by using a distributed node for the data and a centralized server for the model. However, the main differences arise from the data assumptions: Distributed learning uses parallelism to enhance computational power for additional training productivity, whereas federated learning, using encryption, focuses more on conserving data privacy.

### 12.3.1 Type of Federation

Federated learning is divided into mainly two types based on the most used approach: data-driven and model-driven ([Figures 12.1 and 12.2](#)).

![](img/efffc69cb8cda75bcf341884e3396898_272_0.png)

1. Sending Encrypted Gradients
2. Secure Aggregation
3. Sending Back Model Update
4. Updating Model

- High-performance Global Model
- High-performance Local Model
- Data A
- Data B
- Data C

FIGURE 12.1 Model-centric federated learning.

![](img/efffc69cb8cda75bcf341884e3396898_273_0.png)

FIGURE 12.2 Data-centric federated learning.

#### 12.3.1.1 Model-centric Federated Learning

This is the more common of the two types [10]. In model-centric, the model is hosted in a cloud service, and its API is preconfigured (layers, weight, etc.). Each individual downloads the model, enhances it, and uploads a newer version. But this could happen over a long period of time, frequently weeks and months. A great example is Google’s GBoard mobile app. It learns users’ typing preferences over time without sending any private data. The learning is distributed and happens remotely, updating a central model through a suitable federation technique.

#### 12.3.1.2 Data-centric Federated Learning

Less common than model-centric but more suitable for experimentation science, data-centric is hosted inside a cloud server not as a model but as a
