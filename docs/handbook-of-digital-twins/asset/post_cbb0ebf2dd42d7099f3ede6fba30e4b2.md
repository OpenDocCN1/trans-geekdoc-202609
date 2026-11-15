
## A Generic Deployment Methodology for Digital Twins – First Building Blocks

Mohammed Adel Hamzaoui and Nathalie Julien

Université Bretagne Sud Lorient

## 7.1 Introduction

Digital Twin (DT) technology gained prominence across various disciplines and engineering fields, peaking in the Gartner Hype Cycle for Internet Technology (IT) in 2019 and ranking third in trending technologies for 2020 (IEEE Computer Society 2019). It has been applied across diverse domains:

- Healthcare: DT is well-suited for healthcare 4.0, with applications in digital patients, pharmaceuticals, hospitals, and wearable technologies (Erol, Mendi, and Dogan 2020). Projects include the Human Brain Project, Brain Initiative, and Blue Brain Cell Atlas project (Erö et al. 2018), along with patient-based simulation models (Sim and Cure 2022), heart DTs (van Houten 2018), virtual humans, hospital department DTs (Siemens Healthineers 2018), and wireless devices for patient observation (Kellner 2015).

- Smart cities and buildings: Cities have developed into smarter cities over the last years as a result of the widespread information and communication technology, utilizing data-driven models and Artificial Intelligence (AI) solutions (White et al. 2021). DTs of cities include Dublin's Docklands (White et al. 2021), Virtual Singapore (Farsi et al. 2020), and Zurich (Shahat et al. 2021). Intelligent buildings use IoT and microsensors for control and efficiency, with projects like the West Cambridge site (Lu et al. 2020) and structural health monitoring (Shu et al. 2019). Building Information Modeling (BIM) has also been used for building DTs given the advantages offered by this tool for the development of digital models in the building field (Kaewunruen et al. 2018).

- Transportation and logistics: DTs have been used in transportation and processing scheduling (Yan et al. 2021), digital shopfloor management systems (Brenner and Hummel 2017), and Automated Guided Vehicle (AGV) transportation (Martínez-Gutiérrez et al. 2021). Applications extend to elevators (Gonzalez et al. 2020), smart electric vehicles (Bhatti et al. 2021), pipeline DTs (Sleiti et al. 2022), traffic control systems (Wang et al. 2021; Saifutdinov et al. 2020), and Adaptive Traffic Control Systems (Dasgupta et al. 2021).

- Energy 4.0: DTs provide disruptive advantages in energy production, transit, storage, and consumption (Karanjkar et al. 2018; Li et al. 2022). Examples include energy consumption optimization for robotic cells (Vatankhah Barenji et al. 2021), energy cyber-physical systems (Saad et al. 2020), energy storage systems for electric vehicles (Vandana et al. 2021), and smart electrical installations (Fathy et al. 2021; O’Dwyer et al. 2020).

- Smart manufacturing: DT applications in industry can be categorized into four phases: design, production, service, and retirement (Liu et al. 2021). Applications range from iterative optimization (Xiang et al. 2019), virtual validation (Howard 2019), automated flow-shop production systems (Liu et al. 2019), autonomous manufacturing (Zhang et al. 2019), Manufacturing Execution Systems (Cimino et al. 2019), start-up phases acceleration (Zhu et al. 2021), optimization of time-based maintenance strategies (Savolainen and Urbani 2021), Remaining Useful Life (RUL) assessment (Werner et al. 2019), and applications in the retirement phase such as disassembly, reuse, disposal, retrospect, and upgrade (Falckas and Karlis 2021).

In summary, DT technology has been applied across various domains, including healthcare, smart cities and buildings, transportation and logistics, energy management, and smart manufacturing. The wide range of applications and ongoing research showcase the adaptability and potential of DT technology in addressing a multitude of concerns and improving the efficiency and effectiveness of systems across these sectors.

## 7.2 The Digital Twin, between the Quest for Diversity and the Need for Standardization

