
-   ii. **Communication overhead:** A further expense of federated learning is the increased communication that is necessary across the many organizations engaged in order to convey model changes and aggregate them. Particularly when working with big, high-dimensional datasets, this communication overhead can be a significant factor. Methods like model compression, quantization, and selective participation can be applied to this issue.

-   iii. **Ethical and legal considerations:** Due to the fact that federated learning necessitates collaboration between several parties, there are moral and legal issues. Before putting into practice any procedures that are not only legal but also ethical, data ownership, data rights, compliance with laws like the General Data Protection Regulation (GDPR) and the Health Insurance Portability and Accountability Act (HIPAA) must be carefully considered.

iv. **Federated infrastructure management:** Managing the federated infrastructure necessary for federated learning on several datasets that are not physically present in the same location can be challenging. Organizing the involvement of several organizations, establishing secure communication routes, managing updates and synchronization, and other tasks are required to maintain the infrastructure for the collection and dissemination of model information.

To deal with resource limitations and decrease communication overhead, optimization strategies can be used, such as federated optimization algorithms that use optimizing techniques. The ethical and legal difficulties may be resolved in several ways, by establishing explicit data sharing agreements, ensuring compliance with applicable laws, and adopting ethical standards. Federated learning on scattered datasets could be made easier by federated server designs and other effective management and coordination techniques.

The obstacles that federated learning on non-located datasets encounters heterogeneity, data privacy, data security, resource limitations, communication overhead, ethical dilemmas, and infrastructure management, to name just a few. A range of preprocessing approaches, privacy-preserving mechanisms, secure communication protocols, optimization methodologies, and legal practices are needed to get over these obstacles. Several issues must be resolved in order to build and implement federated learning on non-located datasets. Cooperative ML will be safe, private, and trustworthy if this is done.

## 14.4 TECHNIQUES AND BEST PRACTICES FOR FEDERATED LEARNING ON NON-CO-LOCATED DATASETS

To use federated learning on datasets that are not co-located, features like data preprocessing, encryption, secure aggregation, and others must be introduced. In this section, we will examine several federated learning strategies and offer recommendations on the best practices for producing accurate and secure results on geographically scattered datasets, as shown in Figure 14.5.

![](img/a29e06af76c776aadcc01782d636c0d5_349_0.png)

**FIGURE 14.5** Federated learning on non-co-located datasets.

### 14.4.1 DATA PREPROCESSING

In the context of federated learning, data preprocessing is essential, especially when working with disparate datasets. The preprocessing of data can be streamlined using the following methods:

-   *i. *Feature engineering*: Raw data must be transformed into a format that is appropriate for engineering features in order to train a ML model. Feature extraction, dimensionality reduction, and feature scaling are some of the processes included. Each business is free to independently feature engineering on its data while keeping knowledge private.
-   *ii. *Data normalization*: This is essential to ensuring that data from various institutions are measured in accordance with the same standards. The data may be normalized and made more comparable using techniques like max scaling and *z-score normalization*.
-   *iii. *Data imputation*: In real-world datasets, missing data is a frequent problem. Imputation methods like mean imputation and regression imputation can be employed when missing data is to be inferred. Care must be taken to guarantee that imputation is carried out safely and without compromising any personal data.
-   *iv. *Data transformation*: This may be used to spread collections of data that are not physically close to one another in a number of different ways. Converting the data to a standard distribution, the convergence and overall performance of the model can be improved. The use of techniques Log and Box-Cox transformation can provide data normalization and compatibility.

Participating firms may utilize these data preprocessing techniques to guarantee that their data is ready for collaborative model training without jeopardizing data privacy or security.

### 14.4.2 ENCRYPTION

To secure the privacy and confidentiality of the data during the federated learning process, encryption technologies are essential. Any of the ciphering algorithms listed here can be used:

-   i. Homomorphic encryption: The encryption eliminates the need to first decode the data in order to computation on it. Before sending local model updates to the coordinator or central server, entities can encrypt them using their own private key. The server can implement encryption aggregation to protect the privacy of the data by avoiding the raw data.
-   ii. Secure multi-party computation (SMPC): A method known as SMPC enables several participants to compute a function jointly while preserving the confidentiality of each party's unique inputs. Federated learning can employ SMPC to securely aggregate changes. The server executes calculations on the encrypted model updates to create an aggregated model without revealing the specific contributions of the entities.
-   iii. Differential privacy: This fortifies the model-updating process against privacy breaches by introducing a tiny quantity of random noise. Participating firms may “noise” their data with extra information before sending local updates to the network in order to safeguard the privacy of the users. In order to obtain differential privacy, aggregation techniques like the Laplace or Gaussian processes may be used.
-   iv. Secure communication: Employing technologies like SSL and TLS is crucial since data and model changes delivered from one organization to another must be transmitted securely. These protocols include SSL and TLS, for data integrity and privacy can be safeguarded via secure communication, which can prevent data theft or manipulation while it is being transmitted over a network.

By using encryption mechanisms, participating firms may ensure the privacy of data and model changes stored locally during the federated learning process.

### 14.4.3 SECURE AGGREGATION

Secure aggregation is used to maintain the privacy of the data while reaping the benefits of federated learning, as shown in Figure 14.6.

![](img/a29e06af76c776aadcc01782d636c0d5_351_0.png)

FIGURE 14.6 Flow diagram for federated learning with secure aggregation. The following techniques can be applied to ensure safe aggregation:

-   i. Federated averaging: It is a standard method for securely aggregating models. Participating entities submit local versions to a central server, which then combines all into a global model.
-   ii. Secure weighted aggregation: Depending on variables like data quality or entity knowledge, it is essential to give the model updates weights. This ensures that the collective knowledge is accurately represented.
-   iii. Secure learning with trusted execution environments (TEEs): With the aid of TEEs like Intel SGX and ARM TrustZone, computing in a safe environment is now feasible. This opens the door for a method called "federated learning." To enable the secure aggregation of model revisions, TEEs may be utilized by all parties.
-   iv. Privacy-preserving aggregation protocols: While gathering data by using one of privacy-preserving aggregation methods, such as secure or maximum, it is feasible to combine methods without disclosing the unique contributions of individuals. These methods allow the server to compute the total while preserving the privacy of each update.
