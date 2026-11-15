
Foundation Classes (IFC) is used to integrate building information models (BIM) as 3D geometric and georeferenced entities among other data sources through distributed systems. Hence, cloud computing and IoT-based services such as real-time sensor data acquisition and distribution provide interaction and communication with end-users, bridging connections between humans and urban environments.

### 25.4.1 Information Management and Digital Thread

Currently, the BIM model plays a relevant role as a data source (Bojé et al., 2020) and geometrical information model for building, infrastructure and asset management (Lu et al., 2019). However, much of the information and data generated across the lifespan goes unused or missed, and only a limited amount of data is transferred to the next stage. That’s why data sources need to be more connected and integrated in order to properly address the information management challenges in the built environment (Bojé et al., 2020).

Digital thread and simulation are concepts relatively close to, because it integrates real-time data and synchronization, simulation, process monitoring and control, diagnostic and predictive capabilities moving forward to real-time data analysis (Schleich et al., 2017).

As such, the digital thread concept is related to the system development lifecycle (SDLC), which involves the entire lifecycle of the asset from planning to design, construction, operation and maintenance (Singh and Willcox, 2018). Hence, digital threads can generate insights from the entire lifecycle process and enhance predictivity, decision-making and traceability.

Hence, the digital thread of data allows DTs to collect, manage and use data from the pre-project stage to the end-of-life of the physical object, as a tool to use connected information safely and effectively from design to operation and maintenance. Then data related to every component and sub-component of the real-world object needs to be trusted, accurate and reliable as well as structured correctly and consistently, in order to maintain it across the entire lifecycle and raise the value of DTs (Dawood et al., 2020).

In this regard, Grieves evidences fallacies in the concept of DTs only existing until physical counterparts are created. Duality and strong similarity are the only requirements for a DT as an existing model related to some point of the asset’s lifecycle. As such, it can exist prior or even after the physical counterpart as the actual existence of a physical object is not a strict requirement, but its intended realization is the key differentiator of DTs from digital models (Grieves, 2022).

As such, a DT is composed of a repository which stores and links data, keeping an audit trail and maintaining its current record. This feature is related to the concept of golden thread of data and information. The concept was derived from the business world as a metaphor for organizational strategies and the UK Government introduced it in the construction sector in 2016 within the BIM mandate and with a more recent report by the UK Ministry of Housing, Communities and Local Government. The concept of transferring critical information from one stage to another is essential and it ensures a full understanding of the project by the stakeholders. In addition, it allows avoiding costly re-works in discovering information which had been already generated during the previous stage.

A huge amount of data and information are generated, combined, managed and used across the lifecycle and its complexity requires a robust information management process. In fact, the main inefficiencies in the management process of the built environment are related to fragmentations.

An information management framework is essential in order to properly apply DT strategies in the construction sector, as it has been defined by the CDBB as a “formal mechanism to ensure that the right information can be made available at the right time, to the right people and that the quality of the information is known and understood, is required”.

As defined by the ISO 19650 series related to BIM implementation (Tang et al., 2020; Eastman et al., 2011), smart buildings and information management in construction, the need of defining structured processes is essential in order to embed and integrate data over the object lifecycle as a virtual replica. In this regard, Table 25.2 shows how the information management process and digital thread are structured in the construction sector through agreed data standards handling real-time, as-built and performance data (sensor data, IoT, point clouds, etc.). Actually, the amount of “dark data” is around 95% of data produced over the lifecycle of an asset which goes unused.

As mentioned above, digital models can replicate different stages or processes of the assets like historical, current or forward-looking states, while integrating data along temporal dimensions is the main objective of more mature DTs. Digital Thread is a tool for integrating data and information across multiple dimensions based on solid and substantial real-world identifier, ensuring the effectiveness of configuration management capabilities, recording historical, intended, or real-time configurations enabling a sort of “configuration history” dimension. Hence, Digital Threads are composed of identifiers and the software component which allows cohesive state views of information about product, systems or processes.