The DT represents a multifaceted technology, encompassing a range of tools and addressing various concerns and application areas. To strike a balance between adaptability and structural robustness, it must employ different descriptive models, adhere to well-defined standards, and utilize efficient development and deployment methods. In the following sections, we will discuss the key models and standards that offer a comprehensive and synergistic understanding of the DT concept. In order to cover all these models, a generic and standardized approach is necessary to be able to define, implement, and bring to life the different DTs specific to the various applications; this is precisely the object of this paper.

### 7.2.1 The Reference Architecture Model Industrie 4.0 (RAMI 4.0)

This reference architecture model was developed by the German Electrical and Electronic Manufacturers’ Association (ZVEI) to support Industry 4.0 initiatives, and is defined by its creators as follows: “consists of a three-dimensional coordinate system that describes all crucial aspects of Industrie 4.0. In this way, complex interrelations can be broken down into smaller and simpler clusters” (Hankel and Rexroth 2015).

The first axis, “Hierarchy Levels” from IEC 62264, encapsulates various factory functionalities. The second, “Life Cycle & Value Stream,” is grounded in IEC 62890 for lifecycle management. The third axis, “Layers,” deconstructs a machine into organized attributes. Although this model significantly contributes to Industry 4.0 organization, its generic nature doesn’t specifically address DTs as a unique technology. For effective DT development and deployment, employing more specialized methods may be necessary.

### 7.2.2 The Five-Dimension Digital Twin Model

Tao et al. (2019) suggested a paradigm in their book to explain the DT technology. This model is made up of five main parts that each reflect one of the key characteristics of a DT. The proposed model is an expansion of the Three-Dimensional DT model that Grieves initially introduced in 2003 in his product lifecycle management (PLM) course at the University of Michigan (first mentioned in the literature in Grieves (2014)).

In addition to the three dimensions of Grieves’ model – physical element, virtual element, and data and information – two more dimensions were added by Tao et al. (2019), as indicated in expression (7.1):

```
M_DT = (PE, VE, S_S, DD, CN) (7.1)
```

The Physical Entity (PE) represents the real-world object, while the Virtual Entity (VE) consists of an assortment of models (Tao et al. 2019). Services (S_s) cater to both entities, and Data (DD) comprise the information that drives the DT. Connections (CN) link the various DT components. This model effectively embraces the DT’s wider aspects. S_s standardizes and packages DT functions, facilitating convenient and on-demand utilization.

### 7.2.3 ISO 23247 – Digital Twin Framework for Manufacturing

A general development framework that may be instantiated for use in case-specific implementations of DTs in manufacturing is what this ISO standard series attempts to provide (International Organization for Standardization 2021). The standard is divided into four sections: (1) overview and general principles, (2) reference architecture, (3) digital representation, and (4) information exchange (Shao 2021). These four sections include instructions on how to define goals and scope, examine modeling needs, encourage the use of common terminologies, construct a general reference architecture, assist information modeling of OMEs (Observable Manufacturing Elements), and synchronize information between a DT and its OME (Shao 2021).

### 7.2.4 The Digital Twin Capabilities Periodic Table

The Digital Twin Capabilities Periodic Table (CPT) focuses on use case capability needs rather than technology (Pieter 2022). Developed by the Digital Twin Consortium (DTC), a global ecosystem, it clusters capabilities around similar characteristics and addresses overall requirements, platforms.

The CPT proposal, while promising, is incomplete as it doesn’t provide organization guidance for DT capabilities, relying on external expertise for DT development. A structured proposal with a clear process and hierarchy for capability implementation is necessary.

These models and standards allow a good formalization of the DT concept, and set the basis for a good handling of this technology as well as its integration in the migration process toward Industry 4.0 and digital revolution in general. However, it is still necessary to develop a generic methodology for the development and deployment of this technology whatever the application domain and the uses dedicated to it. It is this concern that we are interested in, since we propose through this chapter a generic methodology of development and deployment of the DT, articulated on several successive levels of abstraction.

## 7.3 A Generic Development and Deployment Methodology

There are a plurality of definitions of what should be a DT, and that varies along with the service, the granularity, the application domain, the technical focus and the actors (Boschert, Heinrich, and Rosen 2018; Kritzinger et al. 2018). The DT frequently has a pre-defined simulation model as its only option. The real interests and difficulties of DT, however, lie in the
