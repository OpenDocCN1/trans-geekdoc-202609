

Wang, C., Cai, Z., Li, Y. (2022). Sustainable blockchain-based digital twin management architecture for IoT devices. IEEE Internet of Things Journal. 10(8), 6535–6548.

Yi-Huuomo, J., Ko, D., Choi, S., Park, S., Smolander, K. (2016). Where is current research on blockchain technology? - A systematic review. PLoS One, 11(10), e0163477. DOI: 10.1371/journal.pone.0163477.

Zeadally, S., Abdo, J. B. (2019). Blockchain: Trends and future opportunities. Internet Technology Letters, 2(6), e130. DOI: 10.1002/itl2.130.

Zghaibeh, M., Farooq, U., Hasan, N. U., Baig, I. (2020). Shealth: A blockchain-based health system with smart contracts capabilities. IEEE Access, 8, 70030–70043.

Zhang, C., Zhou, G., Li, H., Cao, Y. (2020). Manufacturing blockchain of things for the configuration of a data-and knowledge-driven digital twin manufacturing cell. IEEE Internet of Things Journal, 7(12), 11884–11894.

## 11 Physics-Based Digital Twins Leveraging Competitive Edge in Novel Markets

Emil Kurvinen
University of Oulu

Antero Kutvonen and Päivi Aaltonen
LUT University

Jussi Salakka
University of Oulu

Behnam Ghalamchi
California Polytechnic State University

### 11.1 Introduction

This chapter focuses on the utilization of technology of physics-based simulation beyond product development and utilizes the digital twin (DT)-enabled approaches. We further draw attention to the product, process, and innovation creation potential of DTs and discuss the managerial implications of such technologies. The concept of the Digital Twin dates back to a University of Michigan presentation to the industry in 2002 for the formation of a Product Lifecycle Management (PLM) center [1], and has since been increasingly adopted by technologically advanced manufacturers globally. During the past decade, the development of physics-based simulation, especially real-time capable dynamic calculations and the methodologies to conduct the analyses have been developed rapidly. Currently, the emergence of virtual machines and real-world machines are actively focused and demonstrations are reported (see, e.g., [2,3]). Subsequently, the literature focused on understanding the operational benefits of DTs from the managerial perspective, such as increasing transparency and aiding in decision-making [4,5], has increased over the decades discussing both industrial applications benefits (further, see, e.g., [6]) and the strategic integration of advanced technologies [7]. Previously, many of the economic theories discussed the potential of augmentation, whereas currently an increasing number of scholars highlight the significance of automation and encourage management to take part in research conducted specifically focusing on intelligent technologies utilization in firms [8]. However, the most common benefit of using advanced technologies in firms is increased product and process innovations as well as ‘world-first’ innovations [9]. Both product and technology development, and utilization of the systematically structured information in the business scenarios can be studied, yet the maturity level of DT defines the achievable objectives along firm-specific factors, such as R&D expenditure, market, and strategy, (see, e.g., [9]).

To introduce the practical advances of DT technology in creating a competitive edge, this book chapter is written based on research work conducted with non-road mobile machinery (NRMM) and high-speed electric machine (HSEM) applications [10], where dynamics modeling and simulation are applied, thereby giving a solid basis to build the DTs on top of the extensive R&D knowledge. In these applications, the final product can be assessed in the virtual domain at high technology readiness level (TRL); for example, in high-speed applications, the controls can be model-based (see, e.g., [11]), i.e., the dynamics model that is used to analyze the machine performance is also used as the basis for the control of the final product. Dynamic modeling is enabling to combine information from design data and verifying the correctness of data as it is fundamentally based on the mass properties of the studied product and its structural stiffness. Experimentally validating the dynamics can be done with modal analysis [12], where the inertia measurement unit, accelerometer, microphone sensors, or laser scanning vibrometer (LSV) [13] are required to capture the vibration in time-domain and transform it to frequency domain (Fast Fourier transformation). From the frequency response, the peaks, i.e., natural frequencies, can be evaluated and compared to the simulation ones. The simulation of the dynamics is a straightforward procedure when using finite element method (FEM) calculation [14], as the geometry and its mass and stiffness properties are needed. Based on these application experiences, the strong physics-based DT is relevant in the applications where the dynamics are relevant in the application.

In the chapter, the simulation-based virtual product is the basis of development, i.e., machine manufacturer R&D knowledge tied to a virtual product. The main applications which the earlier work covers are related to HSEM and NRMM, where the computationally efficient dynamic models are critical from the perspective of the final product and its behavior. The chapter introduces the approaches of different level DTs and exemplary concepts of how they can be leveraged in business to gain a competitive edge in novel markets. The focal point of discussion is linking technology with business thinking and emphasizing how the DT’s maturity affects its ability to capture business value. Therefore, the chapter takes an important position in bridging the technology- and business-oriented issues and experts through building mutual understanding and addressing not only the development but also the business application of DTs.

The chapter is structured as follows. Section 11.2 explains the context and background to the viewpoint and theories; Section 11.3 describes physics-based DT and competitive edge and value creation; and Section 11.4 discusses the benefits, opportunities, and challenges of the physics-based DT in novel markets. Section 11.5 is the concluding section.

### 11.2 Context and Background

Digital twin as a terminology has been expanding rapidly during the last decade [15]. Digital twins can be prototypes (DTP), instances (DTI), or aggregates (DTA) that operate in the digital twin environment (DTE) [1], where the uses for the DTs can be various, e.g., reporting, predicting, analyzing, and autonomous decisions [1]. Depending on the increasing coordination, synchronization, and pooled synergies between various uses within a firm, these can be described with the term ‘digital twin maturity’, and understood as industrial applications equivalent to firm-level artificial intelligence (AI) maturity (see further, e.g., [6,7]). In the last few years, the maturity model and viewpoint on DTs have been developed to discuss the content from the right viewpoint between different experts.

In this book chapter, the DT is viewed from the simulation perspective, where the modeling, computing capacity, and implementation have been enhanced significantly during the last 5 years. For the DT, real-time behavior is desired, but also faster-than-real-time models can give additional insight to the machine, e.g., when utilizing reinforcement learning algorithms [16].

Also, one distinguishing feature when utilizing simulation-based DTs comes from the products which are tailor-made. For mass products, the available data are easily available in large quantities, which is fruitful for AI and neural networks to identify patterns between different measured quantities. The building of a DT from the physics-based models is a bit different viewpoint than the majority of DT literature; however, it has great potential to assess the system behavior beyond the limited scenarios, e.g., in bearing fault classification [17]. In addition, the physics-based simulation serves also for the company process and planning perspective, e.g., human tasks or specific application process optimization.

The cost of failure of an individual machine in a typical product development process becomes higher the longer the machine has been designed, procured and assembled, commissioned, and produced. The design part can be done to a great extent in the virtual world.

The engineering is mainly done in the virtual world, as there the iteration loops are rapid to operate, and also while having the physical real-life