Identifying the key capabilities for each stage of the virtual replica is essential as they may differ in terms of technology and intended outcomes throughout the lifecycle. Capability is defined as “the ability to perform certain actions or achieve certain outcomes” and in the DT domain some capabilities may change across the lifespan, becoming obsolete or being renewed (e.g., capabilities related to the construction stage may not be similar to the operation and maintenance stage of a HVAC plant). The clear identification of capabilities enhances the development of the digital thread throughout different lifecycle stages.

In Table 25.2, the main components of digital thread and information management processes in the built environment are shown.

### TABLE 25.2 Digital Thread and Information Management in Building Lifecycle

| Phase | Outcome | Digital Thread Lifecycle Data | Model |
| --- | --- | --- | --- |
| Plan | Simulation and what-if scenarios<br>Optimized configurations<br>Procurement | As planned<br>Customer data<br>Demand data<br>Design specifications | Systems |
| Design | Simulation and what-if scenarios<br>Asset/district/city modelling<br>Maintenance simulations and improved operational efficiency | As designed<br>Customer data<br>Demand data<br>Design specifications | Time series data and models |
| Construct | Site-based process management<br>Prefabrication and industrialized construction<br>Production management<br>Supply-chain management<br>Data and information management | As constructed<br>Process data<br>Planning data<br>Real-time status data<br>Capacity data<br>Class library | Meta or master data<br>Services |
| Commission | Compliance<br>Design verification | As commissioned<br>Certifications<br>Class libraries | Business systems data |
| Operate | Optimization<br>Simulation and what-if scenarios<br>Safety<br>Real-time monitoring | As operated<br>Operational data<br>Energy data<br>Status data<br>Behaviour data | Physics models<br>Sensors |
| Maintain | Prescriptive maintenance<br>Predictive maintenance<br>Condition-based maintenance | As maintained<br>Historical fault data<br>Time series data<br>Spare parts data | Analytic and visual models |
| Retire | Decommissioning | As retired<br>Operational data | |

### 25.4.2 Digital Twin Architectures

DT architecture is the main core of DTs (Aheleroff et al., 2021) as a reference model which deconstructs complex relations and hierarchies into simple clusters, layers or blocks (Kritzinger et al., 2018). Multi-tier architectures have been proposed in literature in order to support DT environments making data accessible (Wärmefjord et al., 2017; Zhuang et al., 2017), integrated and usable through CPSs, IoT and big data platforms (Silva et al., 2020). A multi-tier architecture is based on dividing the main components into a set of independent layers (Terrazas et al., 2019) sorted according to logical and functional aggregations, communicating with the adjacent layers and deriving functionality only from the lower layer.

As a result, layers act as a whole and independent component in a modular system architecture and components could be used as services within other layers, resulting in simple and traceable data flows.

In order to acquire relevant information from the physical world, connection layers are implemented as a direct thread to physical assets or sensors. Bluetooth, near-field communication (NFC) and RFID are some of the network layers’ components which are implemented to transfer data from connection layers to processing layers. Upper layers are defined according to different application uses.

CPSs architectures are based on the interaction between machines and human beings integrating ICT, sensing and control capabilities, while IoT architectures (Oliver et al., 2018) are based on big data and cloud computing technologies.

In summary, a hierarchical and flexible architecture needs to be developed for data collection and acquisition across the lifecycle of assets, buildings and cities. Moreover, computational capabilities and information management are essential in order to manage a great amount of multidomain data. Also, the human communication and interaction layer plays a relevant role as data or condition status helps users in monitoring as-is feedbacks.

### 25.4.2.1 Data Acquisition and Ingestion Layer

The data acquisition layer is essential in the DT architecture for the built environment considering the huge number of heterogeneous sources and volume of datasets. In this scenario, defining clear information requirements is necessary to properly understand the needs of DT users during the entire asset lifecycle according to The Gemini Principles, as well as collecting data and maximizing their cost-effective value.

Hence, the adoption of distributed sensor techniques at an urban scale is gradually increasing especially for infrastructure, power grids, telecommunication networks, etc.; IoT and micro-electromechanical systems (MEMS) are used at building scales.

According to the Federation Principle, DTs are a federated amount of shared data from interconnected DTs in a common architecture where data are accessible, integrable and federated.
