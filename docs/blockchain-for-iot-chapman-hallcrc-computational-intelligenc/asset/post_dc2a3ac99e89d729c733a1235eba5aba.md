
![](img/73e16681f7c79384b117f947ee8dd11a_225_0.png)

FIGURE 10.2 LoRaWAN mesh topology architecture for crops production.

## 10.3.2 Purification and Normalization of the Acquired Information

The sensors generate the information continuously, and as a result, some of the data may be repeated or irrelevant. To structure the data in a way that will be useful, it needs to be clean and in a correct format so that it easy to understand.

Once the cleaning operation is completed, all the relevant information is distributed at the information warehouse stage. Data should be constructed and well organized, and for this, some information should be included, namely a time stamp, demography, and which kind of data it is (string, number, float, etc.) while performing this operation. Storing data on the Blockchain network makes them more incorruptible and ensures that individually visible data connected with the data obtained from IoT tools are fully preserved and support the protection rules. Figure 10.3 presents the process of cleaning the data. First all sensor data from different stages are imported, and anything duplicated or irrelevant removed. Data are ready and reconditioned to get normalized. After the data are normalized, the testing is started to export the data for use. When the collected information is improved, it is put into ML models for training and testing.

## 10.3.3 Gathering More Specific Knowledge through Machine Learning

The cases that will be used for building the model are crop classification support, crop recognition, crop submit forecasting, crop spreading measurement score, and crop market request forecasting. Using the ML algorithm of the captured data the farmers and stakeholders will be able to increase productivity and enhance the watering operations [39]. Storing data in the Blockchain network will allow agriculture contributors (farmers, suppliers, packagers, and resellers) to acquire such data explicitly. The flow diagram in Figure 10.4 shows how a ML algorithm will work for the crop production–related forecasting. For classifying several crops’ temperature, soil-related data for predicting a data mining procedure are important. The analysis of this agriculture data using different data mining techniques is easily achieved. The algorithm includes K for clustering and fuzzy c for forecasting [40]. Using multilayer perceptron as deep learning neural network, a time series prediction is created for weather forecasting, selling of crops, and warehousing distribution. For performing overall production of food in industries it uses modern processing method based on genetic algorithm and statistical methodology as Bayesian network [41].

![](img/73e16681f7c79384b117f947ee8dd11a_227_0.png)

FIGURE 10.4 Process to train and test the data of food production using machine learning.

## 10.3.4 Storing Methodology

After applying an AI algorithm for forecasting food- and crops-related data, the information is saved in the Ethereum file system as a shared storage policy with hashing address on the blockchain network storage. To make the system more cost efficient, other Blockchain file system also can be used if and as required.

![](img/73e16681f7c79384b117f947ee8dd11a_228_0.png)

FIGURE 10.5 Storing and accessing of data in Blockchain.

With the use of a Blockchain network, the information is shared across each node in the network block as a peer-to-peer (P2P) connection, which means it does not need any central administration to manage the system. Figure 10.5 shows how the information is stored in the Blockchain network, and how the users participate in such a network. The data captured at different stages for food and crops production in the Blockchain can be accessed only after execution of a smart contract or managing controls established between them. Smart contracts support the interchange of information saved on each block among the network participants. This means data will be accessible to each agriculture store candidate associated with this network. In the distributed computing layer, all Blockchain-related operations will be performed, including transactions, consensus, security, and more. In the security section every transaction will have its hashing key, which is very difficult to decrypt. All transaction will be displayed as ledger in the Blockchain network, which will be available to all participants who are involved in this network.

## 10.4 COMPARATIVE ANALYSIS BETWEEN PROPOSED METHOD AND EXISTING METHODS

Table 10.1 presents a comparative analysis between the proposed method and the previously extant methods. The parameters compared include: the design system device; data protection, cost efficiency; intelligent system design; and the use of AI, IoT, and Blockchain. The analysis has determined that the proposed methodology supports ML, IoT, and Blockchain.

| Reference | Methodology | Protected | LowCost | Intelligent System | Support AI/ML/IoT/Blockchain |
|---|---|---|---|---|---|
| Mondal, S., Wijewardena, K. P., Karuppuswami (2019) [20] | RFID-based food supply chain traceability using blockchain | Yes | Yes | No | AI/ML: No, IoT: No, Blockchain: Yes |
| Nurzaman Ahmed, Debahis De (2018) [21] | Smart wireless sensor network architecture designed for farming and agriculture using IoT Fog computing | Yes | Yes | No | AI/ML: No, IoT: Yes, Blockchain: No |
| M. P. Caro, M.S. Ali (2018) [22] | Traceability of food supply chain using Blockchain IoT | Yes | No | No | AI/ML: No, IoT: Yes, Blockchain: Yes |
| Pranto T.H., Noman A., Mahmud A (2021) [24] | Smart agriculture system using IoT and Blockchain | No | No | No | AI/ML: No, IoT: Yes, Blockchain: Yes |
| M.S. Shyamala Devi, R. Suguna, Aparna Shashikant Joshi (2019) [27] | Smart agriculture system design for safety and security using IoT Blockchain | Yes | No | No | AI/ML: No, IoT: Yes, Blockchain: No |
| Tian, F (2016) [29] | A RFID- and GIS-based system design for food supply chain traceability using Blockchain | No | No | No | AI/ML: No, IoT: No, Blockchain: Yes |
| Chen, W.L.; Lin, Y.B. ;Lin(2019)[31] | Soil cultivation system design using IoT | No | Yes | No | AI/ML: No, IoT: Yes, Blockchain: No |
| Proposed Method | Crops production and food traceability using IoT Blockchain and machine learning | Yes | Yes | Yes | AI/ML: Yes, IoT: Yes, Blockchain: Yes |

Comparing the proposed method with the extant ones shows that the proposed methodology is using IoT with Blockchain in which ML is being used in middleware to preprocess the sensor data so that imported data can be more knowledgeable and accurate. Table 10.2 shows that no other existing method can currently achieve the same.

TABLE 10.2 Comparative Analysis between Proposed Method and Existing Methods in the State of Technologies

| Technologies/Methodology | Proposed Methodology | Previous Related Work by Mondal, S., Wijewardena, K. P., Karuppuswami in (2019) [20] |
| :--- | :--- | :--- |
| IoT sensors used for crops production: temperature, water, soil, fire alert | Yes | No |
| IoT data communication devices at the network layer as ZigBee, LoRaWAN for crops production, warehouse distribution, and food market | Yes | No |
| IoT devices, such as Bluetooth Beacon, used for food traceability and supply chain | Yes, Beacon Bluetooth is used with each food product to monitoring in real time food distribution from warehouse to consumer | No, RFID is used for supply of food |
| Network application used (LoRaWAN app server) | Yes | No |
| Artificial Intelligence used for making data knowledgeable and accurate of crops production, warehouse distribution, and food market | Yes, machine learning-based algorithms are used, such as clustering, Bayes’ theorem, and time series prediction for making data filterable and knowledgeable | No such intelligence system has been used |
| Blockchain network for storing all data, distributed ledger of crops production, warehouse distribution, and food market. | Yes, Ethereum is used to create a smart contract with all farmers and consumers who are connected to this network. It is easy-to-use, secure technology. IoT devices data are linked with the IoT device. Machine learning is used as middleware for data filtration. | Blockchain network is used only for food supply chain but not linked with the IoT device. There is no clarity of which Blockchain network is used to transmit the RFID data. |
