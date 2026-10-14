
EC enables engineers and scientists to swiftly and efficiently build, optimize, and test new products and technologies. It enables rapid innovation in fields including aerospace, automobile design, energy systems, and material research by allowing for the study of a broad design space. EC aids in the identification of optimal designs, resulting in improved products and solutions, by modeling and analyzing complicated systems.

### C. Advances in data analytics and AI
EC enables the processing and analysis of enormous datasets in real-time, opening up new opportunities in data analytics and AI. It makes possible for DL and machine learning models to be more accurate and effective, which advances fields like genomics, personalized medicine, social network analysis, autonomous systems, and recommendation systems (Tanmoy et al., 2019; Francis et al., 2020). EC facilitates the extraction of useful insights from enormous amounts of data, fostering innovation and decision-making.

### D. Cross-disciplinary collaboration

EC fosters cross-disciplinary cooperation among scholars. Exascale systems’ computational capacity and resources can be used by scientists, engineers, and subject-matter specialists to tackle challenging issues that call for interdisciplinary solutions ([R. Arya et al., 2021](#ch3.xhtml#ref3_12)). Through information exchange and integrated problem-solving, this partnership may result in advances in areas like fusion energy, drug development, urban design, and computational social sciences.

### E.Precision and realism

EC allows for simulations and modeling with a level of accuracy and realism never before possible. Exascale simulations deliver more precise results by including complex interconnections and finer-grained details. This improves decision-making processes, which helps in better forecasts, and encourages the creation of trustworthy and durable systems and technologies.

### F. Economic and social impact

EC holds the promise of fostering both societal and economic improvement. By quickening the pace of product development cycles, enhancing efficiency, and cutting costs, it encourages innovation and supports industries. By offering strong tools for modeling, analysis, and optimization, EC also helps to address major issues like climate change, healthcare, and sustainable energy.

### G. Advances in computation

EC promotes improvements in computational methods and algorithms. To efficiently utilize the processing capacity of exascale computers, researchers investigate novel algorithms, optimization techniques, and parallel programming paradigms. Beyond exascale computing, these developments help other computer platforms and allow for further development in HPC.

## VII. Challenges in EC

Exascale are facing different technical and social challenges (John et al., 2011; Pete et al., 2012; Judicael et al., 2015; Mahendra et al., 2020; [Matthew et al., 2020](#ch3.xhtml#ref3_2)) are shown in [Figure 3.4](#ch3.xhtml#fig3_4). These challenges are as discussed in the following sections.

![Figure 3.4 Challenges of exascale computing](images/fig3_4_C.jpg)

[Figure 3.4 Challenges of exascale computing](#ch3.xhtml#R_fig3_4)

### A. Technical challenges

Exascale system has identified four key challenges: increased number of faults, power requirement minimization, memory management and parallelism at node level. These challenges are directly related to exascale OS/R (operating system and runtime software) layer. Hardware complexity, resources challenges within OS, programming model, design issues are few more to handle.

1.  **Resilience**

    As the numbers of components are increasing on chip, the numbers of faults are also increases. These faults cannot be protected by other error detection and correction technique. Timely propagation fault notification across large network in limited bandwidth scenario is very difficult.

2.  **Power management**

    It is one of the critical challenges of exascale system. It requires 20–30 MW to run any application. Resources can be change at any time to adopt power requirement.

3.  **Memory hierarchy**

    New memory technology emphasizes on reducing the power cost while data are transferring between different nodes. In case of exascale system, the OS provide more support to runtime and application management and as the complexity reduces the OS overheads.

4.  **Parallelism**

    Exascale system performs the calculation of 10^18 FLOPS. In order to achieve these calculations, application performs billions of calculation with in a second. This situation is significant challenge for developers. Performance cannot be increased through additional clock scaling but additional parallelism is required in order to support next generation of systems. But OS again faces different challenges like efficient and scalable synchronization, scheduling, scalable resource management, global consistency, coordination, and control.

5.  **Hardware-related challenges**

    The hardware resources are heterogeneous in nature. It includes multiple types of memory and different processing element. Different type of component may have different performance characteristics though they have capabilities to perform same function. Therefore, allocation of resources becomes complicated to perform the calculation. Handler establishment process for hardware event is more difficult in order to support responsiveness to faults, application monitoring system, and energy management and so on.

6.  **OS/R structural challenges**

    The new operating system for exascale system is facing different challenges like misalignment of requirements, user-space resource management and parallel OS services.

    1.  **Misalignment of requirements:**

        The interference of OS should be minimized while at the same time OS should provide necessary support to all other application.

    2.  **User-space resource management**

        Generally OS directly manages and controls all resources to different application software. However different programming models and application requires different resources results in inefficiency. In the future application software and runtime will require increased control over resources like core, memory, power and so on.

    3.  **Parallel OS services**

        OS performs parallel processing; effective support and development for this interface is difficult.

7.  **Legacy OS/R issues**

    *   The node operating and runtime systems for an exascale system will need to be highly parallel, with minimal synchronization. Legacy operating and runtime systems tend to be monolithic, frequently assuming mutual exclusion for large portions of the code.

    *   The node operating and runtime systems for an exascale system will need to support tight interaction across sets of nodes (enclaves). Legacy operating and runtime systems have been designed to impose strict barriers between nodes.

    *   The node operating and runtime systems for an exascale system will need to be right-sized in order to meet the needs of the application while minimizing overheads. Legacy operating and runtime systems do not emphasize restructuring to match the needs of an application.

### B. Business and social challenges

In spite of having technical excellence, exascale system is facing different challenges in business like lack of transparency from vendors, sustainability and portability, preservation of existing code base and so on.

## VIII. Future and research aspects of EC

EC has the ability to significantly advance technological innovation, scientific discoveries, and societal concerns. The following are some crucial elements of EC’s future and research potential (Tanmoy et al., 2019; Francis et al., 2020; Maxwell et al., 2021; Yuhui [Don et al., 2022](#ch3.xhtml#ref3_17)). The market growth of EC is represented in the [table 3.2](#ch3.xhtml#tab3_2).

[Table 3.2 Represents the market growth of EC](#ch3.xhtml#R_tab3_2)
