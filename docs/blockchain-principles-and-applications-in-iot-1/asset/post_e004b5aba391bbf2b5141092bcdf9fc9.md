
blockchain in the healthcare field for data storage, security, and retrieval. In the next section, let's have a look at the healthcare system first, then the role of machine learning and blockchain in it.

## 8.3 About Healthcare Informatics

The healthcare domain is one of the fastest-growing fields of informatics and is creating many opportunities for healthcare and IT professionals. The past decade has shown incredible growth for the field of healthcare informatics, transforming from old-fashioned paper-based medical records to electronic health records. Of course, the adoption of electronic health records, with advancements in cloud storage and analytics capabilities, has led to greater availability (and share-ability) of healthcare data. Healthcare informatics applies principles of computer science and information science to improve the quality of life science research, advancements in public health, health education and public. It is a multidisciplinary field that involves computer, cognitive and social sciences. In healthcare, tools and technologies of informatics are used for providing better health services. Further, this data is available in text, image, signals, and many other formats for future reference and shareability. In the upcoming sections, various AI-based sub-domains are encapsulated to perform various smart tasks for better outcomes. A relatively new specialty in health care, health informatics has transformed how the field operates, which will have larger implications across clinical care, health management, disease prevention, and health policy. While some of these results cannot be foreseen, there are indicators of how health informatics will revolutionize health care across those three disciplines (clinical implications, security implications, and policy implications).

## 8.3 Role of Blockchain and Machine Learning in Health Care

### 8.3.1 Blockchain for securing medical data

Although blockchain was introduced for financial industry transactions, its scope is not limited. This chapter deals with healthcare application of blockchain technology. Healthcare informatics takes care of hospital, medical, and human health records at an industrial scale. Human health activities are observed under the supervision of healthcare professionals. Usually it is observed in standard operations that treating facilities do not trust patient's clinical history and previous third-party dealing. There are many technical and logical issues, which seem to be apparent and reasonable. When situations are critical and a complete history remains unknown to a new healthcare worker, it becomes a matter of life and death for the subject under observation. On the other side, if the same history remains available in a (safe, secured) centralized server, the life of a patient becomes easier in multiple dimensions. Blockchain concept applications in healthcare informatics and promising features that may lead us to the next generation of automation. Blockchain features that are uniquely beneficial for this application are immutability, decentralization, enhanced security, distributed ledgers, consensus, and faster real-time updates. In [25,26], the author has shared the research scope in health care with blockchains. We are discussing here the procedure of keeping patients' records secure along with machine learning for data analysis purposes.

### Blockchain for Patient Management

In due course of time, we shall be able to see the application of the mentioned technology in the healthcare sector in a broader sense, and it will reduce the manual task by creating a block of patient that includes all previous health details, their updates, along with treating healthcare professional particulars with provided analysis reports, prescriptions, third-party guidance, and so forth. The patients have to deliver only a code that shall be provided by the hospital network node (Figure 8.2) or possibly a signature like a fingerprint or retinal scan.

Figure 8.2 explains the aforementioned situation. This figure represents the network of hospitals where two types of nodes are present i.e. validator node and member node. Following are the steps that will be applicable on a network in the presence of blockchain technology:

- 1. In a blockchain network, a node is just a machine or a computer having required software/hardware specifications to become a node/member of network. Hence, a machine with required specifications registers for node or member of hospital network.
- 2. After becoming a member, a member node has a right to initiate or receive blocks or data related to patients back and forth to other members (hospitals).
- 3. After receiving any block, a validator node validates it (the correctness of data) and adds it to its centralized ledger (with the help of consensus protocol, validator node take decision).

These above-stated steps are for a blockchain network. Now, a patient's scenario comes in the picture and that is how a patient's data will get created and sent to the concerned hospital or supervisor. Figure 8.3 uses a case diagram to explain the scenario when a patient visits the hospital for the first time. Following are the steps:

![](img/accfea9a01c34cc061afd3c9ae34e481_141_0.png)

- Miners (validator node) can initiate/receive and validate transactions
- Member node can initiate and receive transactions only

FIGURE 8.2
Hospital network (P2P connection).

## Blockchain

Hospital 'A' of hospital Blockchain Network

![](img/accfea9a01c34cc061afd3c9ae34e481_142_0.png)

![](img/accfea9a01c34cc061afd3c9ae34e481_142_1.png)

![](img/accfea9a01c34cc061afd3c9ae34e481_142_2.png)

Block has been initiated and send to validator nodes.

![](img/accfea9a01c34cc061afd3c9ae34e481_142_3.png)

![](img/accfea9a01c34cc061afd3c9ae34e481_142_4.png)

Block has been generated and hash (in terms of fingerprint or id) has been assigned

FIGURE 8.3
Block creation at the time of registration.

Fig 1. Patient provides their personal details and symptoms.
Fig 2. Hee prescription accordingly. All these details will be added into the block of subject.
Fig 3. Based on this data, encrypted hash code will generate that shall be provided to the patient for further access.

The previous steps help a patient to create a block and store their details that will be accessed by authorized persons with the help of a hash code. Now, Figure 8.4 discusses the case when a patient relocates, changes the hospital, or goes for a second opinion (consultation).

Now, the patient has to provide their hash value only to the concerned hospital instead of the entire entries. By entering a hash value, all the details including doctor, contact details, and prescription will be available to the hospital representative. Based on the previous history and current symptoms, a new hash supervisor will be assigned to the patient. Details of the new supervisor along with the prescription will be mentioned and a new block initiated for the patient.

All features of blockchain are taken care when applied in health care. Following are the details of applied features:

- 1. Immutable: Validators first validates the data and then adds it to an existing block whose copy is already there with every node. Hence, it makes data indisputable.
- 2. Decentralized: Group of validator nodes are there to maintain the network that makes it decentralized.

### Blockchain for Patient Management

![](img/accfea9a01c34cc061afd3c9ae34e481_143_0.png)

New block has been generated after entering details.

FIGURE 8.4
Addition of new block in a new hospital.

- 1. **Security**: Encryption algorithms are there to create a hash code for every block that ensures the security of data.
- 2. **Distributed Ledgers**: Record of patients maintains by all other users/nodes of the network as it is distributed.
- 3. **Consensus**: As a core of blockchain architecture, consensus helps groups of nodes to make decisions related to blocks. Here, our approach for consensus protocol is group of health professionals or organizations who define the terms of use.
- 4. **Faster**: Addition and retrieval of data among network is fast.

With the help of the previous illustration, we discuss the role of blockchain that will reduce the human efforts to maintain the health record and provide security with overall system enhancement to that data as well.

### 8.3.1.2 Machine Learning in Medical Science

Machine learning is used for data analysis and prediction purposes with the help of supervised or unsupervised learning algorithms. In supervised learning, a model is trained with a labeled data set [28–31], whereas an unsupervised model is trained with an unlabeled data set used to find the hidden patterns of data, which will help to understand the nature of problem.

These mentioned ML algorithms help a lot in the medical field by maintaining the health record; in the diagnosis of a problem, drug discovery and development and last not the least for treatment and prediction of disease [21–23].
