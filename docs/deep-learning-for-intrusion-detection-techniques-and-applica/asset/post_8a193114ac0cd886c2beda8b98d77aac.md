
Instances, information about certain protocols may be incomplete or unclear, posing challenges for IDSs to conduct accurate analyses. These methods come with drawbacks, including the need for complex analysis and substantial resource consumption as they track multiple sessions simultaneously. Additionally, stateful protocol analysis systems may not identify certain types of attacks that align with expected protocol behavior, such as DoS attacks involving numerous normal actions executed within a short period.

Another limitation is the potential variance in the implementation of the model, depending on the operating system version or the type of client/server in use.

## 1.1.4.3 Intrusion Detection Approaches

- IDS based on statistics.
- IDS based on rule.
- IDS based on heuristics.
- IDS based on pattern.
- IDS based on cloud.
- IDS based on machine learning.
- IDS based on deep learning.

## IDS Based on Statistics

A statistical-based IDS functions by observing regular transactions to establish an authentic profile, identifying deviations from this profile as potential attacks. Each transaction is assigned a score measuring its deviation from normal traffic, triggering an alarm when the score surpasses a predetermined threshold value. This threshold is determined based on the count of events within a defined timeframe, considering various packet metrics like mean, median, mode, and standard deviation. The IDS monitors each packet individually to detect deviations from the expected flow, tracking the flow fingerprint rather than examining data traffic content.

Statistical IDS techniques can be categorized into three main types: time series, multivariate, and univariate.

### a) Univariate:

This technique focuses on analyzing data with a single variable, creating a normal profile based on that metric. Univariate IDS identifies anomalies by detecting abnormalities in each individual metric.

### b) Multivariate:

This model analyses relationships between two or more measures, proving useful when analyzing correlated measures together enhances classification. Challenges in the multivariate approach include difficulty in estimating distributions for high-dimensional data.

### c) Time Series:

Time series involves a sequence of measurements taken over a specific time period, considering an observation unusual if its likelihood of occurring at that time is exceptionally low.

Statistical-based IDS offers benefits, such as detecting previously unknown attacks without relying on signatures, simplified maintenance without frequent updates, and effectiveness in detecting DoS and DDoS attacks. However, drawbacks include the time required to create a legitimate profile, potential changes in the legitimate profile over time, and the necessity for accurate and effective statistical distributions to ensure precision and efficiency.

## IDS Based on Rule

An IDS utilizing a rule-based approach employs pre-established rules to recognize potential intrusions within network traffic. These rules can be perceived as patterns, created through artificial intelligence techniques based on attack patterns. Unlike signature-based IDS, which demands thousands of signatures to detect various attacks, a rule-based IDS can identify multiple attacks using a single rule. This approach requires fewer rules in comparison, making the management of the IDS simpler. Furthermore, this system is adept at identifying new attacks, as alterations in attack patterns may not be significant enough to completely change intrusion patterns. Employing multiple rules in an IDS might be necessary to ensure the identification of all potential network attacks.

## IDS Based on Heuristic

The heuristic-based IDS operates by recognizing malicious behaviors, establishing a model for detecting acceptable behaviors, and flagging any deviations. This approach depends on knowledge and experience to effectively distinguish between normal and attack behaviors. Analysis of collected execution traces is conducted to identify suspicious patterns, triggering an alert upon detection. This method is capable of identifying both unknown (zero-day) attacks and known attacks, with the ability to discover and include new attack types in the list of malicious behaviors. However, the heuristic engine may be susceptible to evasion by certain attacks employing hiding techniques.

## IDS Based on Pattern

The IDS employing a pattern-based approach identifies attacks by extracting characters, strings, and structures from collected data to recognize significant patterns. This approach specifies the malicious instruction sequences in attacks, and the identified patterns within the IDS are termed signatures. While the pattern-based approach is adept at swiftly and effectively detecting known attacks, it is less efficient in identifying most zero-day attacks due to the unknown nature of their patterns or signatures. The implementation of a pattern-based detection system is straightforward. Pattern-matching algorithms are categorized as multiple pattern matching and single pattern matching.

The multiple pattern-matching algorithm is considered more efficient than the single pattern-matching algorithm as it eliminates the need for scanning the packet multiple times. However, the multiple pattern-matching algorithm requires high processing and memory time.

## IDS Based on Cloud

Cloud computing technology offers efficient delivery of online services with advantages such as 24/7 data access, pay-as-you-go, and cost reduction. It encompasses three primary service categories: IaaS (Infrastructure as a Service), PaaS (Platform as a Service), and SaaS (Software as a Service). IaaS provides infrastructure resources like networks, computing devices, and storage, PaaS offers a platform for utilizing various algorithms, and SaaS enables users to perform tasks online. Building IDS in cloud environments has multiple benefits, allowing the detection of malicious network actions from diverse viewpoints and overcoming limitations of traditional intrusion detection methods. Public and private clouds enable simultaneous detection of various network attacks with high efficiency.

The IDS based on cloud technology comprises three main components: the user's data collector, the cloud IDS, and the cloud service. The user's data collector gathers network packets, which are then sent to the cloud service for filtering, standardization, and validation. The cloud service processes and standardizes the collected data before transmitting it to the cloud intrusion detection component. This component includes an analysis engine, a signature database, and a service console. The analysis engine examines packets to detect intrusions. Although this approach is in its early stages, future integration with IDS is essential to enhance model performance.

## IDS Based on Machine Learning

Machine learning (ML) involves the automated analysis of data using algorithms, eliminating the need for human intervention. It encompasses various methods, including unsupervised learning that utilizes unlabeled data, supervised learning that relies on labeled data, and semi-supervised learning, which combines both labeled and unlabeled data [16]. These methods aim to automate the data analysis process through algorithmic approaches. In the realm of intrusion detection, the application of ML is a recent development, with numerous algorithms and techniques available for IDS. Examples include support vector machines, k-nearest neighbors, Bayesian algorithms, neural networks, genetic algorithms, decision trees, and fuzzy logic.

Machine learning methods, empowered by training data, can recognize intricate patterns due to their advanced pattern-matching capabilities. ML involves the extraction of insights and knowledge from large datasets. ML models encompass a collection of techniques, procedures, or intricate transfer functions that can be employed to identify significant patterns in the data or predict behaviors.
