![](images/9780128151198/9780128151204_FC.jpg)

![9780128151204\_FC](images/9780128151198/9780128151204_FC.jpg)

# Table of Contents

[Cover image](#Cover.xhtml)

[Title page](#Titlepage.xhtml)

[Copyright](#S0065245818300081.xhtml)

[Preface](#S006524581830010X.xhtml)

[Chapter One: Model-Based Testing for Internet of Things Systems](#S0065245817300517.xhtml)

[Abstract](#S0065245817300517.xhtml#ab0010)

[1 Introduction](#S0065245817300517.xhtml#s0010)

[2 Challenges of Testing IoT Systems](#S0065245817300517.xhtml#s0015)

[3 State of the Art](#S0065245817300517.xhtml#s0045)

[4 MBT for IoT Conformance Testing](#S0065245817300517.xhtml#s0145)

[5 MBT for IoT Security Testing](#S0065245817300517.xhtml#s0180)

[6 Online MBT for IoT Robustness Testing](#S0065245817300517.xhtml#s0220)

[7 Model-Based Testing as a Service](#S0065245817300517.xhtml#s0245)

[8 Lessons Learnt and Discussion](#S0065245817300517.xhtml#s0275)

[9 Conclusion](#S0065245817300517.xhtml#s0280)

[Acknowledgments](#S0065245817300517.xhtml#s0285)

[Chapter Two: Advances in Software Model Checking](#S0065245817300505.xhtml)

[Abstract](#S0065245817300505.xhtml#ab0010)

[1 Introduction](#S0065245817300505.xhtml#s0010)

[2 Explicit-State Bounded Model Checking](#S0065245817300505.xhtml#s0030)

[3 Symbolic Execution](#S0065245817300505.xhtml#s0075)

[4 Abstraction-Based Model Checking](#S0065245817300505.xhtml#s0110)

[5 Conclusions](#S0065245817300505.xhtml#s0125)

[Chapter Three: Emerging Software Testing Technologies](#S0065245817300529.xhtml)

[Abstract](#S0065245817300529.xhtml#ab0010)

[1 Introduction](#S0065245817300529.xhtml#s0010)

[2 Basic Concepts of Testing](#S0065245817300529.xhtml#s0015)

[3 Test Cases Generation](#S0065245817300529.xhtml#s0065)

[4 Test Challenges](#S0065245817300529.xhtml#s0110)

[5 Testing Process](#S0065245817300529.xhtml#s0150)

[6 Domain-Specific Testing](#S0065245817300529.xhtml#s0170)

[7 Discussion and Conclusions](#S0065245817300529.xhtml#s0225)

[Chapter Four: Optimizing the Symbolic Execution of Evolving Rhapsody Statecharts](#S0065245817300487_1.xhtml)

[Abstract](#S0065245817300487_1.xhtml#ab0010)

[1 Introduction](#S0065245817300487_1.xhtml#s0010)

[2 Background](#S0065245817300487_1.xhtml#s0030)

[3 Related Work](#S0065245817300487_1.xhtml#s0095)

[4 Standard Symbolic Execution of Rhapsody Statecharts](#S0065245817300487_1.xhtml#s0125)

[5 Optimizing Symbolic Execution of Evolving Rhapsody Statecharts](#S0065245817300487_1.xhtml#s0165)

[6 Implementation](#S0065245817300487_2.xhtml#s0230)

[7 Evaluation](#S0065245817300487_2.xhtml#s0260)

[8 Conclusion: Summary, Future Work, and Perspective](#S0065245817300487_3.xhtml#s0295)

[Appendix](#S0065245817300487_3.xhtml#s0320)

[Chapter Five: A Tutorial on Software Obfuscation](#S0065245817300499.xhtml)

[Abstract](#S0065245817300499.xhtml#ab0010)

[1 Introduction](#S0065245817300499.xhtml#s0010)

[2 Classification of Code Obfuscation Transformations](#S0065245817300499.xhtml#s0015)

[3 Classification of MATE Attacks](#S0065245817300499.xhtml#s0055)

[4 Survey of Obfuscation Transformations](#S0065245817300499.xhtml#s0085)

[5 Discussion](#S0065245817300499.xhtml#s0270)

[6 Related Work](#S0065245817300499.xhtml#s0275)

[7 Conclusion](#S0065245817300499.xhtml#s0305)

 

# Copyright

![](images/S0065245818300081/main.png)

 

# Preface

Prof. Atif M. MemonPh.D , ^()College Park, MD, United States

This volume of Advances in Computers is the 108th in this series. This series, which has been continuously published since 1960, presents in each volume four to seven chapters describing new developments in software, hardware, or uses of computers. For each volume, I invite leaders in their respective fields of computing to contribute a chapter about recent advances.

Volume 108 focuses on five topics. In [Chapter 1](#S0065245817300517.xhtml), entitled “Model-Based Testing for Internet of Things Systems,” authors Ahmad et al. posit that the Internet of Things (IoT) has become a means of innovation and transformation. Applications extend to a large number of domains, such as smart cities, smart homes, and healthcare. The Gartner Group estimates an increase up to 21 billion connected things by 2020. The large span of “things” introduces problematic aspects, such as interoperability due to the heterogeneity of communication protocols and the lack of a globally accepted standard. The large span of usages introduces problems regarding secure deployments and scalability of the network over large-scale infrastructures. The chapter describes the challenges for IoT testing, includes a state-of-the-art testing of IoT systems using models, and presents a Model-Based-Testing-As-A-Service approach to respond to its challenges through demonstrations with real use cases.

In [Chapter 2](#S0065245817300505.xhtml), entitled “Advances in Software Model Checking,” authors Siddiqui et al. observe that society is becoming increasingly dependent on software which results in an increasing cost of software malfunction. At the same time, software is getting increasingly complex and testing and verification are becoming harder. Software model checking is a set of techniques to automatically check properties in a model of the software. The properties can be written in specialized languages or be embedded in software in the form of exceptions or assertions. The model can be explicitly provided in a specification language, can be derived from the software system, or the software system itself can be used as a model. Software model checkers check the given properties in a large number of states of the model. If a model checker is able to verify a property on all model states, it is proven that the property holds and the model checker works like a theorem prover. If a model checker is unable to verify a property on all model states, the model checker is still an efficient automated testing technique. This chapter discusses advances in software model checking and focuses on techniques that use the software as its model and embedded exceptions or assertions as the properties to be verified. Such techniques are most likely to be widespread in the software industry in the coming decade due to their minimal overhead on the programmer and due to recent advances in research making these techniques scale.

[Chapter 3](#S0065245817300529.xhtml), “Emerging Software Testing Technologies,” by Lonetti et al., provides a comprehensive overview of emerging software testing technologies. Beyond the basic concepts of software testing, the chapter addresses prominent test case generation approaches and focuses on more relevant challenges of testing activity as well as its role in recent development processes. An emphasis is also given to testing solutions tailored to the specific needs of emerging application domains. Software testing encompasses a variety of activities along the software development process and may consume a large part of the effort required for producing software. It represents a key aspect to assess the adequate functional and nonfunctional software behavior aiming to prevent and remedy malfunctions. The increasing complexity and heterogeneity of software pose many challenges to the development of testing strategies and tools.

In [Chapter 4](#S0065245817300487_1.xhtml), “Optimizing the Symbolic Execution of Evolving Rhapsody Statecharts,” authors Khalil and Dingel present two optimization techniques to direct successive runs of symbolic execution toward the impacted parts of an evolving state machine model using memoization (MSE) and dependency analysis (DSE), respectively. Model-driven engineering (MDE) is an iterative and incremental software development process. Supporting the analysis and the verification of software systems developed following the MDE paradigm requires to adopt incrementally when carrying out these crucial tasks in a more optimized way. Communicating state machines are one of the various formalisms used in MDE tools to model and describe the behavior of distributed, concurrent, and real-time reactive systems (e.g., automotive and avionics systems). Modeling the overall behavior of such systems is carried out in a modular way and on different levels of abstraction (i.e., it starts with modeling the behavior of the individual objects in the system first and then modeling the interaction between these objects). Similarly, analyzing and verifying the correctness of the developed models to ensure their quality and their integrity is performed on two main levels. The intralevel is used to analyze the correctness of the individual models in isolation of the others, while the interlevel is used to analyze the overall interoperability of those that are communicating with each other. The evaluation results of both techniques showed significant reduction in some cases compared with the standard symbolic execution technique.

[Chapter 5](#S0065245817300499.xhtml), “A Tutorial on Software Obfuscation,” by Banescu et al., discusses the important problem of protecting a digital asset once it leaves the cyber trust boundary of its creator; this is a challenging security problem. The creator is an entity which can range from a single person to an entire organization. The trust boundary of an entity is represented by all the (virtual or physical) machines controlled by that entity. Digital assets range from media content to code and include items such as music, movies, computer games, and premium software features. The business model of the creator implies sending digital assets to end-users—such that they can be consumed—in exchange for some form of compensation. A security threat in this context is represented by malicious end-users, who attack the confidentiality or integrity of digital assets, in detriment to digital asset creators and/or other end-users. Software obfuscation transformations have been proposed to protect digital assets against malicious end-users, also called Man-At-The-End (MATE) attackers. Obfuscation transforms a program into a functionally equivalent program which is harder for MATE to attack. However, obfuscation can be used for both benign and malicious purposes. Malware developers rely on obfuscation techniques to circumvent detection mechanisms and to prevent malware analysts from understanding the logic implemented by the malware. This chapter presents a tutorial of the most popular existing software obfuscation transformations and mentions published attacks against each transformation. The chapter presents a snapshot of the field of software obfuscation and indicates possible new research directions.

I hope that you find these articles of interest. If you have any suggestions of topics for future chapters, or if you wish to be considered as an author for a chapter, I can be reached at [atif@cs.umd.edu](mailto:atif@cs.umd.edu).

Chapter One 

# Model-Based Testing for Internet of Things Systems

Abbas Ahmad[\*](#S0065245817300517.xhtml#af0010)^(,[‡](#S0065245817300517.xhtml#af0020)); Fabrice Bouquet[\*](#S0065245817300517.xhtml#af0010); Elizabeta Fourneret^([†](#S0065245817300517.xhtml#af0015)); Bruno Legeard[\*](#S0065245817300517.xhtml#af0010)^(,[†](#S0065245817300517.xhtml#af0015))    ^(\*) Institut FEMTO-ST – UMR CNRS 6174, Besançon, France  
^† Smartesting Solutions & Services – 18, Besançon, France  
^‡ Easy Global Market, Valbonne, France

## Abstract

The Internet of Things (IoT) is nowadays globally a mean of innovation and transformation for many companies. Applications extend to a large number of domains, such as smart cities, smart homes, and health care. The Gartner Group estimates an increase up to 21 billion connected things by 2020. The large span of “things” introduces problematic aspects, such as interoperability due to the heterogeneity of communication protocols and the lack of a globally accepted standard. The large span of usages introduces problems regarding secure deployments and scalability of the network over large-scale infrastructures. This chapter describes the challenges for the IoT testing, includes state-of-the-art testing of IoT systems using models, and presents a model-based testing as a service approach to respond to its challenges through demonstrations with real use cases involving two of the most accepted standards worldwide: FIWARE and oneM2M.

### Keywords

Model-based testing; Modeling approaches; Test generation technology; Security testing

## 1 Introduction

The Internet of Things (IoT) interconnects people, objects, and complex systems. While this is as vast as it sounds, spanning all industries, enterprises, and consumers, one of the challenges facing the IoT is the enablement of seamless interoperability between each connection. The massive scale of recent Distributed Denial of Service (DDoS) attacks (October 2016) on DYNs servers \[

Systematic and automated testing of the IoT based on models is a way of ensuring their security. Nevertheless, traditional testing methods, whether they are based on models or not, require adaptation due to the IoT heterogeneous communication protocol, complex architecture, and insecure usage context, the IoT must be tested in their real use case environment: service-based and large-scale deployments.

A model-based testing as a service (MBTAAS) approach is proposed to respond to these challenges where the IoT are tested in their natural environment: large-scale and service-oriented. The MBTAAS approaches goal is to ensure conformance and security over proposed solutions (APIs, devices, etc.). The models of the approach mimic the intended behaviors, thus the services are seen as Black Boxes for testing.

Models can be described in different ways, depending on the discipline. They can be described by use of diagrams (UML, BPMN, etc.), tables, text, or other types of notations, such as the ETSI TPLan. They might be expressed in a mathematical formalism or informally. Although computing equipment and software play an important role for the application of modeling in science and engineering, modeling is not as ubiquitous in software engineering as it is in other engineering disciplines. However, formal methods are one discipline where modeling has been applied in the areas of safety and security-critical software systems. Test phases are in the last stages of system development. They are therefore strongly constrained by delivery periods. In general, they suffer from the accumulated delays during the overall project.

Currently, the verification and validation process for the IoT having no systematic or automatic process is often underestimated and outsourced to reduce costs. All these factors affect the quality of current products. Testing is a difficult and time-consuming activity. Indeed, it is not possible to test everything because the quantity of test cases to be applied could be potentially infinite for the majority of modern systems. The difficulty of testing lies in the selection of relevant test cases for each phase of validation. It also lies in the absence of a true reflection of test optimization guided by the maintenance of the final quality while minimizing costs.

We present hereafter a technology which is used ever more in the IoT domain to avoid bugs, to improve large-scale quality, interoperability, and reduce security threats: model-based testing (MBT). MBT allows the automatic generation of software test procedures, using models of system requirements and behavior. Although this type of testing requires more upfront effort in building the model, it offers substantial advantages over traditional testing methods \[

*   • Rules are specified once.
*   • Project maintenance is lower. There is no need to write new tests for each new feature. Once a model is obtained, it is easier to generate and regenerate test cases than it is with hand-crafted test cases.
*   • The design is fluid. When a new feature is added, a new action is added to the model to run in combination with existing actions. A simple change can automatically ripple through the entire suite of test cases.
*   • Design more and code less. This makes the testing process generic with respect to the development languages used to implement an application, for instance, for different operating systems (OS).
*   • High coverage. Tests continue to find bugs, not just regressions due to changes in the code path or dependencies.
*   • Model authoring is independent of implementation and actual testing, so that these activities can be performed by different members of a team concurrently.
*   • Unit testing is elementary and it is not sufficient to check the functionalities, thus MBT is complementary to unit testing.
*   • Ensures that the system is behaving in the same sequence of actions.
*   • MBT adoption in the industry as an integrated part of the testing process has largely increased.
*   • Mature and efficient tools exist to support MBT.

[Section 2](#S0065245817300517.xhtml#s0015) presents the specific key challenges of testing IoT system. [Section 3](#S0065245817300517.xhtml#s0045) gives an insight on the state of the art, in general, about MBT and existing MBT tools to select solutions adapted to the IoT testing approach. [Section 4](#S0065245817300517.xhtml#s0145) presents MBT for IoT conformance testing. [Section 5](#S0065245817300517.xhtml#s0180) presents MBT for IoT security testing. [Section 6](#S0065245817300517.xhtml#s0220) presents online MBT for IoT robustness testing. [Section 7](#S0065245817300517.xhtml#s0245) depicts an exploration of the MBTAAS approach. We finally provide our lessons learnt and discuss the different approaches in [Section 8](#S0065245817300517.xhtml#s0275), before providing concluding remarks in [Section 9](#S0065245817300517.xhtml#s0280).

## 2 Challenges of Testing IoT Systems

Gartner states that more than 6.4 billion IoT devices were in use in 2016, and that number will grow to more than 20 billion by 2020. Testing these devices, which range from refrigerators that automatically place orders to the supermarket to self-driving cars, will be one of the biggest challenges encountered by the device manufacturers and integrators in the coming years. Effective testing is critical and defining the best approach implies dissecting the different IoT layers involved.

### 2.1 IoT Layers

There are four major layers in an IoT system, as illustrated in [Fig. 1](#S0065245817300517.xhtml#f0010). From bottom to top, the first is the sensor layer. Then, there is the gateway and network layer. On the third layer, the management service layer and finally as a fourth layer, the application layer.

![Fig. 1 IoT layers.](images/S0065245817300517/f01-01-9780128151198.jpg)

Fig. 1 IoT layers.

The sensor layer uses and produces data. Thus, the IoT devices, at this bottom layer, can behave differently whether their purpose is to generate data (a data producer), or to use produced data (a data consumers). Note that it is significantly different from the application layer where data are also used and produced. For example, the complex event processing (CEP) application is a data consumer application within the application layer. Its purpose is to read input data and produce output data depending on a defined rule. An example of a rule defined in a CEP application: if the data of two temperature sensors in the same room exceed a certain value, then an alert is triggered. The produced data are in this case the generated alert.

The service connectivity and network layers are represented by the sensors, actuators, tags (which include radio frequency IDs (RFID) and barcodes), and other types of data producers/consumers. At the gateway and network layer, wide area networks, mobile communication networks, Wi-Fi, Ethernet, gateway control, etc. are considered. Then, in the management service layer, device modeling configuration and management is a major focus. Data flow management and security control need to be provided at the management service layer. Finally, the overall application layer is where the applications dedicated to energy, environment, health care, transportation, supply chain, retail, people tracking, surveillance, and many other endless applications are located.

### 2.2 Key Challenges

The different layers of the IoT bring a new level of complexity to performance monitoring and conformance testing in terms of scalability, interoperability, and security. Testers must adapt to new platforms and techniques to ensure that they can address the challenges of testing the IoT devices and applications to deliver the best experience to the end user. With large numbers of devices involved when talking about the IoT, scalability is defined as one of the most important key challenges. The mass of different devices that the IoT introduces, each with different protocols, brings along all the perks of a heterogeneous environment: the interoperability challenge. With many different devices and the amount of generated data in the IoT infrastructure, it is difficult to keep track of the privacy and confidentiality of the produced data. Security is a major challenge for the success of the IoT expansion, and we will address this key challenge for testing the IoT systems in the next sections.

#### 2.2.1 Scalability

Connected IoT devices rely on fast communication. Consequently, network status can have a significant effect on device performance. Smart devices often experience problems with network infrastructure, such as overburdened Wi-Fi channels, unreliable network hardware, and slow or inconsistent Internet connections. The IoT devices and applications must be tested across these different conditions to ensure that they respond correctly without losing data.

#### 2.2.2 Interoperability

Each IoT device has its own hardware and relies on software to drive it. Application software will also integrate with the IoT devices, issuing commands to the device and analyzing data gathered by the device. Connecting “things” as devices requires one to overcome a set of problems arising in the different layers of the communication model. Using device data or responding to a devices request requires an IoT deployment to interact with a heterogeneous and distributed environment. Indeed, devices are most likely to be running several protocols (such as HTTP, MQTT, COAP), through multiple wireless technologies. Devices have many particularities and it is not feasible to provide a testing solution where one size fits all. Some devices are resource constrained and cannot use full standard protocol stacks because they cannot transmit information too frequently due to battery drainage; they are not always reachable due to the wireless connection based on low duty cycles, their communication protocols are IoT-specific, lack an integrated approach, and use different data encoding languages. A global IoT platform deployment is difficult to foresee as a direct result of these limitations. Developers face complex scenarios where merging the information is a real challenge.

#### 2.2.3 Security

Securing an entire “classical” infrastructure is a challenge in itself, but the IoT demands an even larger security approach to keep endpoints and networks protected against more sophisticated cybercrime techniques and tools, such as sniffer attacks, DoS attacks, compromised-key attacks, password-based attacks, and man-in-the-middle (MITM) attacks.

Security certification is needed to ensure that a product satisfies the required security requirements, which can be both proprietary requirements (i.e., defined by a company for their specific products) and market requirements (i.e., defined in procurement specifications or market standards). The process for certification of a product is generally summarized in four phases:

1.  1. Application. A company applies a product for evaluation to obtain certification.
2.  2. An evaluation is performed to obtain certification. The evaluation can be mostly done in three ways: 
    1.  (a) The evaluation can be conducted internally to support self-certification.
    2.  (b) The evaluation can be performed by a testing company, who legally belongs to the product company.
    3.  (c) It can be a third-party certification where the company asks a third-party company to perform the evaluation of its product.
3.  3. In the case of an internal company or a third-party company evaluation, the evaluation company provides a decision on the evaluation.
4.  4. Surveillance. This is a periodic check on the product to ensure that the certification is still valid or it requires a new certification.

In the market requirements case, the requirements are also defined to support security interoperability. For example, to ensure that two products are able to mutually authenticate or to exchange secure messages. Security certification is needed to ensure that products are secure against specific security attacks or that they have specific security properties, such as:

*   • Authentication: Data sender and receiver can always be verified.
*   • Resistance to replay attacks: Intermediate nodes can store a data packet and replay it at a later stage. Thus, mechanisms are needed to detect duplicate or replayed messages.
*   • Resistance to dictionary attacks: An intermediate node can store some data packets and decipher them by performing a dictionary attack if the key used to cipher them is a dictionary word.
*   • Resistance to DoS attacks: Several nodes can access the server at the same time to collapse it. For this reason, the server must have DoS protection or a fast recovery after this attack.
*   • Integrity: Received data are not tampered with during transmission; if this does not happen, then any change can be detected.
*   • Confidentiality: Transmitted data can be read only by the communication endpoints.
*   • Resistance to MITM attacks: The attacker secretly relays and possibly alters the communication.
*   • Authorization: Services should be accessible to users who have the right to access them.
*   • Availability: The communication endpoint can always be reached and cannot be made inaccessible.
*   • Fault tolerance: The overall service can be delivered even when a number of atomic services are faulty.
*   • Anonymization: If proper countermeasures are not taken, even users employing pseudonyms could be tracked by their network locator.

Nevertheless, in the IoT domain, initiative exists for security certification, such as the alliance for IoT innovation (AIOTI) through its standardization and policy working groups that complement the existing certifications, such as the common criteria (CC). However, enabling technologies that help to formally address the specific testing challenges and that enable the IoT certification today are lacking \[

## 3 State of the Art

The key challenges in testing for scalability, interoperability, and security of the IoT have proven to be problematic when trying to resolve them with traditional testing methods, which is a strong roadblock for wide adoption of this innovative technology. This section aims to describe how the MBT has addressed this problem though IoT testing.

MBT designates any type of testing based on or involving models \[

Nevertheless, the functions of MBT tools vary largely from one to another. Users without prior knowledge struggle to choose appropriate tools corresponding to their testing needs among the wide list. The MBT tools require input in terms of different models (e.g., UML, PetriNet, and BPMN) and focus on different MBT aspects with different generation strategies for data, test cases, and test scripts. Moreover, most of the existing MBT tools support mainly automatic test case generation rather than test data generation and test script generation due to two reasons: first, the test case generation requires complicated strategies involving various test selection criteria from MBT models, and the generation results highly reply on the selected criteria and strategies; second, the test case generation brings many more testing benefits, as the main efforts spent on traditional testing lie in manual preparation of test cases. To provide users with a common understanding and systematic comparison, this chapter reviews the identified set of MBT tools, focusing on the test case generation aspect. The MBT tools have been previously reported and compared in several surveys: the first report is presented in \[

### 3.1 Model-Based Testing

MBT is an application of model-based design for generating test cases and executing them against the SUT for testing purpose. The MBT process can be generally divided into five steps \[

*   • Step 1: Creation of the MBT models. In the first step, users create the MBT models from requirement/system specifications. The specifications define the testing requirements or the aspects to test of the SUT (e.g., functions, behaviors, and performances). The created MBT models usually represent high-level abstractions of the SUT and are described by formal languages or notations (e.g., UML, PetriNet, and BMPN). The formats of the MBT models depend on the characteristics of the SUT (e.g., function-driven or data-driven system, deterministic or stochastic system) and the required input formats of the MBT tools.
*   • Step 2: Generation of test cases. In the second step, abstract test cases from the MBT models are generated automatically, based on test selection criteria. The test selection criteria guide the generation process by indicating the interesting focus to test, such as certain functions of the SUT or coverage of the MBT model (e.g., state coverage, transition coverage, and data flow coverage). Applying different criteria to the same MBT model will generate different sets of test cases that could be complementary. Abstract test cases without implementation details of the SUT are generated from the MBT models.
*   • Step 3: Concretization of the test cases. In the third step, the abstract test cases (produced in step 2) are concretized into executable test cases with the help of mappings between the abstraction in the MBT models and the system implementation details. Executable test cases contain low-level implementation details and can be directly executed on the SUT.
*   • Step 4: Execution of the test cases. The executable test cases are executed on the SUT either manually or within an automated test execution environment. To automate the test execution, system adapters are required to provide channels connecting the SUT with the test execution environment. During the execution, the SUT is, respectively, stimulated by inputs from each test case, and the reactions of the SUT (e.g., output and performance information) are collected to assign a test verdict. For each test case, a test verdict is assigned indicating if a test passes or fails (or is inconclusive).
*   • Step 5: Results analysis. At the end of the testing, the testing results are reported to the users. For nonsatisfactory test verdicts, the MBT process records traces to associate elements from specifications to the MBT models and then to the test cases, which are used to retrieve the possible defects.

### 3.2 MBT Approaches for the IoT Domain

The related work we discuss in this chapter addresses the panel of existing MBT approaches with a view on the IoT systems. The MBT can be offline, whereby the test cases are generated in a repository for future execution or online, whereby the test cases are generated and executed automatically \[

#### 3.2.1 Functional Testing

Standards are a well-known method used to increase the user's confidence and trust in a product. MBT approaches to support conformance testing to standards have been applied to different domains, such as electronic transactions and notably for CC certifications, for instance, on the global platform (GP). Authors in \[

#### 3.2.2 Security Testing

Mode-based security testing (MBST) is a dynamic application security testing (DAST) approach consisting of dynamically checking the security of the systems's security requirements \[

#### 3.2.3 Online Testing

Online techniques can indeed address the uncertain behavior of the IoT systems, but lack application and maturity for the IoT domain, as current techniques mostly address a testbed setup for execution in a real-life environment, without dealing with the test cases conception.

Several online tools exist in the MBT literature. For instance, UPPAAL for Testing Real-time systems ONline (UPPAAL TRON) \[

Authors in \[

Shieferdecker et al. designed a mutation-based fuzzing approach that uses fuzzing operators on scenario models specified by sequence diagrams. The fuzzing operators perform a mutation of the diagrams resulting in an invalid sequence. Shieferdecker et al. use online behavioral fuzzing which generates tests at run time \[

### 3.3 MBT Tools

In this section, we present a representative set of academic and industrial MBT tools for test case generation that we investigated for usage in the IoT domain and discuss their characteristics. A digest of the tools is presented in [Table 1](#S0065245817300517.xhtml#t0010) and provides a comparison of the different MBT tools based on the testing type, test selection, and test generation technology. It also gives an indication of the test generation process (online, offline, or both).

 

Table 1

 MBT Tools Characterization 

 
| Tools  || Test Generation |
| --- | --- |
| Test Type || Test Selection || Technology || Process |
| CertifyIt || Functional and security || Structural coverage, test case specification || Search based, model checking || Both |
| --- | --- | --- | --- | --- |
| CompleteTest || Functional and security || Structural coverage || Model checking, search based || Offline |
| DIVERISTY || Functional and security || Structural coverage, random and stochastic, test case specification || Symbolic execution || Offline |
| FMBT || Functional || Structural coverage, test case specification || Search based || Both |
| HTG || Functional || Data coverage || Random generation, search based || Offline |
| Lurette || Functional || Random and stochastic || Random generation || Online |
| MISTA || Functional || Structural coverage, random and stochastic || Search based, random generation || Both |
| Modbat || Functional || Random and stochastic || Random generation, search based || Both |
| MoMuT || Functional and security || Fault based || Search based || Offline |
| Pragamadev || Functional and security || Structural coverage, random and stochastic || Symbolic execution || Offline |
| Tcases || Functional || Data coverage || Constraint solving || Offline |
| TCG || Functional and security || Structural coverage, random and stochastic || Search based, random generation || Offline |
| VERA || Security || Structural coverage || Search based || Both |

![t0010](images/S0065245817300517/t0010.png)

#### 3.3.1 CompleteTest

CompleteTest \[

#### 3.3.2 DIVERSITY

DIVERSITY \[

#### 3.3.3 FMBT

FMBT \[

#### 3.3.4 HTG

HTG \[

#### 3.3.5 Lurette

Lurette \[

#### 3.3.6 MISTA

MISTA \[

#### 3.3.7 Modbat

Modbat \[

#### 3.3.8 MoMuT

MoMuT is a set of model-based test case generation tools that work with the UML state machine, timed automata, requirement interfaces, and action systems \[

[Table 1](#S0065245817300517.xhtml#t0010) is an abstract of the MBT tools that offer the IoT testing capabilities. It represents the different testing characterizations for each presented MBT tool: their test type, test selection criteria, the technology used for test generation, and the generation process.

#### 3.3.9 PragmaDev

PragmaDev Studio \[

#### 3.3.10 Tcases

Tcases \[

#### 3.3.11 TCG

TCG \[

#### 3.3.12 VERA

VERA \[

#### 3.3.13 CertifyIt

Smartesting CertifyIt \[

Finally, we increment the classical usage of the CertifyIt tool for functional and security testing and integrate it into a MBT as a Service (MBTAAS) environment, which delivers immense value for the IoT community. The adaptation of CertifyIt for the IoT domain has already shown its value, as discussed by the authors in \[

## 4 MBT for IoT Conformance Testing

Interoperability is one of the key challenges in the IoT testing because of the substantial number of devices deployed and expected to be deployed. Our experience showed that unit testing is not sufficient to check a standardized IoT platform implementation and ensure against interoperability issues. The reason is that the system's functionalities are not seen globally, but from an elementary coding level, a function or even a statement, is that the full spectrum of functionalities, as required by the standard, may not be validated through this type of testing.

On the contrary to unit testing, MBT has its entry point at the standard level, which defines the full spectrum of functionalities. Thus, it ensures the test coverage of these functionalities and provides the oracle to validate the implementation's conformance to the standard.

This section aims to illustrate how MBT can respond to the challenge of interoperability and present it through a real use case based on a real interoperability standard, FIWARE \[

We apply our approach to the IoT Services Enablement Generic Enablers (GEs) implementing the FIWARE specifications, and more specifically to the data handling GE. Thus, we verify the implementations for compliance to the standard. The FIWARE platform \[

*   • Cloud hosting: enables entrepreneurs and individuals to test the technology as well as their applications on FIWARE.
*   • Data/context management: provides solutions to innovative applications that require management, processing and exploitation of context information, as well as data streams in real-time and on massive scales. The context information is any relevant information regarding the environment and its users.
*   • Internet of Things services enablement: allows things to become available, searchable, accessible, and usable contextual resources.
*   • Applications, services, and data delivery: support the creation of an ecosystem of applications, services, and data.
*   • Security of data: provides security to the IoT application, for example, OAuth 2.0 \[
*   • Interface to networks and devices (I2ND): defines an enabler space for providing GEs to run an open and standardized network infrastructure.
*   • Advanced web-based user interface: brings components that will provide a simple, uniform way to create rich networked 2D and 3D applications that run in a browser.

### 4.1 MBT Specificities for IoT Conformance Testing

FIWARE uses the open mobile alliance (OMA) NGSI-9/10 standardized RESTful interfaces \[

In addition, RESTful systems communicate over the hypertext transfer protocol (HTTP) with the same HTTP verbs (GET, POST, PUT, DELETE, etc.) that web browsers use to retrieve web pages and to send data to remote servers. Their purpose is to exchange information about the availability of contextual information.

In our context of testing the implementation of the data handling GE, we are interested in applying conformance testing on NGSI-9/10. Moreover, although it is often assumed that the GEs are correctly implemented and are used or are part of the services provided by FIWARE, noncompliance to the FIWARE specifications may lead to several dysfunctional interoperability issues. To ensure the interoperability, the GEs should be thoroughly tested to assess their compliance to these specifications. MBT is considered to be a lightweight formal method to validate software systems. It is formal because it works off formal (that is, machine-readable) specifications (or models) of the software SUT (usually called the implementation or just SUT). It is lightweight because, contrary to other formal methods, such as B and Z notation, MBT does not aim at mathematically proving that the implementation matches the specifications under all possible circumstances. In MBT, the model is an abstraction of the SUT and represents the tested perimeter based on the specifications, which is not necessarily the entire system. As such, it allows to systematically generate from the model a collection of tests (a “test suite”) that, when run against the SUT, will provide sufficient confidence that the system behaves accordingly to the specification. Testing follows the paradigm of not proving the absence of errors, but showing their presence. MBT, on the other hand, scales much better and has been used to test life-size systems in very large projects \[

In FIWARE, the MBT conformance model is a representation of the standard. The model includes all the behaviors of the NGSI-v1 and generates the complete suite of test cases that are needed to test for implementation compliance to that standard. Changing an MBT model designed for conformance testing implies that the standard has changed.

In the following sections, we provide an overview of the MBT approach applied for conformance testing of one FIWARE GE implementation.

#### 4.1.1 MBT Model

This approach considers a subset of the UML to develop the MBT models, composed of two types of diagrams for the structural modeling: class diagrams and object diagrams, and OCL to represent the system's behavior. From one MBT model, various test selection criteria can be applied, as shown in [Fig. 2](#S0065245817300517.xhtml#f0015). For this study, we used the Smartesting MBT approach and its test generation tool—CertifyIt, which uses the coverage-based test selection criteria.

![Fig. 2 The MBT workflow.](images/S0065245817300517/f01-02-9780128151198.jpg)

Fig. 2 The MBT workflow.

Tested requirements are manually extracted from the specification. Each of the requirements is than tagged into the model, which serves as a basis to maintain traceability to the specification. Based on the specification information and tested requirements perimeter, the structure of the system is represented in a class diagram, which is a static view of the system limited to elements used for test generation.

The FIWARE class diagram ([Fig. 3](#S0065245817300517.xhtml#f0020)) is an abstraction of the IoT system:

*   • Its entities, with their attributes. The class Sut represents the SUT where things can register to it. The CEP statement CepStatement can also be registered to the Sut and the Sut supports Subscription to its registered things.
*   • Operations that model the API of the SUT. The operation names give a self-explanation of their action, for example, the class registerContext enables a sensor to register itself in the IoT platform.
*   • Points of observations that may serve as oracles are explained in the following paragraphs (for instance, an observation returns the current state of the user's connection to a website).

![Fig. 3 Data handling GE class diagram.](images/S0065245817300517/f01-03-9780128151198.jpg)

Fig. 3 Data handling GE class diagram.

The class diagram, providing a static view of the SUT, is instantiated by an object diagram. The object diagram provides the initial state of the system and also all objects that will be used in the test input data as parameters for the operations in the generated tests.

It contains the input data based on the partition equivalence principle. The input data are instances of the classes and they are represented in the form of objects, as introduced previously. Each input data is identified by an enumeration, representing an equivalent partition of data from which the test could be derived. For instance, from [Fig. 4](#S0065245817300517.xhtml#f0025), to test the Espr4FastData API, we may consider an initial state of the system with a SUT having nothing connected to it and some entities to be used for registering, creating the CEP statements, subscriptions, etc.

![Fig. 4 Excerpt of the data handling object diagram.](images/S0065245817300517/f01-04-9780128151198.jpg)

Fig. 4 Excerpt of the data handling object diagram.

Finally, the dynamic view of the system or its behaviors are described by the object constraint language (OCL) constraints written as pre/postconditions in the operations in a class within a class diagram, as depicted in [Fig. 5](#S0065245817300517.xhtml#f0030). The test generation engine sees these behavioral objects as test targets. The operations can have several behaviors, identified by the presence of the conditional operator, if-then-else. The precondition is the union of the operation's precondition and the conditions of a path that is necessary to traverse for reaching the behaviors postcondition. The postcondition corresponds to the behavior described by the action in the “then” or “else” clause of the conditional operator. Finally, each behavior is identified by a set of tags which refers to a requirement covered by the behavior. For each requirement, two types of tags exist

*   • @REQ—a high-level requirement
*   • @AIM—its refinement

![Fig. 5 Object constraint language (OCL) example.](images/S0065245817300517/f01-05-9780128151198.jpg)

Fig. 5 Object constraint language (OCL) example.

Both are followed by an identifier. One advantage of the used MBT tool is the possibility to automatically deduct the test oracle. A specific type of operation, called observation, defines the test oracle. The tester with these special operations can define the system points or variables to observe, for instance, a function returns a code. Thus, based on these observations, the test oracle is automatically generated for each test step. The next session provides us an inside view on the test case generation process.

#### 4.1.2 Test Case Generation

Based on the chosen test selection criteria, CertifyIt extracts the test objectives into a test suite, called with the CertifyIt terminology a smartsuite.

In our case study, two smartsuites named EspR4FastData\_GETestSuite and UserTestScenarios were created. The EspR4FastData\_GETestSuite test suite indicates that the generation should be done for all defined test objectives whereas for the UserTestScenarios\_SmartSuite, they are user-defined scenarios of tests to define some very specific cases with the help of the MBT model. Based on the object diagram and the OCL postcondition, the CertifyIt tool automatically extracts a set of test targets, which is the tool comprehensible form of a test. The test targets are used to drive the test generation. As discussed previously, each test has a set of tags associated with it, which ensures the coverage and traceability to the specification. [Fig. 6](#S0065245817300517.xhtml#f0035) gives a snapshot of a test in the CertifyIt tool. On the left side, the tool lists all generated tests clustered per covered requirement. On the right side, the test case can be visualized and for each step a test oracle is generated. As discussed, the tester with the observation manually defines the system points to observe when calling any function. Figure, checkResult, observes the return code of each function with respect to the activated requirement. In addition, on the bottom-right of the figure for each test case and test step, it is possible to observe the test targets (set of tags).

![Fig. 6 CertifyIt test case view.](images/S0065245817300517/f01-06-9780128151198.jpg)

Fig. 6 CertifyIt test case view.

In addition, [Fig. 7](#S0065245817300517.xhtml#f0040) illustrates the generated tests with CertifyIt, in exported HTML. More specifically, the shown test covers the behavior that resets the GE implementation using the resetGE function. As discussed previously, each test has a set of associated tags for which it ensures the coverage. The export of this test, as illustrated in [Fig. 7](#S0065245817300517.xhtml#f0040), in the rightmost column, maps to each step the covered requirements or more precisely the test objective tagged by @REQ and @AIM in the model. The export, as shown in the middle column of the figure, contains guidelines for test reification, giving directions on how the abstract test case should be adapted into a concrete script, which is described in the next section.

![Fig. 7 Implementation abstract test case (HTML export).](images/S0065245817300517/f01-07-9780128151198.jpg)

Fig. 7 Implementation abstract test case (HTML export).

Within the considered limits of the implementation, the tool extracted 26 “test targets” and generated 22 tests in around 10 s to cover the test targets. Each story in the CertifyIt tool corresponds to one test target. However, one test covers one or more test targets. Moreover, the tool's engine generates fewer tests then test targets, because it uses the “light merge” of test methods, which considers that one test covers one or more test objectives (all test objectives that have been triggered by the test steps). For instance, the test shown in [Fig. 6](#S0065245817300517.xhtml#f0035) covers two test objectives. The “light merge” of the tests shortly and on a high-level means that the generator will not produce separate tests for the previously reached test targets.

The generated tests are abstract and to execute them on the SUT, they should be further adapted. For our study, a SoapUI exporter was created, which publishes tests into SoapUI XML projects using the SoapUI library.

#### 4.1.3 Test Case Reification and Execution

In the used MBT approach, to execute tests on the SUT, the activity of test cases reification, also named test case adaptation, is performed first; it consists of creating an adaptation layer to fulfill the gap between the abstract test case generated from the MBT model, the concrete interface, and the initial set of test data of the SUT. As classically required for the test adaptation activities, exporting the abstract test cases (ATS) into executable scripts is the first step to perform, in this case, the ATS are exported into XML files which can be imported and executed on the SoapUI. To illustrate the test adaptation activities, let us consider the following simple test case given in [Fig. 7](#S0065245817300517.xhtml#f0040):

*   sut.resetGE(INVALIDURL)
*                   -> sut.checkErrorCode () = URL\_ERROR

This test has one step that calls the function to reset the data with a URL set to “INVALIDURL.” CertifyIt automatically generates the test oracle, by using an observation operation defined in the model, in our example, it is called “checkErrorCode.” For instance, the expected result of the test is the error URL\_ERROR. Further, we created a SoapUI exporter, which from the CertifyIt tool publishes the abstract test cases into concrete SoapUI projects. These projects can be imported and executed on SoapUI.

[Fig. 8](#S0065245817300517.xhtml#f0045) shows an example of four executed test cases after importing the SoapUI project. On the left side, the test cases are illustrated. On the right side, it is possible to observe the test case execution status for each step. The green color on a test step represents its successful execution status while the red color represents a failed test step. On the top, a global test pass/fail result is summarized.

![Fig. 8 SoapUI test case launch example with result status.](images/S0065245817300517/f01-08-9780128151198.jpg)

Fig. 8 SoapUI test case launch example with result status.

### 4.2 Experimentation and Results

The use case showed the feasibility of our MBT solution for the IoT conformance testing and we could show the benefits of applying the MBT approach in terms of improving the APIs interoperability, thus ensuring the conformance to the specifications. In terms of project planning, it takes 16 person-hours to create the MBT model. More specifically, it takes 4 person-hours to model the static view of the system (the class diagram) suitable for testing and 12 person-hours to model the dynamic view of the system (to write the OCL postconditions). These metrics abstract the domain knowledge from the FIWARE standards and the implementation of the specification itself. If the MBT approach is integrated within the project, the testing teams already possess this knowledge. In addition, the time spent to create the adaptation layer is linked to the developers/testers experience and it is considered as negligible. One major advantage in applying the MBT approach on the FIWARE data enabler implementation is that the test repository remains stable, while the project requirements and specification may evolve over time. Another advantage concerns the testing exhaustiveness. It is indeed impossible to test any system exhaustively. Nevertheless, it is possible, as we did, to generate a test suite that covers the test objectives in an automated and systematic way. The CertifyIt tool further allows generating reports to justify the test objective coverage, which can be easily used for auditing. This couple of examples shows the usefulness of an automated and systematic use of an MBT approach on the IoT applications that should comply to specific standards.

### 4.3 Lessons Learnt

MBT is a suitable approach for emerging technologies and especially for the IoT platforms where the maturity level and the technology development are still ongoing. First, automated and systematic test suites are conceived covering the defined test objectives. Second, the MBT further allows generating reports to justify the test objective coverage, which can be used for auditing purposes. These examples show the usefulness of such an MBT approach on applications that should comply to a standard.

## 5 MBT for IoT Security Testing

End-to-end security is used successfully today, for example, in online banking applications. Correct and complete end-to-end security in the growing IoT is required to ensure data privacy, integrity, etc. Introducing MBT to this problem may raise certain questions on the feasibility of the models being generic enough to withstand the wide range of IoT applications. It is impossible to provide an exhaustive list of all application domains of the IoT. The IoT components involved in a solution have in most common cases, a wide range of different components, such as hardware (devices, sensors, actuators, etc.), software, and network protocols. Security on their endpoints (client–server or client–client for peer-to-peer) is an absolute requirement for secure communications. Such a solution contains the following components:

*   • Identity: This component encompasses the known and verifiable entity identities on both ends.
*   • Protocols (for example, TLS): Protocols are used to dynamically negotiate the session keys, and to provide the required security functions (for example, encryption and integrity verification) for a connection. Protocols use cryptographic algorithms used to implement these functions.
*   • Cryptographic algorithms (for example, advanced encryption standard \[AES\] and secure hash algorithm \[SHA-1\]): These algorithms use the previously mentioned session keys to protect the data in transit, for example, through encryption or integrity checks.
*   • Secure implementation: The endpoint (client or server) that runs one of these protocols mentioned previously must be free of bugs that could compromise security.
*   • Secure operations: Users and operators must understand the security mechanisms, and how to manage exceptions. For example, web browsers warn about invalid server certificates, but users can override the warning and still make the connection. This concern is a nontechnical one, but is of critical concern today.

In addition, for full end-to-end security, all these components should be seen globally to ensure their security. For instance, in networks with end-to-end security, both ends can typically (depending on the protocols and algorithms used) rely on the fact that their communication is not visible to anyone else, and that no one else can modify the data in transit.

### 5.1 MBT Specificities for IoT Security Testing

In this section, to illustrate the approach, we are focusing on MBT applied to two security components: algorithms and secure operation. For a real case study, we use the steps taken by ARMOUR \[

[Fig. 9](#S0065245817300517.xhtml#f0050) depicts the E2ES scenario which combines Exp1 and Exp7. The IoT platform used in this particular scenario by Exp7 is the oneM2M standard implementation. Both data consumers/producers retrieve keys from a credential manager (CM) and the IoT platform role is to support the data storage/retrieval. However, a single security problem in any of the components involved in this scenario can compromise the overall security.

![Fig. 9 Large-scale end-to-end security scenario.](images/S0065245817300517/f01-09-9780128151198.jpg)

Fig. 9 Large-scale end-to-end security scenario.

One specificity of testing such a security scenario, MBT-wise, is that each experience has its own MBT model and the E2ES MBT model is a combination of the Exp1 and Exp7 models.

A wise integration of the experiments is made from each experience model. We call it an integration model which is used by a Business Process Model Notation (BPMN) model to generate the abstract test cases as shown in [Fig. 10](#S0065245817300517.xhtml#f0055). A standard BPMN provides businesses with the capability of understanding their internal business procedures in a graphical notation and gives organizations the ability to communicate these procedures in a standard manner. The test cases then follow the normal MBT procedure, that is, test generation and then publication. In this use case, the published tests are written as TTCN-3 \[

![Fig. 10 End-to-end security MBT description.](images/S0065245817300517/f01-10-9780128151198.jpg)

Fig. 10 End-to-end security MBT description.

#### 5.1.1 MBT Model

Each of the IoT systems are composed of producers, consumers, an IoT platform, and eventually a security service, gateways, and/or sniffer. The entities communicate through message requests (of different types) and respond to messages through message responses. This generic model, which we call the IoT MBT generic model ([Fig. 11](#S0065245817300517.xhtml#f0060)), can be created automatically from the MBT tool (CertifyIt). This model can then be customized with respect to the IoT SUT, for instance, choosing suitable names, add different types of message exchanges, configure response status codes, test patterns, delete unnecessary model elements, etc.

![Fig. 11 IoT MBT generic model.](images/S0065245817300517/f01-11-9780128151198.jpg)

Fig. 11 IoT MBT generic model.

Specifically, oneM2M is a global organization that creates requirements, architecture, API specifications, security solutions, and interoperability for machine-to-machine (M2M) and the IoT technologies. It was established through an alliance of standards organizations to develop a single horizontal platform for the exchange and sharing of data among all applications and provides functions that M2M applications across different industry segments commonly need. The service layer is developing into a critical component for future IoT architectures. The consortium consists of eight of the worlds preeminent standards development organizations, notably: ARIB (Japan), ATIS (USA), CCSA (China), ETSI (Europe), TIA (USA), TSDSI (India), TTA (Korea), and TTC (Japan). These partners collaborate with industry fora or consortia and over 200 member organizations to produce and globally maintain applicable technical specifications for a common M2M/IoT service layer. The oneM2M standard employs a simple horizontal, platform architecture that fits within a three-layer model comprising applications, services, and networks.

In the same way that consumers want to ensure that their personal and usage data are not misused, any number of stakeholders will also want to ensure that their data is protected and the services are securely delivered. Unlike the traditional internet, a typical IoT system:

*   • Inputs information about our behaviors, thus it directly exposes our privacy.
*   • Outputs adaptations to our environment, thus it potentially affects our safety.

Security is a chain that is only as strong as its weakest link; hence, all stages of a devices/services lifecycle need to be properly secured throughout its lifetime. In oneM2M, there are three layers of protection for the communications:

*   • Security Association Establishment Framework (SAEF): Adjacent entities.
*   • EndtoEnd Security of Primitive (ESPrim): Originator Hosting platform.
*   • EndtoEnd Security of Data (ESData): Data producer to data consumer.

We used in our use case, a oneM2M compliant platform (OM2M \[

![Fig. 12 Integration of the MBT model.](images/S0065245817300517/f01-12-9780128151198.jpg)

Fig. 12 Integration of the MBT model.

Here is an enumeration of the behaviors emerging from the Exp1 and Exp7 integration and that the model implements:

1.  1. The smart object requests its group key to the CM.
2.  2. The CM extracts the set of attributes of the entity from the request payload and it generates the group key associated with such a set.
3.  3. The CM sends to the smart object its group key.
4.  4. The sniffer intercepts the messages exchanged between the smart object and the CM and tries to read the group key.

The model also includes test oracles. For example: If the sniffer cannot read the group key, the test will be satisfactory. Otherwise, the test will be unsatisfactory.

To drive the test generation, a BPMN model ([Fig. 13](#S0065245817300517.xhtml#f0070)) is created.

![Fig. 13 BPMN model.](images/S0065245817300517/f01-13-9780128151198.jpg)

Fig. 13 BPMN model.

The BPMN model drives the test generation by giving some guidelines to the MBT tool for test coverage. The BPMN will ensure to test the business scenario required: test the end-to-end security of the process from key retrieval to secure encrypted data in the IoT platform.

Once all the MBT material described is in place, we proceed to the test case generation step.

#### 5.1.2 Test Case Generation

[Section 4.1.2](#S0065245817300517.xhtml#s0160) gave us some initial insight of the test case generation from the model perspective. The generation process for MBT the IoT security uses the same principles, and we will extend the study approach to the generation within the CertifyIt tool. The BPMN model ([Fig. 13](#S0065245817300517.xhtml#f0070)) allows one to generate one test case related to the end-to-end security scenario. The generated test case is shown in [Fig. 14](#S0065245817300517.xhtml#f0075). [Fig. 14](#S0065245817300517.xhtml#f0075) shows the test case details on its right-hand side. We recognize the steps introduced in the BPMN model as:

1.  1. The sensor sends a request to the CM asking for a KEY.
2.  2. The CM receives the request.
3.  3. The CM generates a KEY and sends it to the sensor.
4.  4. The sensor receives the KEY.
5.  5. The sensor encrypts its data with the received KEY.
6.  6. The sensor sends the key to the oneM2M implementation.
7.  7. The oneM2M implementation receives the encrypted value.

![Fig. 14 Test case generation with the MBT tool.](images/S0065245817300517/f01-14-9780128151198.jpg)

Fig. 14 Test case generation with the MBT tool.

The generated test case is still an abstract test as the enumerated values taken from the model are present. For example, the test oracle for the fourth test step is the “KEY\_GENERATION\_SUCCESS” code. All enumerated values need to be adapted to obtain a concrete executable test. The next session shows how this process is conducted.

#### 5.1.3 Test Case Reification

After successfully generating the tests, a conversion (or, in the CertifyIt terminology publish) into a target language is needed. The default publishers in CertifyIt are XML, Junit, and HTML. The XML publisher is the base publisher that will convert all test cases and other model data to an XML file that then can be used by other publishers to generate tests in other formats. The publisher in JUnit generates tests that can be executed in Java with a glue code, i.e., a code that will be an adapter between the SUT and the JUnit tests converting the abstract values into concrete ones. The HTML publisher serves mainly for documentation purposes because its output is simply a webpage where all steps for every test case are shown. The TTCN-3 publisher works on the same principle: the TTCN-3 generated tests are joined with an adapter file where all types, templates, functions, and components are defined. Then, we proceed to the next phase of test compilation. The TTCN-3 example generated from the model is shown in [Fig. 15](#S0065245817300517.xhtml#f0080). It follows the same structure as that generated from the model. The TTCN-3 tests start with the variables declaration. Then, the static part of the preamble is used to configure the test component. The second part of the preamble and the test body is derived from the abstract test case. The send/receive instructions are part of the test body and are detected by the naming convention that they are in fact templates, not functions. The messages used in the receive part are taken from the “observer” functions in the model.

![Fig. 15 TTCN-3 abstract test suite example.](images/S0065245817300517/f01-15-9780128151198.jpg)

Fig. 15 TTCN-3 abstract test suite example.

Once the abstract test suite (ATS) in the TTCN-3 format is obtained, executing it is the next step. To achieve this, a compiler transforming the TTCN-3 code into an intermediate language, like C++ or Java, is needed. The TTCN-3 code is abstract in a sense that it does not define the way to communicate with the SUT, or how the TTCN-3 structures will be transformed into a real format. This is a task for the system adapter (SA) and the Codec, which are described in detail in the next section. There are few commercial and noncommercial compilers that are available for download from the official TTCN-3 webpage \[

*   • Compile TTCN-3 to a target language (Titan uses C++, TTWorkbench uses Java).
*   • Add the Codec and SA written in the target language.

In the scope of this study, we show the Titan test case execution tool as it is an open-source project.

#### 5.1.4 Test Case Execution

The goal of the testing process, as described in [Fig. 10](#S0065245817300517.xhtml#f0055), is to execute the MBT-generated tests on the SUT.

As described in [Fig. 16](#S0065245817300517.xhtml#f0085), after the publication of our tests in TTCN-3, we use the Titan compiler to compile them to C/C++ code. To this code, we add the C/C++ code of the SA and the Codec. Using a makefile generated by Titan, we can compile the complete suite into a test executable. Its execution can be controlled by Titan via a configuration file explained in the following paragraphs. At the end of the execution, we obtain a log of the execution, with a status for every test case executed. The test cases results can be traced back to their test purposes and test patterns.

![Fig. 16 Test execution.](images/S0065245817300517/f01-16-9780128151198.jpg)

Fig. 16 Test execution.

Module parameters, abbreviated as modulepars, are a feature of TTCN-3 described in its specification. They are similar to constants and are used to define the parameters of a test suite. These parameters can be, for example, the address of the SUT, the timeout period, or some details of the SUT that can be chosen depending on the SUT implementation. These parameters also are called Protocol Implementation eXtra Information for Testing (PIXIT). Titan can use these module parameters inside its configuration file to provide configuration of the ATS without the need to recompile it. In the same file the user can configure the SA, for example, if it uses a UDP test port, through which system port of the test system it should send or receive the data.

TTCN-3 provides a whole structure inside a module to control the execution order of the test cases. Inside the control part, the tester has full control over the execution. He can create and start one or more components that can run the tests in parallel, and can use conditions and loops to create an execution of the test suite that is closely adapted to the needs of the SUT or the tester itself. Also, Titan widens this control by implementing a higher level of control inside the configuration file. Here, the user can specify, if there is more than one module with control parts, which module will be first to execute, which will be last, and the exact order of the test cases, etc.

Every TTCN-3 compiler has the right to implement its own method to store the test execution results in the form of a logging file. The Titan open-source compiler uses a proprietary log format from Ericsson by default, but its logging interface is very rich and thus it is not difficult to create new logging formats adapted to a user's needs. The logging facility in Titan can produce logs with various levels of details to manage different requirements for the console log and log file. The logging parameters can be configured in Titan's configuration file by setting the ConsoleMask and FileMask options, respectively, for the level of information that should be shown on the console and saved in the log file. TTCN-3 has strict control of a test case status. The five different values for test statuses are “none,” “pass,” “inconc” (short of inconclusive), “fail,” and “error.” Every time a test case is started, its status is automatically assigned to “none.” The tester, through the test case, can change it to “pass,” “inconc,” or “fail,” depending on the conditions that are defined in the test case. To prevent a failed test becoming valid, when the test case is executing and the status is set to “fail,” it cannot be reverted to “pass” or “inconc.” The same is true for “inconc,” it cannot revert to “pass.” A special status is the “error” status and it is reserved for any runtime errors to distinguish them from SUT errors.

### 5.2 Experimentation and Results

To test the end-to-end security scenario efficiently, the need for a large-scale test framework is a primordial factor as it emulates a real implementation of an IoT service. The MBT Testing Framework for Large-Scale IoT Security Testing ([Fig. 17](#S0065245817300517.xhtml#f0090)) consists of seven modules from three tool suites: CertifyIt tool suite, Titan, and FIT IoT-LAB\[

![Fig. 17 MBT testing framework for large-scale IoT security testing.](images/S0065245817300517/f01-17-9780128151198.jpg)

Fig. 17 MBT testing framework for large-scale IoT security testing.

After the MBT-generated test cases and their publication in the TTCN-3 test scripts, they are deployed in the FIT IoT-LAB ready to be executed by Titan. Titan will first compile, then adapt, and finally execute the test cases on a SUT within the FIT IoT-LAB. Results of the feasibility of the demonstrated approach have been achieved and the large-scale scenario could be demonstrated through the ARMOUR experiments. We could test the complete chain of events described in the BPMN scenario and record the messages exchanged in the testbed through the use of its integrated sniffer. The sniffer revealed that substantial portions of the messages exchanged (92%) where not ciphered. This result is further used to benchmark the security of an IoT deployment. Our experiments can safely assess that the data transiting between the sensor and the IoT platform is ciphered. This is far from optimal to conclude that the deployment is secure. We discuss more details on how our results can be used to benchmark an IoT deployment in the next session.

### 5.3 Lessons Learnt

The experiments concluded within ARMOUR have as one of the main objectives to define an approach for benchmarking security and trust technologies for experimentation on large-scale IoT deployments. In this respect, it is a major necessity to provide tools for the IoT stakeholders to evaluate the level of preparedness of their system to the IoT security threats. Benchmarking is the typical approach to this and ARMOUR will establish a security benchmark for end-to-end security in the large-scale IoT, by building up the ARMOUR large-scale testing framework and process. Additionally, ARMOUR experiments will be benchmarked using the ARMOUR benchmarking methodology. Several dimensions will be considered including

*   • Security attacks detection.
*   • Defense against attacks and misbehavior.
*   • Ability to use trusted sources and channels.
*   • Levels of security and trust conformity, etc.

Benchmark results of the large-scale IoT security and trust solutions experiments will be performed and the result datasets will be made available via the FIESTA \[

*   • Consider the methodology defined in ARMOUR for generic test patterns and test models based on the threats and vulnerability identified for the IoT and the procedure to provide test generations based on the previous one.
*   • Identify metrics per functional block (authentication, data security, etc.) to perform various micro- and macrobenchmarking scenarios on the target deployments.
*   • Collect metrics from the evaluation and then use the metrics to categorize them (taxonomy) into different functional aspects, and based on this, provide a label approach to the security assessment.

Microbenchmarks provide useful information to understand the performance of subsystems associated with a smart object. Microbenchmarks are useful to identify possible performance bottlenecks at the architectural level and allow embedded hardware and software engineers to compare and assess the various design trade-offs associated with component level design. Macrobenchmarks provide statistics relating to a specific function at the application level and may consist of multiple component level elements working together to perform an application layer task. The final objective is to provide the security benchmarking and assurance that should include a measure of our level of confidence in the conclusion. As an example of such a measure of confidence used to evaluate the security of an IoT product or system, we mention the evaluation assurance level (EAL) from the CC. The EAL is a discrete numerical grade (from EAL1 through EAL7) assigned to the IoT product or system following the completion of a CC security evaluation, which is an international standard in effect since 1999. These increasing levels of assurance reflect the fact that incremental assurance requirements must be met to achieve CC certification. The intent of the higher assurance levels is a higher level of confidence that the systems security features have been reliably implemented. The EAL level does not measure the security of the system; it rather simply states at what level the system was tested. The EALs include the following:

*   • EAL 1 Functionally tested.
*   • EAL 2 Structurally tested.
*   • EAL 3 Methodically tested and checked.
*   • EAL 4 Methodically designed, tested, and reviewed.
*   • EAL 5 Semiformally designed and tested.
*   • EAL 6 Semiformally verified design and tested.
*   • EAL 7 Formally verified design and tested.

## 6 Online MBT for IoT Robustness Testing

Robustness testing, or fuzzing, provides many diverse types of valid and invalid input to software to make it enter an unpredictable state or disclose confidential information. It works by automatically generating input values and feeding them to the software package. Fuzzing can use different input sources. The developer running the test can supply a long- or short-list of input values and can write a script that generates the input values. Also, fuzz testing software can generate input values randomly or from a specification; this is known as generation fuzzing. Traditionally, fuzzing is used and the results show that it is very effective at finding security vulnerabilities, but because of its inherently stochastic nature, the results can be highly dependent on the initial configuration of the fuzzing system.

“Practical model-based testing: A tools approach” \[

For online MBT IoT robustness testing, MBeeTle is a specific tool which is designed to combine MBT and fuzzing. MBeeTle is an independent tool based on the CertifyIt technology, whose purpose is to randomly generate test cases for test fuzzing.

Our experience in using a Fuzzing approach based on models with a tool such as MBeeTle, showed several advantages, such as:

*   • Minimal initial configuration is required to start a fuzzing campaign.
*   • Minimal supervision of the fuzzing campaign is required.
*   • Uniqueness determination is handled through an intelligent backtrace analysis.
*   • Automated test case minimization reduces the effort required to analyze the results.

The approach is complementary to other MBT testing approaches and can reveal unexpected behavior due to its random nature.

### 6.1 MBT Specificities for the IoT Robustness Testing

The MBT for the IoT robustness testing model is based on the same MBT models used for security functional and vulnerability testing; it generates test cases using behavioral fuzzing. Contrary to the previous two approaches where the test case generation aims to cover the test objectives produced from the test purposes, the MBeeTle fuzzing tool generates weighted random test cases to cover the test objectives based on the expected behavior of the system. The tool relies on the principle to rapidly generate as high as possible many fuzzed tests with a substantial number of steps in each period using a weighted random algorithm. The generated tests are valid with respect to the constraints in the MBT model. Thus, contrary to most fuzzers, the produced test cases on the one hand are syntactically correct with respect to the systems inputs. On the other hand, since it uses a weighted random algorithm and measures the coverage of the behaviors, it avoids duplication of the generated tests, which makes the test evaluation and assessment easier. Another advantage of this MBT fuzzing is its rapidity and contrary to classical functional testing approach, it explores the system states in various uncommon contexts and potentially placing the system into a failed state. [Fig. 18](#S0065245817300517.xhtml#f0095) depicts at a high level the test generation algorithm. Each step covers a test objective, which corresponds to one behavior of the system identified in the model in the OCL expression in an operation with specific preexisting tags @REQ/@AIM (illustrated in the figure). A step is generated by randomly choosing the available states possibly leading to an error from a given context of the system (for instance, start exploring the systems behavior when administrator operations are called from normal user connection). More specifically, a test step is selected only if it activates a new behavior (tag), otherwise the algorithm continues the exploration to conceive a test step that activates a new tag. The test generation stops either when the test generation time allocated to the generation engine has elapsed or by fulfilling the user conditions (for instance, all tags in the model are covered, or a stop is signaled).

![Fig. 18 Behavioral fuzzing test step selection.](images/S0065245817300517/f01-18-9780128151198.jpg)

Fig. 18 Behavioral fuzzing test step selection.

Moreover, MBT fuzzing is a complementary approach to functional and security (functional and vulnerability) testing, offering multifold benefits:

*   • it activates behaviors in uncommon contexts that potentially lead to system failures, unknown by domain experts.
*   • it rapidly generates tests, and since the algorithms are random, they are extremely quick and feedback to the user is sent rapidly (hundreds of tests in a few minutes).
*   • it reuses the same MBT model used for functional and security testing.
*   • it reuses the same adaptation layer, thus no extra effort is needed for executing the test cases.

Nevertheless, the random algorithms lack power in constructing complex contexts of the system, which is bypassed using existing valid test sequences produced using functional testing, as a preamble of the test case. Thus, it lowers its impact on the quality of the test cases.

#### 6.1.1 MBT Model

The MBT fuzzing tool (MBeeTle) uses the same model used for functional and security testing as described in step 1 of [Section 3.1](#S0065245817300517.xhtml#s0050). On a technical level, the model does not change and this is important in terms of model reusability and time-saving. On the other hand, important changes are made into the test case generation and execution.

#### 6.1.2 Test Case Generation, Reification, and Execution

The MBT robustness testing or MBT fuzzing uses an online test generation methodology. The online generation consists of executing directly produced test steps by the tool on the SUT. For each generated test step, the tool waits for its result before generating another step. If the result is not the one expected by the model, the generation process is interrupted. [Fig. 19](#S0065245817300517.xhtml#f0100) describes the online generation methodology.

![Fig. 19 Online generation methodology.](images/S0065245817300517/f01-19-9780128151198.jpg)

Fig. 19 Online generation methodology.

To communicate with the SUT in its own language and protocol, the online test generator sends its generated test steps to an adaptation layer that will translate the tests into executable steps. The result of each action taken on the SUT is traced back to the generator to decide if it should continue the test generation by exploring the model or to interrupt the process depending on the status of the last step result.

### 6.2 Future Works

The methodology introduced is fairly new and its validation is an ongoing work as of April 2017 in the ARMOUR H2020 project described previously. The main goal is to experiment with the MBT robustness testing on the large-scale testbed FIT IoT-LAB. Thus, with respect to the obtained results, we can assert the effectiveness of this methodology in real-time and on large-scale deployments.

## 7 Model-Based Testing as a Service

The IoT platforms tend nowadays to be significantly more service-oriented to user applications. The question of testing and validation of the IoT platforms can be tackled with the same “as a service” approach. This section presents the general architecture of the model-based testing as a service (MBTAAS) approach. We then present in more details, how each service works individually to publish, execute, and present the tests/results.

### 7.1 MBTAAS Architecture

An overview of the general architecture can be found in [Fig. 20](#S0065245817300517.xhtml#f0105), where we find the four main steps of the MBT approach (MBT modeling, test generation, test implementation, and execution).

![Fig. 20 MBTAAS architecture.](images/S0065245817300517/f01-20-9780128151198.jpg)

Fig. 20 MBTAAS architecture.

However, to the difference of a classical MBT process, MBTAAS implements several web services, which communicate with each other to realize the testing steps. A web service, uses web technology, such as HTTP, for machine-to-machine communication, and more specifically for transferring machine-readable file formats such as XML^([¹](#fn1))

In addition to the classical MBT process, the central piece of architecture is the database service ① that is used by all the other services. Its involvement is explained as each service is described individually. Nevertheless, the database service can be separated from all the other services, and it can be running in the cloud where it is easily accessible. The database stores essential information, such as test data (input data for test execution) and test results. The entry point of the system is the web front-end service (customization service). This service takes a user input to customize a testing session and it communicates it to a publication service ②. The purpose of the publisher service is to gather the MBT results file and user custom data to produce a customized test description file (EGM\_TAAS file). This file is then sent to an execution service ③ which controls the execution of the customized tests. It stimulates the SUT with input data to obtain a response as the SUT output data. The execution service then finally builds a result response and sends it to a last service, the reporting service. The reporting service is configured to feed the database service with the test results. These test results are used by the web front-end service to submit them to the end user. This testing architecture is executed at a modular level to respond to the heterogeneity of an IoT platform. In the following sections, a detailed description of each service is provided.

### 7.2 Customization Service

To provide user-friendly testing as a service environment, MBTAAS implements a graphical web front-end service to configure and launch the test campaigns. The customization service is a website where identified users have a private dashboard. The service offers a preconfigured test environment. The user input can be reduced to a minimum, that is: defining a SUT endpoint (URL). User specific test customization offers a wide range of adjustments to the test campaign. The web service enables

*   • Test selection: from the proposed test cases, a user can choose to execute only a part of them.
*   • Test data: preconfigured data are used for the tests. The user can add his own specific test data to the database and choose it for a test. It is a test per test configurable feature.
*   • Reporting: by default, the reporting service will store the result reported on the web front-end service database (more details on this in [Section 7.5](#S0065245817300517.xhtml#s0270)). The default behavior can be changed to fit the user needs, for example, having the results in another database, tool.

After completion of the test configuration and depressing the launch test button, a configuration file is constructed. The configuration files, as seen in [Fig. 21](#S0065245817300517.xhtml#f0110): Configuration File excerpt, defines a set of {key = value}. This file is constructed with default values that can be overloaded with user-defined values.

![Fig. 21 Configuration file excerpt.](images/S0065245817300517/f01-21-9780128151198.jpg)

Fig. 21 Configuration file excerpt.

The configuration file is one of the three components that the publisher service needs to generate the test campaign. The next section describes the publication process in more detail.

### 7.3 Publication Service

The publisher service, as its name states, publishes the abstract tests generated from the model into a concrete test description file. It requires three different inputs ([Fig. 20](#S0065245817300517.xhtml#f0105)) for completion of its task: the model, the configuration file, and the test data. The model provides test suites containing abstract tests. The concretization of the abstract tests is made with the help of a database and a configuration file. For example, the abstract value ENDPOINT\_URL taken from the model is collected from the configuration file.

The concrete test description file is for this approach, an XML file that instantiates abstract tests. The test description file has two main parts, general information and at least one test suite ([Fig. 22](#S0065245817300517.xhtml#f0115)). A test suite is composed of one or more test cases, and a test case itself is composed of one or more test steps. This hierarchy respects the IEEE 829-2008, Standard for Software and System Test Documentation.

![Fig. 22 Published file parts.](images/S0065245817300517/f01-22-9780128151198.jpg)

Fig. 22 Published file parts.

The general informational part of the file is useful to execute the tests ([Section 7.4](#S0065245817300517.xhtml#s0265)) and report the results. Here are some of the most important parameters that can be found in that part of the file:

*   • Owner: used for traceability purposes. It allows one to know who is the detainer of the test to present it in his personal cloud dashboard.
*   • Sut\_endpoint: the hostname/IP address of the SUT. This address should be reachable from the execution service point of view.
*   • Location: the hostname/IP address of the reporting service ([Section 7.5](#S0065245817300517.xhtml#s0270)).

The test suites contain all useful test information. In this case, the IoT platform proposes HTTP-based RESTful applications. The mandatory information required to succeed a RESTful query are the URL (SUT endpoint) and the HTTP method (GET, POST, PUT, DELETE). The test suite and test cases purpose is the ordering and naming of the test, but the test information and test data are stored in the test steps. Each test step has its own configuration. Once the file is published, it is sent to the execution service to execute the tests.

### 7.4 Execution Service

The execution service is the functional core of the MBTAAS architecture. The execution service will run the test and collect the results depending on the configuration of the received test description file. The FIWARE RESTful interface tests are executed with the REST execution module. Each test is run against the SUT and a result report ([Listing 1](#S0065245817300517.xhtml#b0015)) is constructed on the test step completion. The result report contains information on the date-time of execution, time spent executing the step and some other test specific values. The “endpoint” represents the URL value and validity of where the step should be run. An invalid endpoint would allow one to skip the type check on the endpoint value and thus allow ne to acquire an execution error. The response of each step is validated within the “assertion\_list” tags (test oracle). It validates each assertion depending on the assertion type and values against the received response.

Listing 1:

Test step result report

*   < teststep   name = " UpdateEntity1 " >
*          < executionResults >
*                    < timestamp > { TIMESTAMP } < / timestamp >
*             < executionTimeMs > 22 < / executionTimeMs >
*          < / executionResults >
*          < endpoint >
*                < value > { IP } : { PORT }/ upContext < / value >
*                < isinvalid > false < / isinvalid >
*          < / endpoint >
*          < method > POST < / method >
*          < headers > { HEADERS } < / headers >
*          < payload > { PAYLOAD } < / payload >
*          < assertion\_list >
*                < assertion >
*                           < type > JSON < / type >
*                           < key > code < / key >
*                        < value > 404 < / value >
*                        < result > false < / result >
*                < / assertion >
*          < / assertion\_list >
*          < result > false < / result >
*          < response > {
*                 " errorCode "   :   {
*                       " code "   :   " 400 " ,
*                       " reasonPhrase "   :   " Bad   Request " ,
*                       " details "   :   " JSON   Parse   Error "
*                 }
*          }
*          < / response >
*   < / teststep >

[Fig. 23](#S0065245817300517.xhtml#f0120) shows an excerpt of the execution service log. To execute one test step, the endpoint (URL) must be validated. Then, a RESTful request is created and executed. A response is expected for the assertions to be evaluated. Finally, an overall test result is computed. The overall assertion evaluation algorithm is as simple as: “All test assertions must be true,” which implies if one assertion is false, the test is marked as failed.

![Fig. 23 Execution snapshot.](images/S0065245817300517/f01-23-9780128151198.jpg)

Fig. 23 Execution snapshot.

Once the execution service has finished all test steps, their results are gathered within one file, this file is called test results, and it is sent to the reporting service.

### 7.5 Reporting Service

After executing the test, a file containing the test description alongside the results is sent to and received by the reporting service. The reporting service configuration is made on the web front-end service. The configuration is passed with the test configuration file where the publisher service retranscribes that information to the file sent to the execution service. The execution service then includes the reporting configuration in the report file where it is used in the reporting service once it receives it. By default, the reporting service will save the results in the database service ①. For this use case, the database is implemented as a MySQL database. This database is then used by the web front-end service to present the test results to the user.

MBTAAS has proven to be generic enough to be integrated with little effort for the IoT conformance, security, and robustness testing.

## 8 Lessons Learnt and Discussion

The work and results presented in this chapter is a combination of multiple work done in the domain of MBT for the IoT systems testing. We provided a demonstration of the capabilities of an MBT approach adapted to the IoT platform conformance and security testing. Results of their application are encouraging to move forward and bring the service layer to it.

The initial cost in applying MBT in general is usually high, due to: (i) the time spent on the models conception and (ii) the first implementation of an adaptation layer for test execution that can be complex depending on the SUT. This high initial cost of implementing MBT can be rewarded if we consider that the project requirements and specification may evolve in its development cycle. In this later case, the MBT for the IoT platforms can keep the test repository stable. This leads us to conclude that MBT is a suitable approach for emerging technologies and standards, especially on the IoT platforms where the maturity level is still increasing while technology development is still ongoing. Being able to generate tests automatically and in a systematic way, as we did, makes it possible to constitute a test suite covering the defined test objectives. The MBT further offers the means to format the results into automated reports to justify the test objective coverage, which can be easily used for certification and labeling purposes. These several examples show the usefulness of an automated and systematic use of an MBT approach on applications that should comply to specific standards. Regarding the security point of view, where new vulnerabilities are emerging faster than security experts can predict them, MBT allows the integration of new vulnerability patterns with little cost to an ongoing test campaign. Combined with a user-friendly and easily accessible interface through a service-oriented solution, the first experiments with MBTAAS show that it is a promising and powerful tool. The reusability of the service approach is a strong and solid factor for its adoption. The only changes to be made concern the test environment and the adaptation layer, to make it compatible with any IoT component under test. One major concern is to provide the tests to the community in the easiest way possible. It provides to all (not only testers) the capacity to test their components remotely using an online service. The service provides to users a test-friendly interface that simplifies the test execution tools installation and the various technical challenges with respect to system incompatibilities, such as networking access problems.

The newly introduced MBT fuzzing method does not follow the standard fuzzing testing methods. Its goal in the IoT testing is to extensively use the MBT model to generate random test steps, thus ensuring a deeper exploration of requirements coverage. There are no malformed test steps in this process. The objective is to ensure the correct behavior of the tested SUT over its lifetime span as it enables stress testing over an extended period of time. The new method has yet to prove its effectiveness in a large-scale testbed.

 

## 9 Conclusion

This chapter presented the state of the art on MBT of the IoT systems and described specific challenges and MBT solutions for the IoT testing.

More specifically, it provided answers that address the key challenges of scalability, interoperability, and security of the IoT with real use cases. The solutions that we proposed have a common execution approach: MBTAAS. The MBT used for the IoT conformance testing shows that the specificities in generating test cases to validate the correct behavior of an SUT with respect to its standard lies in the model creation. In this case, the model is a representation of the standard. Any test executed on the SUT that fails could represent a gap between the specification and implementation, or a compliance from the SUT toward the standard it is implementing. The MBT used for the IoT security testing diverted from the traditional MBT setup with its specific test case reification environment. Finally, we had a first view on the specificities of an MBT for the IoT robustness testing approach. It illustrates how MBT fuzzing could be applied to the IoT systems. The tooling we presented gives the possibility to reuse the already created model during the functional/security testing phase; thus, no additional time is spent for modeling. This approach is considered as complimentary to security or conformance testing, as we expect that the detected inconstancies will differ from the others.

The standardization institutes and certification entities that make available tomorrows standards have the process of testing as the highest importance. They provide standard implementers a set of test cases to assess the conformance, scalability, and security of their products. Test cases traceability after execution is also a major factor as it is used to benchmark the test results. With security threats constantly evolving, and to maintain high confidence and trust, the proposed test cases must be continuously maintained. This is where MBT finds its interest and added value. The traceability starts with the specification, then the requirements, and finally to the test cases which are an embedded feature to that of the classical MBT approach. The test case traceability provided by MBT gives the possibility to implement test generation strategies which aim to cover a maximum of the specification. The automated test generation is low time-consuming comparing to hand written tests, and thus makes the maintenance of generated test cases cheaper. MBT has major advantages in terms of test coverage, test maintenance, etc. Those advantages are accelerating the adoption of MBT over time.

The MBT approach for test case generation and execution is relatively new. Nowadays, it is becoming more and more visible and accepted compared to 10/15 years ago. The approach was previously reserved for a smaller number of use cases due to the high difficulty of taking in hand the modeling. Modeling requires highly skilled testers and at the time the profession was not common in the software industry. Only highly critical companies had the privilege of modeling their concepts to test them. The IoT sector is reaching this critical level nowadays. Security intrusions are more sophisticated than ever and occur more frequently then we realize. The need for quality assurance in the field of the IoT testing is essential to accompany its growth. With MBT, the evolution of the security threads is added into the model and they are by this process considered in the test generation process. The process saves time when it is not started from scratch. The models for conformance testing are reusable and adapted to security testing. MBT shows its benefits in the medium to long term as it has a high initial cost and it has been one of the strongest roadblocks for MBT adoption. The MBT approach requires highly skilled testers and it is complicated to change the daily habits of testers in the field. It requires a significant time investment that most are not willing to partake. One other roadblock for the MBT approach adoption is the complexity of the existing tools. Nevertheless, MBT is still relatively new and we see more and more tools emerging. However, these tools require a high degree of formation and skill for practical usage. The test generation tools are complicated and the complexity of test generation can take a significant amount of time (NP-complete problems). In the future, the MBT approach requires significant evolution to survive and show a rise in its adoption. New techniques have already been developed by tool makers, as seen in [Section 6](#S0065245817300517.xhtml#s0220), MBeeTle is one of the emerging tools for online testing that responds to the need for a real-time analysis of the test cases on the IoT deployments. This new tool allows for a loss of nondeterminism in a real-time system.

To conclude, the technology for automated model-based test case generation has matured to the point where the large-scale deployments of this technology are becoming commonplace. The prerequisites for success, such as qualification of the test team, integrated tools chain availability and methods are now identified, and a wide range of commercial and open-source tools are available, as introduced in this chapter. Although MBT will not solve all testing problems in the IoT domain, it is extremely useful and brings considerable progress within the state of the practice for functional software testing effectiveness, increasing productivity, and improving functional coverage. Moreover, the MBT approach has shown its importance in the IoT by introducing an ease of access to conformance, security, and robustness testing. The technology is constantly evolving, making it tester friendly and considerably reducing the high initial cost that is typically the case. Because of its easier accessibility for testers, as well as more fine-grained integration with the large-scale IoT testbeds, MBT should expect a larger approval rate.

## Acknowledgments

This research was supported by the ARMOUR project Grant ID 688237 of the Horizon 2020 Call ICT-12-2015 Integrating experiments and facilities in FIRE+. We would like to thank Dr. Cedric ADJIH, Dr. José Luis Hernández RAMOS, and Sara Nieves Matheu GARCIA for sharing their valuable insights with us.

## References

\[1\] *DYN DDoS Attack Report.* 2017. [http://www.computerworld.com/article/3135434/security/ddos-attack-on-dyn-came-from-100000-infected-devices.html](http://www.computerworld.com/article/3135434/security/ddos-attack-on-dyn-came-from-100000-infected-devices.html) (last visited April 2017).

\[2\] Binder R.V., Legeard B., Kramer A. Model-based testing: where does it stand? *Commun. ACM.* 0001-07822015;58(2):52–56. doi:10.1145/2697399.

\[3\] Baldini G., Skarmeta A., Fourneret E., Neisse R., Legeard B., Gall F.L. Security certification and labelling in Internet of Things. In: 2016:627–632. *2016 IEEE 3rd World Forum on Internet of Things (WF-IoT).*.

\[4\] Kramer A L.B. *Model-Based Testing Essentials—Guide to the ISTQB Certified Model-Based Tester: Foundation Level.* Wiley; 2016.

\[5\] Capgemini. *World Quality Report 2016-17.* 2016.

\[6\] *Model-Based Engineering Forum.* 2017. [http://modelbasedengineering.com/](http://modelbasedengineering.com/) (last visited April 2017).

\[7\] Utting M., Legeard B. *Practical Model-Based Testing—A Tools Approach.* San Francisco, CA: Morgan Kaufmann; 2006 ISBN 0123725011.

\[8\] Spillner A., Linz T., Schaefer H. *Software Testing Foundations: A Study Guide for the Certified Tester Exam: Foundation Level, ISTQB Compliant.* CA: Santa Barbara; 2014.

\[9\] Hartman A. *Model Based Test Generation Tools.* Agedis Consortium; 2002. [http://www.agedis.de/documents/ModelBasedTestGenerationTools\_cs.pdf](http://www.agedis.de/documents/ModelBasedTestGenerationTools_cs.pdf).

\[10\] Budnik C., Subramanyan R., Vieira M. Peer-to-Peer Comparison of Model-Based Test. In: *GI Jahrestagung.* 2008.

\[11\] Shafique M., Labiche Y. A Systematic Review of Model Based Testing Tool Support. *Technical Report SCE-10-04.* Canada: Carleton University; 2010.

\[12\] Marinescu R., Seceleanu C., Guzen H.L., Pettersson P. *A Research Overview of Tool-Supported Model-based Testing of Requirements-Based Designs.* Elsevier; 2015.89–140.

\[13\] Utting M., Pretschner A., Legeard B. A taxonomy of model-based testing approaches. *Soft. Test. Verif. Reliab.* 1099-16892012;22(5):297–312. doi:10.1002/stvr.456.

\[14\] Utting M., Legeard B., Bouquet F., Fourneret E., Peureux F., Vernotte A. Chapter Two—Recent Advances in Model-Based Testing. In: Elsevier; 53–120. *Advances in Computers.* 2016;vol. 101.

\[15\] E.S. Reetz, Service testing for the Internet of things (Ph.D. thesis), University of Surrey, 2016.

\[16\] IBM, Model-Based Testing (MBT) at InterConnect 2016? Yes! [https://www.ibm.com/developerworks/community/blogs/35dfcb99-111b-423a-aaa4-50f3fddae141/entry/Model\_Based\_Testing\_MBT\_at\_InterConnect\_2016\_Yes?lang=en](https://www.ibm.com/developerworks/community/blogs/35dfcb99-111b-423a-aaa4-50f3fddae141/entry/Model_Based_Testing_MBT_at_InterConnect_2016_Yes?lang=en), (accessed 06.03.17).

\[17\] I. Schieferdecker, J.A. Gromann, A. Rennoch, Model Based Security Testing Selected Considerations (keynote at SECTEST at ICST 2011), [http://www.avantssar.eu/sectest2011/pdfs/Schieferdecker-invited-talk.pdf](http://www.avantssar.eu/sectest2011/pdfs/Schieferdecker-invited-talk.pdf), (accessed 25.09.12).

\[18\] Schieferdecker I., Grossmann J., Schneider M. Model-Based Security Testing. In: 2012:1–12. doi:10.4204/EPTCS.80.1. *MBT.*.

\[19\] Larsen K.G., Mikucionis M., Nielsen B. Online testing of real-time systems using UPPAAL. In: Grabowski J., Nielsen B., eds. *Formal Approaches to Software Testing. FATES 2004.* Berlin, Heidelberg: Springer; . *Lecture Notes in Computer Science.* 2005;vol. 3395.

\[20\] Kriouile A., Serwe W. Using a formal model to improve verification of a cache-coherent system-on-chip. In: Baier C., Tinelli C., eds. *Tools and Algorithms for the Construction and Analysis of Systems.* Berlin, Heidelberg: Springer; 708–722. *Lecture Notes in Computer Science.* 2015;vol. 9035.

\[21\] Schneider M., Gromann J., Schieferdecker I., Pietschker A. Online model-based behavioral fuzzing. In: 2013:469–475. *2013 IEEE Sixth International Conference on Software Testing, Verification and Validation Workshops.*.

\[22\] *CompleteTest.* 2017. [http://www.completetest.org/about/](http://www.completetest.org/about/) (last visited April 2017).

\[23\] Larsen K.G., Pettersson P., Yi W. UPPAAL in a nutshell. *Int. J. Softw. Tools Technol. Transfer.* 1997;1:134–152.

\[24\] *Eclipse Formal Modeling Project.* 2017. [https://projects.eclipse.org/proposals/eclipse-formal-modeling-project](https://projects.eclipse.org/proposals/eclipse-formal-modeling-project) (last visited April 2017).

\[25\] Faivre A., Gaston C., Gall P. *Symbolic Model Based Testing for Component Oriented Systems.* Springer; 2007.

\[26\] *FMBT.* 2017. [https://01.org/fmbt/](https://01.org/fmbt/) (last visited April 2017).

\[27\] *HTG.* 2017. [https://sites.google.com/site/htgtestgenerationtool/home](https://sites.google.com/site/htgtestgenerationtool/home) (last visited April 2017).

\[28\] *Netlist Syntax.* 2017. [http://fides.fe.uni-lj.si/spice/netlist.html](http://fides.fe.uni-lj.si/spice/netlist.html) (last visited April 2017).

\[29\] LaValle S.M., Branicky M.S., Lindemann S.R. On the relationship between classical grid search and probabilistic roadmaps. *Int. J. Robot. Res.* 2004;doi:10.1177/0278364904045481.

\[30\] *Lurrette.* 2017. [http://www-verimag.imag.fr/Lurette,107.html](http://www-verimag.imag.fr/Lurette,107.html) (last visited April 2017).

\[31\] Raymond P., Roux Y., Jahier E. Lutin: a language for specifying and executing reactive scenarios. *EURASIP J. Embed. Syst.* 2008;2008(1):753821.

\[32\] *Lustre V6.* 2017. [http://www-verimag.imag.fr/Lustre-V6.html](http://www-verimag.imag.fr/Lustre-V6.html) (last visited April 2017).

\[33\] *MISTA—Model-Based Testing.* 2017. (last visited April 2017) [http://cs.boisestate.edu/dxu/research/MBT.html](http://cs.boisestate.edu/dxu/research/MBT.html).

\[34\] *Modbat.* 2017. [https://people.kth.se/artho/modbat/](https://people.kth.se/artho/modbat/) (last visited April 2017).

\[35\] *Momut.* 2017. [https://momut.org/](https://momut.org/) (last visited April 2017).

\[36\] W. Herzner, R. Schlick, A. Austrian, H. Br, J. Wiessalla, F.F. Aachen, Towards fault-based generation of test cases for dependable embedded software.

\[37\] *PragmaDev—Modeling and Testing Tools.* 2017. [http://pragmadev.com/](http://pragmadev.com/) (last visited April 2017).

\[38\] *Tcases.* 2017. [https://github.com/Cornutum/tcases](https://github.com/Cornutum/tcases) (last visited April 2017).

\[39\] Sanchez J. *A Review of Pair-Wise Testing.* Springer; 2016.

\[40\] Muniz L.L., Netto U.S.C., Maia P.H.M. TCG—A Model-based Testing Tool for Functional and Statistical Testing. *ICEIS.* 2015.

\[41\] *LoTuS.* 2017. [http://jeri.larces.uece.br/lotus/](http://jeri.larces.uece.br/lotus/) (last visited April 2017).

\[42\] *Vera.* 2017. [http://www.spacios.eu/index.php/spacios-tool/](http://www.spacios.eu/index.php/spacios-tool/) (last visited April 2017).

\[43\] *Smartesting CertifyIt.* 2017. [http://www.smartesting.com/en/certifyit/](http://www.smartesting.com/en/certifyit/) (last visited April 2017).

\[44\] *IBM—Rational Software Architect Designer.* 2017. [http://www-03.ibm.com/software/products/en/ratsadesigner](http://www-03.ibm.com/software/products/en/ratsadesigner) (last visited April 2017).

\[45\] Neisse R., Baldini G., Steri G., Ahmad A., Fourneret E., Legeard B. Improving Internet of Things device certification with policy-based management. In: 2017. *2017 Global Internet of Things Summit (GIoTS).*.

\[46\] *FIWARE.* 2017. [https://www.fiware.org/](https://www.fiware.org/) (last visited April 2017).

\[47\] *OAuth 2.0.* 2017. [https://oauth.net/2/](https://oauth.net/2/) (last visited April 2017).

\[48\] Alliance O.M. *NGSI Context Management.* 2012. [http://technical.openmobilealliance.org/Technical/release\_program/docs/NGSI/V1\_0-20120529-A/OMA-TS-NGSI\_Context\_Management-V1\_0-20120529-A.pdf](http://technical.openmobilealliance.org/Technical/release_program/docs/NGSI/V1_0-20120529-A/OMA-TS-NGSI_Context_Management-V1_0-20120529-A.pdf).

\[49\] Fourneret E., Cantenot J., Bouquet F., Legeard B., Botella J. SeTGaM: generalized technique for regression testing based on UML/OCL models. In: 2014:147–156. *8th International Conference on Software Security and Reliability, SERE, 2014.*.

\[50\] *ARMOUR H2020 Project.* 2017. [http://www.armour-project.eu/](http://www.armour-project.eu/) (last visited April 2017).

\[51\] The Testing and Test Control Notation Version 3 (TTCN-3), [http://www.ttcn-3.org/](http://www.ttcn-3.org/) (last visited April 2017).

\[52\] *OM2M, oneM2M Standard Implementation.* 2017. [http://www.eclipse.org/om2m/](http://www.eclipse.org/om2m/) (last visited April 2017).

\[53\] *FIT IoT Lab, Large Scale Testbed.* 2017. [https://www.iot-Iab.info/](https://www.iot-Iab.info/) (last visited April 2017).

\[54\] *FIESTA Testbed.* 2017. [http://fiesta-iot.eu/](http://fiesta-iot.eu/) (last visited April 2017).

![u01-01-9780128151198](images/S0065245817300517/u01-01-9780128151198.jpg)

**Abbas Ahmad**, a PhD student at Easy Global Market, has a master's degree in computer sciences from the University of Franche-Comté. He specialized his master's degree in “Design and development of secure software.” He has accomplished a 6-month internship at Airbus Operations SAS, in the R&D department where he developed IATT (Isami Analyst Testing Tool), a nonregression test tool. He also has an ISTQB® (International Software Testing Qualifications Board) foundation level certification, an ISTQB® Model-Based Tester foundation, a FIWARE developer's week Brussels diploma, and a TTCN-3 certificate in test automation. With a strong knowledge of software and application testing, he also has been a FIWARE friendly tester during 4 months, where he tested the FIWARE cloud portal and some Generic Enablers. One of his achievements is wining first prize of the Internet of Things Hackathon during the IoT Week (Lisbon 2015). He is now running a PhD thesis in the field of model-based testing for IoT systems.

![u01-02-9780128151198](images/S0065245817300517/u01-02-9780128151198.jpg)

**Fabrice Bouquet** studied computer sciences and received his PhD degree in University of Provence, France in 1999. He is a lecturer during high years, and since 2008, he has been a full professor at the University of Franche-Comté, France. His research interests in validation of complex systems from requirements to model include operational semantic, testing, model transformation, and functional and nonfunctional properties with applications in vehicle, aircraft, smart objects, and energy.

![u01-03-9780128151198](images/S0065245817300517/u01-03-9780128151198.jpg)

**Elizabeta Fourneret** is a Project Manager at Smartesting. She has strong experience in the field of security testing based on models. She leads several R&D projects at Smartesting oriented on functional and security testing for critical systems, such as HSM (Hardware Security Modules), and IoT systems. Within the scope of the ongoing H2020 ARMOUR project on large-scale experiments of IoT Security & Trust she is leading the Large-Scale Testing Framework development.

She has received her PhD degree in Computer Science in the domain on model-based regression testing of security-critical systems at the National Research Institute in Computer Science and Automation—INRIA—Nancy, France and her MSc degree in Software Verification and Validation at the University of Franche-Comté in Besançon, France.

![u01-04-9780128151198](images/S0065245817300517/u01-04-9780128151198.jpg)

**Bruno Legeard** is a Professor at UBFC, Institut FEMTO-ST, Scientific Advisor, and cofounder of Smartesting. Bruno has more than 20 years’ expertise in Model-Based Testing/Model-Based Security Testing (MBT/MBST) and its introduction in the industry. His research activities mainly concern features about automation of Model-Based Test case generation using AI techniques. His research results in more than 100 scientific and industrial publications based on MBT and MBST. He is the author of three books disseminating Model-Based Testing in the industry. “Practical Model-Based Testing” has more than 1200 citations.

* * *

Chapter Two 

# Advances in Software Model Checking

Junaid H. Siddiqui; Affan Rauf; Maryam A. Ghafoor    ^()Lahore University of Management Sciences, Lahore, Pakistan

## Abstract

Society is becoming increasingly dependent on software which results in an increasing cost of software malfunction. At the same time, software is getting increasingly complex and testing and verification are becoming harder and harder. Software model checking is a set of techniques to automatically check properties in a model of the software. The properties can be written in specialized languages or be embedded in software in the form of exceptions or assertions. The model can be explicitly provided in a specification language, can be derived from the software system, or the software system itself can be used as a model. Software model checkers check the given properties in a large number of states of the model. If a model checker is able to verify a property on all model states, it is proven that the property holds and the model checker works like a theorem prover. If a model checker is unable to verify a property on all model states, the model checker is still an efficient automated testing technique.

This chapter discusses advances in software model checking and focuses on techniques that use the software as its model and embedded exceptions or assertions as the properties to be verified. Such techniques are most likely to be widespread in the software industry in the coming decade due to their minimal overhead on the programmer and due to recent advances in research making these techniques scale.

### Keywords

Model checking; Symbolic execution; Bounded model checking; Explicit-state model checking; Abstraction-based model checking; Safety properties; Liveness properties; Schedule nondeterminism; Input nondeterminism; Concurrent systems

## 1 Introduction

As software pervades our societies and lives, the need for software reliability grows more and more. With computers controlling airplanes and running financial markets, the cost of even a single software failure can be quite high. Failures already cost the U.S. economy $59.5 billion every year \[

With an exponential increase in the complexity of software, manual testing is become increasing less effective. Commercial software is often released with a large number of known bugs. Manual testing exercises a very small number of states the software can be in.

Formal verification of software strives to formulate the verification problem mathematically and solve it. There are two essential ways to achieve it: using theorem proving and using model checking.

Theorem proving attempts to build a formal proof of the correctness of the system with the help of the programmer. For example, loop invariants are deduced or provided by the programmer that remain true regardless of the number of iterations of the loop. The theorem prover uses these invariants to prove properties of the system. In essence, the properties are proved to be true for every state of the system. However, theorem proving has been limited to small programs and often requires extensive and laborious input from the programmer.

On the other hand, model checking checks properties of the system on a large number of states, thus verifying the properties for only these states. The work of a model checker on a single state is easy, but generalizing the result to all states is difficult. For example, in a particular state, a program loop would have run a fixed number of times, and it is apparent if a particular error state is reached or not.

There are two fundamental variations of model checking: bounded model checking and abstraction-based model checking. In bounded model checking, the number of states is bounded, e.g., by limiting the maximum number of conditional statements on a path. The finite number of states can be searched using either stateful search or stateless search. [Section 2](#S0065245817300505.xhtml#s0030) discusses bounded model checking. Bounded model checking is an effective technique to find software bugs but it cannot prove the absence of bugs. Advances in bounded model checking enable identifying equivalent states, or treating multiple states as one, resulting in checking more states in less time. An extreme of treating multiple states as one is to divide the problem in a fixed number of abstract states with each abstract state representing possibly infinite states. The divisions are done based on a certain property, e.g., if a Boolean variable is true or false. Any properties checked on these finite states are true for all states, but any errors found may not be real errors in a concrete system.

A lot of model checking work is concentrated on checking properties of concurrent systems and the state space explosion resulting from thread interleavings. External inputs are often provided by an alternate test input generation system and the model checker exercises all given input choices. Symbolic execution is a technique to systematically check properties of systems over all input choices. It converts the program path in an SMT (satisfiability modulo theory) formula to solve and generate inputs that are guaranteed to exercise different paths. Due to loops, most programs have an infinite number of paths. Bounded symbolic execution exercises a bounded number of states. Recent advances have brought abstraction-based techniques to symbolic execution in some specific cases.

Model checking is often used for increasing software quality. While testing suffers from the problem of generating a good test suite and verification or proving program correctness is limited to small programs, model checking enables systematic exploration of a large number of program states, thus providing better guarantees of software quality than testing but still applies to much larger programs and verifies more general properties than verification.

### 1.1 Properties

The properties to be checked in a software system can be broadly classified into safety properties and liveness properties \[

In this survey, we will focus on safety properties. Safety properties can be formulated as a reachability problem. Particular error locations in the program (e.g., assert statements inserted by the programmer) signify a bad state. If we guarantee that an assert statement is unreachable, we have shown that the program satisfies a safety property.

In bounded model checking, we verify that the safety properties are held in the bounded number of states but we cannot prove that the properties are held in general. In symbolic model checking, we verify that the safety property is held in general but if a violation is found, we cannot always prove that the violation is true for the specific system under test.

### 1.2 Soundness and Completeness

A sound algorithm for safety property verification declares programs safe with respect to some safety property that are truly safe. A complete algorithm for safety property verification declares all truly safe programs with respect to some safety property as safe. No sound and complete algorithm can solve the verification problem in general due to the undecidability of the halting problem \[

### 1.3 Schedule Nondeterminism and Input Nondeterminism

Programs change their state as they execute, usually in a deterministic manner. However, when executing a conditional statement, the program state can possibly change in two different ways. The inputs to the program indirectly determine if one or both branches are feasible to execute. This is called input nondeterminism. Also, for concurrent programs, the state can change in n different ways if there are n active threads. This is called schedule nondeterminism.

Fundamentally, state search for both schedule nondeterminism and input nondeterminism is identical. However, the techniques to prune equivalent states or use symbolic states (that represent a number of concrete states) are different for both. Traditionally, techniques focusing on schedule nondeterminism have been called model checkers while those focusing on input nondeterminism in a symbolic way are called symbolic execution tools. Traditional model checkers handle input nondeterminism by exploring all given input choices without symbolic abstraction resulting in state space explosion.

## 2 Explicit-State Bounded Model Checking

Bounded model checking checks all states of the system under test within some bounds. The states are concrete or explicit, i.e., actual states the program can be in. Explicit-state model checking for any program with loops has to be bounded because the number of explicit states are infinite in a program with loops. Model checking is a search of the graph formed by program states and transitions. For concurrent systems, it deals with exploration of all possible interleaving of processes leading to state space explosion for larger set of processes. In general, concurrent events are modeled by exploring all possible interleaving of events relative to each process which results in a large set of paths with many states on each path. Each path represents one unique interleaving of processes. There are two fundamental techniques to search the state space: stateless and stateful.

### 2.1 Stateful Search

In stateful search, the graph of program states and transitions is explicitly made and explored. The graph is finite due to the bounds on the bounded search. If no state reaches the error location, the given safety property is verified.

Stateful search keeps a worklist of states, and in each iteration, takes an element from the worklist and applies the next transitions to it. The updated state or states are added back to the worklist. The choice of next element from the worklist determines whether a depth-first or a breadth-first technique is used. Many model checkers use a heuristic-based choice that favors exploring new lines of code in anticipation of finding a fault.

Even within small bounds, the number of states grows exponentially and the resulting problem is called state space explosion. Dealing with the number of states is one of the key research challenges in model checking. To reduce the number of states, equivalence groups are found such that a bug in any state of the group will be reflected in all states of the group. The two primary techniques for this are symmetry reduction and partial order reduction (POR).

### 2.2 Symmetry Reduction

Symmetry reduction techniques identify symmetries in process order, communication order, and the structure of specifications to identify equivalence classes of states where a single representative state is enough to find bugs in any of the states in the equivalence class \[

### 2.3 Partial Order Reduction

POR is an optimization technique that exploits the fact that many paths are redundant, as they are formed due to the execution of independent transitions in different orders. Another way to understand it is considering that many concurrent operations are commutative, i.e., they result in the same state. POR is the identification and pruning of transitions that will result in identical states. Model checkers that include state comparison to avoid duplicate states still benefit from POR because of the early exclusion of transition rather than generating and comparing states.

Model checkers employ POR to avoid unnecessary exploration of schedules. POR addresses the problem of state explosion for concurrent systems by reducing the size of state space to be searched by model checking software. POR \[

### 2.4 Execution-Based Search

Verisoft \[

The advantage of execution-based search is that any error state found is accompanied by a complete execution trace with inputs and schedule to reach the error state. Furthermore, no translation of the software into a modeling language or translation of programming language semantics into state transitions is required.

Execution-based model checkers mostly use inputs generated from an external test suite (generated automatically using another technique or manually) and exercise different schedules on those inputs. Input choices are not explored using the model checker as it results in an enormous number of states. Covering input domains efficiently requires using symbolic states using, e.g., symbolic execution.

The key challenge of execution-based model checkers is storing the state. Being execution-based, their state is the entire program state. Java PathFinder (JPF) \[

### 2.5 Stateless Search

Verisoft also introduced the idea of stateless search. Instead of explicitly storing a worklist of states and applying one transition to the state, stateless search works by forcing the program on a particular schedule. At every nondeterministic choice, e.g., thread schedule or user input, the execution queries the scheduler, and the scheduler provides the next number in the schedule, an integer in a finite domain of active threads or finite domain of valid input values.

After an execution is finished, the next schedule is formed by effectively incrementing the last schedule. The very last nondeterministic choice is changed to the next value in the domain and if the choices are exhausted, the second last nondeterministic choice is changed. Eventually, all choices are explored.

Like other tools in the execution-based category, Verisoft cannot practically explore input domains as it results in a very large number of states. It focuses on exploring input schedules.

The key advantage of stateless search is the minimal requirements on state storage. However, the main disadvantage is the inability to identify duplicate states or adapt complex heuristic-based search orders that are possible when states are explicitly stored.

### 2.6 Tools and Recent Advancements

The first famous explicit-state model checkers with stateful search were the SPIN model checker \[

Verisoft introduced stateless execution-based model checking. It observes processes that communicates using interprocess communication (IPC) primitives. By trapping calls to IPC primitives, the Verisoft scheduler is able to influence the schedule in which different processes proceed.

JPF is an explicit-state model checker which explores different interleavings of threads by selecting a thread nondeterministically from a set of live threads. In order to explore all possible schedules, JPF uses the choice generator on thread operations. JPF generates schedules on the basis of calls to initialization and termination of these threads by executing the statements of the thread until the thread finishes the execution.

JPF executes Java byte code instructions from the application on its own virtual machine (VM). JPF has listeners which get notified by the VM whenever a specific operation is performed. These listeners can be used to perform a specific operation and/or to further control the execution of the program. JPF explores states of the program along all possible paths and whenever end of path is reached, it backtracks to explore other unexplored paths.

Other popular execution-based model checking tools include CMC and CHESS. CMC (C model checker) uses the OS scheduler to explore different interleavings. It hashes the state to identify similar states in an attempt to prioritize new states. CMC has been used to successfully find bugs in real systems \[

JPF-SE \[

### 2.7 Parallel Model Checking

Stern and Dill's parallel Murphi \[

A similar technique was used by Lerda and Visser \[

Parallel Randomized State Space Search for JPF by Dwyer et al. \[

Ranged model checking \[

### 2.8 Model Checking in Other Domains

Model checking has also been used for web applications \[

For model checking of database operations, Paleari et al. \[

Emmi and Majumdar \[

## 3 Symbolic Execution

When dealing with external inputs, explicit-state model checking produces a lot of different but unnecessary states. For example, the symbolic expression x < 5 represents all states in which x is less than 5. An explicit-state model checker has to exercise all these states individually even if the states exercise the same path in code.

Symbolic execution is a technique to use symbolic states for program input. At every conditional statement, two symbolic states are formed with different clauses. When the program ends, there is a clause in the state for every conditional statement on the path executed by the program.

Symbolic execution relies on SAT (satisfiability theory) or SMT (satisfiability modulo theory) solvers to solve the set of clauses in each state, also called path conditions. Solving the path condition is NP-complete but heuristic-based solvers are able to solve most path conditions in a reasonable time. If paths reaching error states are solvable, a safety property violation is found.

Symbolic execution was developed over three decades ago \[

A lot of progress has been made during the last decade in constraint solving technology, in particular SAT \[

Forward symbolic execution is a technique for executing a program on symbolic values \[

[Program 1](#S0065245817300505.xhtml#b0010) contains a function that finds the middle of three integer values. [Fig. 1](#S0065245817300505.xhtml#f0010) shows the execution tree of this program and shows the six path conditions explored. The path conditions for each of these paths can be solved using off-the-shelf SAT solvers for concrete tests that exercise the particular path. For example, path 2 can be solved to X = 1, Y = 3, and Z = 2. Following are all the six paths explored:

Program 1

To find middle of three integers

*   1    int mid(int x, int y, int z) {
*   2         if (x<y) {
*   3            if (y<z) return y;
*   4            else if (x<z) return z;
*   5            else return x;
*   6         } else if (x<z) return x;
*   7         else if (y<z) return z;
*   8         else return y; }

![Fig. 1 Execution tree of Program 1.](images/S0065245817300505/f02-01-9780128151198.jpg)

Fig. 1 Execution tree of [Program 1](#S0065245817300505.xhtml#b0010).

```
Path 1: [X < Y < Z] L2 -> L3
Path 2: [X < Z < Y] L2 -> L3 -> L4
Path 3: [Z < X < Y] L2 -> L3 -> L4 -> L5
Path 4: [Y < X < Z] L2 -> L6
Path 5: [Y < Z < X] L2 -> L6 -> L7
Path 6: [Z < Y < X] L2 -> L6 -> L7 -> L8
```

### 3.1 Stateful Symbolic Execution

PREfix \[

KLEE \[

### 3.2 Stateless Symbolic Execution

Just like bounded model checking techniques, symbolic execution can be implemented in an stateless tool. In a stateless execution-based approach, the state comprises of concrete variable values (like explicit-state model checkers) in addition to the symbolic formulas for each variable. The concrete values satisfy the corresponding symbolic formula. The effect of each program statement is updated on both the concrete values and the symbolic values. When a conditional statement is encountered, the program proceeds in whatever direction the concrete values take it and the conditional clause is added to the path condition. When an execution finishes, the last clause in the path condition is negated (or the path before if the last one has already been negated) to arrive at a path condition for a yet unexplored path. The SAT solver is used to solve this path condition and the concrete values thus found guide the next execution.

Traditional or forward symbolic execution uses SAT solver to find if error paths are truly feasible or not while stateless or back-tracking-based symbolic execution uses the SAT solver to find concrete values that will drive the next execution on a different path.

Symbolic execution guided by concrete inputs has been a topic of extensive investigation during the last 7 years. DART \[

### 3.3 Symbolic Bounded Model Checking

Symbolic bounded model checking uses a search algorithm similar to explicit-state bounded model checking but uses symbolic states representing a number of explicit states. Unlike symbolic execution, the symbolic states do not have a mapping over program paths. The symbolic states are formed over program variables and a single formula is formed for all paths in a symbolic state.

Symbolic execution enumerates paths and uses the solver to solve those path conditions, whereas symbolic bounded model checking unroll the control flow graph up till a particular depth and form a single formula for a given symbolic state about reachability of an error location. In this way the program computations are all formulated and backtracked inside the solver.

CBMC \[

Other early bounded model checkers in this category include F-Soft \[

ESBMC \[

Scaling bounded model checking for large programs is a challenging problem. Blitz \[

Due to complexities of a high-level language, it becomes difficult to apply model checking directly on the source code. LLBMC \[

Concurrency errors manifest themselves with a few context switches. Therefore, context-bounded verification tools limit the number of context switches. Sequentialization is a technique that translates a concurrent program into an equivalent nondeterministic sequential program by replacing control nondeterminism with data nondeterminism. Lazy sequentialization \[

### 3.4 Ranged and Incremental Symbolic Execution

Due to the nature of various model checking algorithms, every code change invalidates prior results and a new analysis has to be run. Due to the pace at which software changes, analysis results often become obsolete very soon. However, a lot of work from prior runs can be efficiently utilized since most of the code remains unchanged. Incremental techniques try to leverage this pattern and make incremental analysis faster.

Ranged symbolic execution \[

Ranged symbolic execution enables symbolic exploration between two given paths. For example, if path 2 and path 4 of the earlier example are given, it can explore paths 2, 3, and 4. It only needs the concrete solution that satisfies the corresponding path condition. Therefore it is efficient to store and pass paths. This is shown in [Fig. 2](#S0065245817300505.xhtml#f0015) and the general idea of dividing search in ranges is shown in [Fig. 3](#S0065245817300505.xhtml#f0020).

![Fig. 2 Symbolic execution between paths ρ and ρ′.](images/S0065245817300505/f02-02-9780128151198.jpg)

Fig. 2 Symbolic execution between paths ρ and ρ′.

![Fig. 3 High-level overview of dividing symbolic execution into nonoverlapping ranges for independent symbolic executions. (A) Standard symbolic execution. (B) Ranged symbolic execution (four ranges). (C) Only boundaries redundantly analyzed.](images/S0065245817300505/f02-03-9780128151198.jpg)

Fig. 3 High-level overview of dividing symbolic execution into nonoverlapping ranges for independent symbolic executions. (A) Standard symbolic execution. (B) Ranged symbolic execution (four ranges). (C) Only boundaries redundantly analyzed.

Incremental symbolic execution applies symbolic execution in increments based on versions of code \[

Directed incremental symbolic execution \[

Directed Incremental Symbolic Execution (DiSE) \[

Katch \[

Green \[

GreenTrie \[

Memoized symbolic execution \[

Conc-iSE \[

### 3.5 Parallel Symbolic Execution

A couple of recent research projects have proposed techniques for parallel symbolic execution \[

KleeNet \[

### 3.6 Other Advancements in Symbolic Execution

Hybrid concolic testing \[

Staged symbolic execution \[

Symbolic execution for Alloy models \[

Symbolic Execution of stored procedures in database management systems \[

Postconditioned symbolic execution tries to mitigate the path explosion problem by a new redundancy removal method. At each branching location, in addition to determine the feasibility of a particular branch, it also checks whether the branch is subsumed by previous explorations \[

Zou et al. \[

Wang et al. \[

Feist et al. \[

Symbolic PathFinder \[

Braione et al. \[

Ibing \[

## 4 Abstraction-Based Model Checking

Abstraction-based model checking for checking safety properties performs abstract reachability analysis. The analysis is performed on abstract states that capture some but not all of the state of the program. Each concrete program operation becomes an abstract operation performing a subset of the effects in the real program. Abstract states can be formed by removing variables from the state or dividing their values into domains (e.g., positive, zero, negative). The goal of abstraction is to make the number of states finite while retaining the variables relevant to proving a particular property.

Abstract model checking performs the same model checking algorithm as previously discussed on the simplified graph of abstract states and abstract transitions. Unlike explicit-state model checking a counterexample found (e.g., error state reachable) may not be a real counterexample. On the other hand, if there is no way to reach the error state in the abstract graph, then we are guaranteed that there is no way to reach the error state in the real program. Thus abstraction-based model checking is sound in general but not complete.

In the most common form, predicate abstraction \[

### 4.1 Abstraction Refinement

Abstraction-based model checking can return spurious counterexamples. Refinement focuses to identify if the counterexample is true in the real program.

Abstracting too much increases the chances of finding spurious counterexamples and abstracting too little increases the number of states exponentially. Counterexample guided refinement techniques attempt to get the best of both worlds by starting with too much abstraction and as soon as a counterexample is found, find a way to add more details to the state such that the counterexample no longer remains valid. Thus precision is added on an as-needed basis. CEGAR (counter-example guided abstraction refinement) \[

### 4.2 Tools and Recent Advancements

SLAM and BLAST are well-known model checkers that use predicate-based abstraction and the CEGAR loop. SLAM \[

BLAST \[

CPAChecker \[

Other model checkers based on abstraction include the MAGIC model checker \[

## 5 Conclusions

Software model checking has advanced in the last few decades from research ideas working on small specialized examples to working on real large programs finding actual bugs. Execution-based model checkers enable using the software system as its own model without the need to write specifications or perform an error-prone translation of the program into its specifications. Furthermore, model checkers can use programmer inserted assertions as a specification of safety properties, thus eliminating the need to provide a separate set of specifications.

Explicit-state model checkers keep an explicit-program state in memory while symbolic model checkers keep a symbolic state that represents a number of explicit states. Stateless model checkers backtrack over a schedule to exercise all program states and stateful model checkers explicitly keep all to be explored program states in memory. Symmetry reduction and POR enable identifying equivalent states, thus covering a reduced number of states while maintaining the bug finding ability. Finally, abstract model checkers divide the state space into a finite number of abstract states to be able to prove properties instead of focusing on finding bugs. Counterexample refinement techniques attempt to identify if the bugs found in an abstract state are real program bugs or not.

Software model checking will likely gain much wider significance in the coming decades. It hits the sweet spot between theorem proving targeting both soundness and completeness and random testing targeting neither. By aiming at one of soundness or completeness and more importantly following a systematic process of exploring software states, a lot of arbitrariness associated with random testing is avoided and a lot of scalability is gained.

Software model checking still suffers from state space explosion and the cost of systematically exploring a number of states. However, in the past decade, it has progressively been applied to larger and more complex software and the trend is likely to continue in the coming years. Advances in software model checkers introduce heuristics to make the search more effective, address scalability, e.g., by making the process parallel or incremental, or increase soundness or completeness in specific cases. Software model checkers are now able to verify properties in very large programs and expected to become integrated in the average developer's tool chain in the coming decades.

Specific reasons why model checking is not widely used in software industry include time taken for analysis, false positives and false negatives, and limitations of model checking for software requiring external interaction. All of these are active areas of research with scalability receiving the most attention as it is the biggest hurdle. New data sources need to be tapped to add supplemental information that can direct the systematic search and make it more scalable. Some ideas recently explored include taking hints from software histories, bug repositories, comments, and design patterns.

Apart from scalability, another key challenge for software model checking is checking of user interfaces and interacting with external nondeterministic sources. Progress has been made in this direction in recent years with techniques attempting to verify user interfaces, to verify the impact of language translations on user interfaces, and to interact with external systems in a more deterministic way, e.g., using proxies or by remembering past responses. Despite the progress, model checking software with external interfaces remains a challenging area and the coming decade is likely to bring new ideas and better solutions.

Model checking will also need to catchup with new and resurgent software paradigms including agent-driven, event-driven, and functional paradigms. Event-driven has received the most attention in recent years, especially in the context of web systems, but there are still challenges in handling the large number of event sequences possible and separating the most important sequences in a systematic way.

While model checking is becoming increasingly useful for verification, it will likely play a much broader role in software development in the coming decades. Techniques likes automated fault localization, automated repair, programming by sketching, software construction from specifications, and other emerging ideas often depend on systematic search techniques as an enabling technology and these techniques are slowing gaining prominence. One example is recent approaches in automated repair that apply repair while software is being written and give repair suggestions as hints just like semantic compiler hints. This requires a highly scalable and heuristic systematic search. Model checking needs to cope with these challenges, and once it does, it will likely become a fundamental part of the software development process.

Model checking has grown in scalability and new applications but attempts to combine the various model checking approaches have been few and far between. This is likely one of the most promising directions of radical improvements in scalability of software model checking and its applications to significantly larger systems. A fundamental limitation is that researchers are often specialized in a particular model checking technique, whereas model checking techniques have been heavily borrowing ideas from programming languages and compiler design community and from hardware model checking and from pure mathematics that underlies many of the programming language calculus. A more interdisciplinary approach taking ideas from a variety of domains with a unified focus is needed to take software model checking to the next level.

## References

\[1\] National Institute of Standards and Technology. *The Economic Impacts of Inadequate Infrastructure for Software Testing.* 2002 Planning report 02-3.

\[2\] Woodcock J. First steps in the verified software grand challenge. *Computer.* 2006;39:57–64.

\[3\] Alpern B., Schneider F.B. *Recognizing Safety and Liveness.* Ithaca, NY: Technical report; 1986.

\[4\] Turing A. On computable numbers with an application to the Entscheidungsproblem. *Proc. Lond. Math. Soc.* 1937;s2-42(1):230–265.

\[5\] Clarke E.M., Filkorn T., Jha S. Exploiting symmetry in temporal logic model checking. In: London, UK: Springer-Verlag; 1993:3-540-56922-7450–462. *Proceedings of the 5th International Conference on Computer Aided Verification, CAV ’93.*. [http://dl.acm.org/citation.cfm?id=647762.735503](http://dl.acm.org/citation.cfm?id=647762.735503).

\[6\] Emerson E.A., Sistla A.P. Symmetry and model checking. *Formal Methods Syst. Des.* 1572-81021996;9(1):105–131. doi:10.1007/BF00625970.

\[7\] Flanagan C., Godefroid P. Dynamic partial-order reduction for model checking software. In: New York, NY: ACM; 110–121. *ACM Sigplan Notices.* 2005;vol.40.

\[8\] Godefroid P., van Leeuwen J., Hartmanis J., Goos G., Wolper P. *Partial-Order Methods for the Verification of Concurrent Systems: An Approach to the State-Explosion Problem.* Berlin, Heidelberg: Springer-Verlag; . 1996;vol. 1032.

\[9\] Clarke E.M., Grumberg O., Minea M., Peled D. State space reduction using partial order techniques. *Int. J. Softw. Tools Technol. Transfer.* 1999;2(3):279–287.

\[10\] Godefroid P. Model checking for programming languages using VeriSoft. In: 1997:174–186. *Proc. 24th Symposium on Principles of Programming Languages (POPL).*. [http://portal.acm.org/ft\_gateway.cfm?id=263717&type=pdf&coll=GUIDE&dl=GUIDE&CFID=54069747&CFTOKEN=82180120](http://portal.acm.org/ft_gateway.cfm?id=263717&type=pdf&coll=GUIDE&dl=GUIDE&CFID=54069747&CFTOKEN=82180120).

\[11\] Visser W., Havelund K., Brat G., Park S. Model checking programs. In: 2000:3. *Proc. 15th International Conference on Automated Software Engineering (ASE).*. [http://portal.acm.org/ft\_gateway.cfm?id=786967&type=external&coll=GUIDE&dl=GUIDE&CFID=52387804&CFTOKEN=40229725](http://portal.acm.org/ft_gateway.cfm?id=786967&type=external&coll=GUIDE&dl=GUIDE&CFID=52387804&CFTOKEN=40229725).

\[12\] Holzmann G.J. The model checker SPIN. *IEEE Trans. Softw. Eng.* 0098-55891997;23(5):279–295. doi:10.1109/32.588521.

\[13\] Dill D.L. The Murphi verification system. In: London, UK: Springer-Verlag; 1996:3-540-61474-5390–393. *Proceedings of the 8th International Conference on Computer Aided Verification, CAV ’96.*. [http://dl.acm.org/citation.cfm?id=647765.735832](http://dl.acm.org/citation.cfm?id=647765.735832).

\[14\] Musuvathi M., Engler D.R. Model checking large network protocol implementations. In: Berkeley, CA: USENIX Association; 2004. *Proceedings of the 1st Conference on Symposium on Networked Systems Design and Implementation—Volume 1, NSDI’04.*. [http://dl.acm.org/citation.cfm?id=1251175.1251187](http://dl.acm.org/citation.cfm?id=1251175.1251187) pp. 12–12.

\[15\] Yang J., Twohey P., Engler D., Musuvathi M. Using model checking to find serious file system errors. *ACM Trans. Comput. Syst.* 0734-20712006;24(4):393–423. doi:10.1145/1189256.1189259.

\[16\] Musuvathi M., Qadeer S. Iterative context bounding for systematic testing of multithreaded programs. In: New York, NY: ACM; 2007:978-1-59593-633-2446–455. doi:10.1145/1250734.1250785. *Proceedings of the 28th ACM SIGPLAN Conference on Programming Language Design and Implementation, PLDI ’07.*.

\[17\] Qadeer S., Rehof J. *Context-bounded model checking of concurrent software.* Berlin, Heidelberg: Springer; 2005.978-3-540-31980-193–107. doi:10.1007/978-3-540-31980-1\_7.

\[18\] Anand S., Păsăreanu C.S., Visser W. JPF-SE: a symbolic execution extension to Java PathFinder. In: Springer; 2007:134–138. *International Conference on Tools and Algorithms for the Construction and Analysis of Systems.*.

\[19\] Jayaraman K., Harvison D., Ganesh V., Kiezun A. jFuzz: a concolic whitebox fuzzer for java. In: *Proceedings of the First NASA Formal Methods Symposium, April.* 2009:121–125.

\[20\] van der Merwe H., van der Merwe B., Visser W. Verifying android applications using Java PathFinder. *ACM SIGSOFT Softw. Eng. Notes.* 2012;37(6):1–5.

\[21\] Rehman W.U., Ayub M.S., Siddiqui J.H. Verification of MPI Java programs using software model checking. In: New York, NY: ACM; 2016:978-1-4503-4092-255:1–55:32. doi:10.1145/2851141.2851192. *Proceedings of the 21st ACM SIGPLAN Symposium on Principles and Practice of Parallel Programming, PPoPP ’16.*.

\[22\] Stern U., Dill D.L. Parallelizing the Murphi verifier. In: London, UK: Springer-Verlag; 1997:3-540-63166-6256–278. *CAV ’97: Proceedings of the 9th International Conference on Computer Aided Verification.*.

\[23\] Visser W., Havelund K., Brat G., Park S. Model checking programs. In: Washington, DC: IEEE Computer Society; 2000:0-7695-0710-73. *ASE ’00: Proceedings of the 15th IEEE International Conference on Automated Software Engineering.*.

\[24\] Lerda F., Visser W. Addressing dynamic issues of program model checking. In: New York, NY: Springer-Verlag, Inc.; 2001:3-540-42124-680–102. *SPIN ’01: Proceedings of the 8th International SPIN Workshop on Model Checking of Software.*.

\[25\] Holzmann G.J. The model checker SPIN. *IEEE Trans. Softw. Eng.* 0098-55891997;23(5):279–295. doi:10.1109/32.588521.

\[26\] Lerda F., Sisto R. Distributed-memory model checking with SPIN. In: London, UK: Springer-Verlag; 1999:3-540-66499-822–39. *Proceedings of the 5th and 6th International SPIN Workshops on Theoretical and Practical Aspects of SPIN Model Checking.*.

\[27\] Holzmann G.J., Bosnacki D. The design of a multicore extension of the SPIN model checker. *IEEE Trans. Softw. Eng.* 2007;33(10):659–674.

\[28\] Holzmann G.J. Parallelizing the spin model checker. In: Springer; 2012:155–171. *International SPIN Workshop on Model Checking of Software.*.

\[29\] Jones M.D., Sorber J. Parallel search for LTL violations. *Int. J. Softw. Tools Technol. Transf.* 1433-27792005;7(1):31–42. doi:10.1007/s10009-003-0115-8.

\[30\] Kumar R., Eric D., Mercer G., Quinn D., Snell O., Bryan D., Morse S., University B.Y., University B.Y., Embley W., Bryce G.R., Dean A. Load balancing parallel explicit state model checking. *Electr. Notes Theor. Comput. Sci.* 2005;128:19–34.

\[31\] Palmer R., Gopalakrishnan G. A distributed partial order reduction algorithm. In: London, UK: Springer-Verlag; 2002:3-540-00141-7370. *FORTE ’02: Proceedings of the 22nd IFIP WG 6.1 International Conference Houston on Formal Techniques for Networked and Distributed Systems.*.

\[32\] Dwyer M.B., Elbaum S., Person S., Purandare R. Parallel randomized state-space search. In: Washington, DC: IEEE Computer Society; 2007:0-7695-2828-73–12. doi:10.1109/ICSE.2007.62. *ICSE ’07: Proceedings of the 29th International Conference on Software Engineering.*.

\[33\] Funes D., Siddiqui J.H., Khurshid S. Ranged model checking. *SIGSOFT Softw. Eng. Notes.* 0163-59482012;37(6):1–5. doi:10.1145/2382756.2382799.

\[34\] Petrov B., Vechev M., Sridharan M., Dolby J. Race detection for web applications. In: 2012:978-1-4503-1205-9251–262. *Proceedings of the 33rd ACM SIGPLAN Conference on Programming Language Design and Implementation, PLDI ’12.*.

\[35\] Martin M., Lam M.S. Automatic generation of XSS and SQL injection attacks with goal-directed model checking. In: 2008:31–43. *Proceedings of the 17th Conference on Security Symposium, SS’08.*.

\[36\] Artzi S., Kiezun A., Dolby J., Tip F., Dig D., Paradkar A., Ernst M.D. Finding bugs in web applications using dynamic test generation and explicit-state model checking. *IEEE Trans. Softw. Eng.* 0098-55892010;36(4):474–494.

\[37\] R. Paleari, D. Marrone, D. Bruschi, M. Monga, On race vulnerabilities in web applications, in: Proceedings of the 5th International Conference on Detection of Intrusions and Malware, and Vulnerability Assessment, DIMVA ’08.

\[38\] Zheng Y., Zhang X. Static detection of resource contention problems in server-side scripts. In: 2012:978-1-4673-1067-3584–594. *Proceedings of the 34th International Conference on Software Engineering, ICSE ’12.*.

\[39\] Emmi M., Majumdar R., Sen K. Dynamic test input generation for database applications. In: 2007:151–162. *Proceedings of the 2007 International Symposium on Software Testing and Analysis.*.

\[40\] Marcozzi M., Vanhoof W., Hainaut J.-L. *Testing Database Programs Using Relational Symbolic Execution, Technical report, University of Namur.* 2014.

\[41\] Pan K., Wu X., Xie T. Database state generation via dynamic symbolic execution for coverage criteria. In: ACM; 2011:4. *Proceedings of the Fourth International Workshop on Testing Database Systems.*.

\[42\] Khalek S.A., Khurshid S. Systematic testing of database engines using a relational constraint solver. In: 2011:50–59. *2011 IEEE Fourth International Conference on Software Testing, Verification and Validation (ICST).*.

\[43\] Pan K., Wu X., Xie T. Generating program inputs for database application testing. In: IEEE; 2011:73–82. *2011 26th IEEE/ACM International Conference on Automated Software Engineering (ASE).*.

\[44\] Wassermann G., Yu D., Chander A., Dhurjati D., Inamura H., Su Z. Dynamic test input generation for web applications. In: 2008:978-1-60558-050-0249–260. *Proceedings of the 2008 International Symposium on Software Testing and Analysis, ISSTA ’08.*.

\[45\] Felmetsger V., Cavedon L., Kruegel C., Vigna G. Toward automated detection of logic vulnerabilities in web applications. In: 2010:10. *Proceedings of the 19th USENIX Conference on Security, USENIX Security’10.* ISBN 888-7-6666-5555-4.

\[46\] Ghafoor M.A., Mahmood M.S., Siddiqui J.H. Effective partial order reduction in model checking database applications. In: 2016:146–156. doi:10.1109/ICST.2016.25. *2016 IEEE International Conference on Software Testing, Verification and Validation (ICST).*.

\[47\] Clarke L.A. A system to generate test data and symbolically execute programs. *IEEE Trans. Softw. Eng.* 1976. ;2(3):215–222. [http://portal.acm.org/ft\_gateway.cfm?id=1313532&type=external&coll=Portal&dl=GUIDE&CFID=50149523&CFTOKEN=17299335](http://portal.acm.org/ft_gateway.cfm?id=1313532&type=external&coll=Portal&dl=GUIDE&CFID=50149523&CFTOKEN=17299335).

\[48\] King J.C. Symbolic execution and program testing. *Commun. ACM.* 1976. ;19(7):385–394. [http://portal.acm.org/ft\_gateway.cfm?id=360252&type=pdf&coll=Portal&dl=GUIDE&CFID=50149523&CFTOKEN=17299335](http://portal.acm.org/ft_gateway.cfm?id=360252&type=pdf&coll=Portal&dl=GUIDE&CFID=50149523&CFTOKEN=17299335).

\[49\] Barrett C., Tinelli C. CVC3. In: 2007:298–302. *Proc. 19th International Conference on Computer Aided Verification (CAV).*.

\[50\] de Moura L., Bjørner N. Z3: an efficient SMT solver. In: 2008:337–340. doi:10.1007/978-3-540-78800-3\_24. *International Conference on Tools and Algorithms for the Construction and Analysis of Systems (TACAS).*.

\[51\] Sörensson N., Een N. An extensible SAT-solver. In: 2003:502–518. *Proc. 6th International Conference on Theory and Applications of Satisfiability Testing (SAT).*.

\[52\] Khurshid S., Pasareanu C.S., Visser W. Generalized symbolic execution for model checking and testing. In: 2003:553–568. *Proc. 9th International Conference on Tools and Algorithms for the Construction and Analysis of Systems (TACAS).*. [http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.8.8862](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.8.8862).

\[53\] Godefroid P., Klarlund N., Sen K. DART: directed automated random testing. In: 2005:213–223. *Proc. 2005 Conference on Programming Languages Design and Implementation (PLDI).*. [http://portal.acm.org/ft\_gateway.cfm?id=1065036&type=pdf&coll=Portal&dl=GUIDE&CFID=50151101&CFTOKEN=70334910](http://portal.acm.org/ft_gateway.cfm?id=1065036&type=pdf&coll=Portal&dl=GUIDE&CFID=50151101&CFTOKEN=70334910).

\[54\] Sen K., Marinov D., Agha G. CUTE: a concolic unit testing engine for C. In: 2005:263–272. *Proc. 5th Joint Meeting of the European Software Engineering Conference and Symposium on Foundations of Software Engineering (ESEC/FSE).*. [http://portal.acm.org/ft\_gateway.cfm?id=1081750&type=pdf&coll=Portal&dl=GUIDE&CFID=50151101&CFTOKEN=70334910](http://portal.acm.org/ft_gateway.cfm?id=1081750&type=pdf&coll=Portal&dl=GUIDE&CFID=50151101&CFTOKEN=70334910).

\[55\] Cadar C., Dunbar D., Engler D.R. KLEE: unassisted and automatic generation of high-coverage tests for complex systems programs. In: 2008:209–224. *Proc. 8th Symposium on Operating Systems Design and Implementation (OSDI).*.

\[56\] Ramos D.A., Engler D.R. Practical, low-effort equivalence verification of real code. In: 2011:669–685. *Proc. 23rd International Conference on Computer Aided Verification (CAV).*.

\[57\] Elkarablieh B., Garcia I., Suen Y.L., Khurshid S. Assertion-based repair of complex data structures. In: 2007:64–73. *Proc. 22nd International Conference on Automated Software Engineering (ASE).*.

\[58\] Seo C., Malek S., Medvidovic N. Component-level energy consumption estimation for distributed java-based software systems. In: 2008:97–113. *Proc. 11th International Symposium on Component-Based Software Engineering.*.

\[59\] L.A. Clarke, Test data generation and symbolic execution of programs as an aid to program validation (Ph.D. thesis), University of Colorado at Boulder, 1976.

\[60\] Bush W.R., Pincus J.D., Sielaff D.J. A static analyzer for finding dynamic programming errors. *Softw. Pract. Experience.* 2000. ;30(7):775–802. [https://doi.org/10.1002/(SICI)1097-024X(200006)30:73C775::AID-SPE3093E3.0.CO;2-H](https://doi.org/10.1002/\(SICI\)1097-024X\(200006\)30:73C775::AID-SPE3093E3.0.CO;2-H).

\[61\] Adve V., Lattner C., Brukman M., Shukla A., Gaeke B. LLVA: a low-level virtual instruction set architecture. In: 2003:205–216. *Proc. 36th International Symposium on Microarchitecture (MICRO).*.

\[62\] Godefroid P. Compositional dynamic test generation. In: 2007:47–54. *Proc. 34th Symposium on Principles of Programming Languages (POPL).*.

\[63\] Cadar C., Engler D. Execution generated test cases: how to make systems code crash itself. In: 2005:2–23. *Proc. International SPIN Workshop on Model Checking of Software.*.

\[64\] Cadar C., Ganesh V., Pawlowski P.M., Dill D.L., Engler D.R. EXE: automatically generating inputs of death. In: 2006:322–335. doi:10.1145/1180405.1180445. *Proc. 13th Conference on Computer and Communications Security (CCS).*.

\[65\] Clarke E., Kroening D., Yorav K. Behavioral consistency of C and Verilog programs using bounded model checking. In: New York, NY: ACM; 2003:1-58113-688-9368–371. doi:10.1145/775832.775928. *Proceedings of the 40th Annual Design Automation Conference, DAC ’03.*.

\[66\] Clarke E., Kroening D., Lerda F. A tool for checking ANSI-C programs. In: Springer; 2004:168–176. *International Conference on Tools and Algorithms for the Construction and Analysis of Systems.*.

\[67\] Kroening D., Tautschnig M. CBMC-C bounded model checker. In: Springer; 2014:389–391. *International Conference on Tools and Algorithms for the Construction and Analysis of Systems.*.

\[68\] Ivančić F., Yang Z., Ganai M.K., Gupta A., Ashar P. Efficient SAT-based bounded model checking for software verification. *Theor. Comput. Sci.* 0304-39752008;404(3):256–274. doi:10.1016/j.tcs.2008.03.013.

\[69\] Xie Y., Aiken A. Scalable error detection using Boolean satisfiability. In: New York, NY: ACM; 2005:1-58113-830-X351–363. doi:10.1145/1040305.1040334. *Proceedings of the 32nd ACM SIGPLAN-SIGACT Symposium on Principles of Programming Languages, POPL ’05.*.

\[70\] Babic D., Hu A.J. Calysto: scalable and precise extended static checking. In: New York, NY: ACM; 2008:978-1-60558-079-1211–220. doi:10.1145/1368088.1368118. *Proceedings of the 30th International Conference on Software Engineering, ICSE ’08.*.

\[71\] Cordeiro L., Fischer B., Marques-Silva J. SMT-based bounded model checking for embedded ANSI-C software. *IEEE Trans. Softw. Eng.* 2012;38(4):957–974.

\[72\] Cho C.Y., D’Silva V., Song D. Blitz: compositional bounded model checking for real-world programs. In: IEEE; 2013:136–146. *2013 IEEE/ACM 28th International Conference on Automated Software Engineering (ASE).*.

\[73\] Falke S., Merz F., Sinz C. The bounded model checker LLBMC. In: IEEE; 2013:706–709. *2013 IEEE/ACM 28th International Conference on Automated Software Engineering (ASE).*.

\[74\] Inverso O., Tomasco E., Fischer B., La Torre S., Parlato G. Lazy-CSeq: a lazy sequentialization tool for C. In: Springer; 2014:398–401. *International Conference on Tools and Algorithms for the Construction and Analysis of Systems.*.

\[75\] Siddiqui J.H., Khurshid S. Scaling symbolic execution using ranged analysis. In: New York, NY: ACM; 2012:978-1-4503-1561-6523–536. doi:10.1145/2384616.2384654. *Proceedings of the ACM International Conference on Object Oriented Programming Systems Languages and Applications, OOPSLA ’12.*.

\[76\] Person S., Yang G., Rungta N., Khurshid S. Directed incremental symbolic execution. In: 2011:504–515. *Proc. 2011 Conference on Programming Languages Design and Implementation (PLDI).*.

\[77\] Marinescu P.D., Cadar C. KATCH: high-coverage testing of software patches. In: 2013. *Proc. 12th Joint Meeting of the European Software Engineering Conference and Symposium on Foundations of Software Engineering (ESEC/FSE).*.

\[78\] Visser W., Geldenhuys J., Dwyer M.B. Green: reducing, reusing and recycling constraints in program analysis. In: 2012. *Proc. 2012 Joint Meeting of the European Software Engineering Conference and Symposium on Foundations of Software Engineering (ESEC/FSE).*.

\[79\] Jia X., Ghezzi C., Ying S. Enhancing reuse of constraint solutions to improve symbolic execution. In: ACM; 2015:177–187. *Proceedings of the 2015 International Symposium on Software Testing and Analysis.*.

\[80\] Yang G., Păsăreanu C.S., Khurshid S. Memoized symbolic execution. In: 2012:978-1-4503-1454-1144–154. doi:10.1145/2338965.2336771. *Proc. 2012 International Symposium on Software Testing and Analysis (ISSTA), ISSTA 2012.*.

\[81\] Guo S., Kusano M., Wang C. Conc-iSE: incremental symbolic execution of concurrent software. In: IEEE; 2016:531–542. *2016 31st IEEE/ACM International Conference on Automated Software Engineering (ASE).*.

\[82\] Siddiqui J.H., Khurshid S. ParSym: parallel symbolic execution. In: 2010:V1405–V1409. *Proc. 2nd International Conference on Software Technology and Engineering (ICSTE).*.

\[83\] Staats M., Pǎsǎreanu C. Parallel symbolic execution for structural test generation. In: 2010:183–194. *Proc. 19th International Symposium on Software Testing and Analysis (ISSTA).*.

\[84\] Godefroid P., Levin M.Y., Molnar D.A. Automated whitebox fuzz testing. In: 2008. *Proc. Network and Distributed System Security Symposium (NDSS).*.

\[85\] Sasnauskas R., Landsiedel O., Alizai M.H., Weise C., Kowalewski S., Wehrle K. KleeNet: discovering insidious interaction bugs in wireless sensor networks before deployment. In: 2010:186–196. *Proc. 9th International Conference on Information Processing in Sensor Networks (ISPN 2010).*.

\[86\] Majumdar R., Sen K. Hybrid concolic testing. In: 2007:416–426. *Proc. 29th International Conference on Software Engineering (ICSE).*.

\[87\] Siddiqui J.H., Khurshid S. Staged symbolic execution. In: New York, NY: ACM; 2012:978-1-4503-0857-11339–1346. doi:10.1145/2245276.2231988. *Proceedings of the 27th Annual ACM Symposium on Applied Computing, SAC ’12.*.

\[88\] Siddiqui J.H., Khurshid S. Scaling symbolic execution using staged analysis. *Innov. Syst. Softw. Eng.* 1614-50462013;9(2):119–131. doi:10.1007/s11334-013-0196-9.

\[89\] Siddiqui J.H., Khurshid S. Symbolic execution of alloy models. In: Berlin, Heidelberg: Springer-Verlag; 2011:978-3-642-24558-9340–355. *Proceedings of the 13th International Conference on Formal Methods and Software Engineering, ICFEM ’11.*. [http://dl.acm.org/citation.cfm?id=2075089.2075119](http://dl.acm.org/citation.cfm?id=2075089.2075119).

\[90\] Jackson D. *Software Abstractions: Logic, Language, and Analysis.* The MIT Press; 2006.

\[91\] Mahmood M.S., Abdul Ghafoor M., Siddiqui J.H. Symbolic execution of stored procedures in database management systems. In: New York, NY: ACM; 2016:978-1-4503-3845-5519–530. doi:10.1145/2970276.2970318. *Proceedings of the 31st IEEE/ACM International Conference on Automated Software Engineering, ASE 2016.*.

\[92\] Yi Q., Yang Z., Guo S., Wang C., Liu J., Zhao C. Eliminating path redundancy via postconditioned symbolic execution. *IEEE Trans. Softw. Eng.* 2017;doi:10.1109/TSE.2017.2659751. [http://ieeexplore.ieee.org/document/7835264/](http://ieeexplore.ieee.org/document/7835264/).

\[93\] Zou Q., Huang W., An J., Fan W. Redundant constraints elimination for symbolic execution. In: IEEE; 2016:235–240. *Information Technology, Networking, Electronic and Automation Control Conference.*.

\[94\] Wang H., Liu T., Guan X., Shen C., Zheng Q., Yang Z. Dependence guided symbolic execution. *IEEE Trans. Softw. Eng.* 2017;43(3):252–271.

\[95\] Feist J., Mounier L., Potet M.-L. Guided dynamic symbolic execution using subgraph control-flow information. In: Springer; 2016:76–81. *International Conference on Software Engineering and Formal Methods.*.

\[96\] Păsăreanu C.S., Rungta N. Symbolic PathFinder: symbolic execution of Java bytecode. In: ACM; 2010:179–180. *Proceedings of the IEEE/ACM international Conference on Automated Software Engineering.*.

\[97\] Rosner N., Geldenhuys J., Aguirre N.M., Visser W., Frias M.F. BLISS: improved symbolic execution by bounded lazy initialization with sat support. *IEEE Trans. Softw. Eng.* 2015;41(7):639–660.

\[98\] Braione P., Denaro G., Pezzè M. Symbolic execution of programs with heap inputs. In: ACM; 2015:602–613. *Proceedings of the 2015 10th Joint Meeting on Foundations of Software Engineering.*.

\[99\] Ibing A. Dynamic symbolic execution with interpolation based path merging. In: 2016. *Int. Conf. Advances and Trends in Software Engineering.*.

\[100\] Agerwala T., Misra J. *Assertion Graphs for Verifying and Synthesizing Programs.* Austin, TX: Technical report; 1978.

\[101\] Graf S., Saïdi H. Construction of abstract state graphs with PVS. In: London, UK: Springer-Verlag; 1997:3-540-63166-672–83. *Proceedings of the 9th International Conference on Computer Aided Verification, CAV ’97.*. [http://dl.acm.org/citation.cfm?id=647766.733618](http://dl.acm.org/citation.cfm?id=647766.733618).

\[102\] Ball T., Rajamani S. *Boolean Programs: A Model and Process for Software Analysis, Technical report.* 2000. [https://www.microsoft.com/en-us/research/publication/boolean-programs-a-model-and-process-for-software-analysis/](https://www.microsoft.com/en-us/research/publication/boolean-programs-a-model-and-process-for-software-analysis/).

\[103\] Clarke E., Grumberg O., Jha S., Lu Y., Veith H. *Counterexample-Guided Abstraction Refinement.* In: Berlin, Heidelberg: Springer; 2000:978-3-540-45047-4154–169. doi:10.1007/10722167\_15.

\[104\] Saidi H. Model checking guided abstraction and analysis. In: London, UK: Springer-Verlag; 2000:3-540-67668-6377–396. *Proceedings of the 7th International Symposium on Static Analysis, SAS ’00.*. [http://dl.acm.org/citation.cfm?id=647169.760067](http://dl.acm.org/citation.cfm?id=647169.760067).

\[105\] Ball T., Rajamani S.K. The SLAM project: debugging system software via static analysis. In: ACM; 1–3. *ACM SIGPLAN Notices.* 2002;vol. 37.

\[106\] Ball T., Levin V., Rajamani S.K. A decade of software model checking with SLAM. *Commun. ACM.* 2011;54(7):68–76.

\[107\] Ball T., Bounimova E., Cook B., Levin V., Lichtenberg J., McGarvey C., Ondrusek B., Rajamani S.K., Ustuner A. Thorough static analysis of device drivers. In: New York, NY: ACM; 2006:1-59593-322-073–85. doi:10.1145/1217935.1217943. *Proceedings of the 1st ACM SIGOPS/EuroSys European Conference on Computer Systems 2006, EuroSys ’06.*.

\[108\] Beyer D., Henzinger T.A., Jhala R., Majumdar R. The software model checker Blast. *Int. J. Softw. Tools Technol. Trans.* 2007;9(5–6):505–525.

\[109\] Beyer D., Keremoglu M.E. CPAchecker: a tool for configurable software verification. In: Springer; 2011:184–190. *International Conference on Computer Aided Verification.*.

\[110\] Dangl M., Löwe S., Wendler P. CPAchecker with support for recursive programs and floating-point arithmetic. In: Springer; 2015:423–425. *International Conference on Tools and Algorithms for the Construction and Analysis of Systems.*.

\[111\] Chaki S., Clarke E., Groce A., Strichman O. *Predicate Abstraction with Minimum Predicates.* In: Berlin, Heidelberg: Springer; 2003:19–34.

\[112\] McMillan K.L. Lazy abstraction with interpolants. In: Berlin, Heidelberg: Springer-Verlag; 2006:3-540-37406-X123–136. doi:10.1007/11817963\_14. *Proceedings of the 18th International Conference on Computer Aided Verification, CAV’06.* 978-3-540-37406-0.

\[113\] Wang C., Yang Z., Gupta A., Ivančic F. Using counterexamples for improving the precision of reachability computation with polyhedra. In: Berlin, Heidelberg: Springer-Verlag; 2007:978-3-540-73367-6352–365. *Proceedings of the 19th International Conference on Computer Aided Verification, CAV’07.*. [http://dl.acm.org/citation.cfm?id=1770351.1770405](http://dl.acm.org/citation.cfm?id=1770351.1770405).

\[114\] Mixed Symbolic Representations for Model Checking Software Programs. In: Washington, DC: IEEE Computer Society; 2006:1-4244-0421-517–26. doi:10.1109/MEMCOD.2006.1695896. *Proceedings of the Fourth ACM/IEEE International Conference on Formal Methods and Models for Co-Design, MEMOCODE '06.*.

![u02-01-9780128151198](images/S0065245817300505/u02-01-9780128151198.jpg)

**Junaid Haroon Siddiqui** is an assistant professor of Computer Science at Lahore University of Management Sciences in Pakistan. Previously, he received his Ph.D. from The University of Texas at Austin. His research interests are static and dynamic techniques in program verification.

 

![u02-02-9780128151198](images/S0065245817300505/u02-02-9780128151198.jpg)

**Affan Rauf** is a Ph.D. candidate in the School of Science and Engineering, Lahore University of Management Sciences, Pakistan. His work interests include automated test case generation, symbolic execution, and software model checking.

![u02-03-9780128151198](images/S0065245817300505/u02-03-9780128151198.jpg)

**Maryam Abdul Ghafoor** is a Ph.D. candidate at Lahore University of Management Sciences, Pakistan. She received MS degree in Computer Science from the same school in 2015. Her research interests include program analysis, symbolic execution, automated software testing, and verification.

Chapter Three 

# Emerging Software Testing Technologies

Francesca Lonetti; Eda Marchetti    ^()ISTI-CNR, Pisa, Italy

## Abstract

Software testing encompasses a variety of activities along the software development process and may consume a large part of the effort required for producing software. It represents a key aspect to assess the adequate functional and nonfunctional software behavior aiming to prevent and remedy malfunctions. The increasing complexity and heterogeneity of software poses many challenges to the development of testing strategies and tools. In this chapter, we provide a comprehensive overview of emerging software testing technologies. Beyond the basic concepts of software testing, we address prominent test case generation approaches and focus on more relevant challenges of testing activity as well as its role in recent development processes. An emphasis is also given to testing solutions tailored to the specific needs of emerging application domains.

### Keywords

Software testing; Testing objectives; Testing techniques and tools; Testing challenges; Software process; Testing needs and trends; Emerging application domains

## 1 Introduction

The testing phase is an important and critical part of software development, consuming even more than half of the effort required for producing deliverable software \[

The testing planning starts during the early stages of requirement analysis and proceeds systematically, with continuous refinements during the course of software development until the completion of the coding phase, with the beginning of the test cases execution. This last step represents the biggest part of software cost that can be evaluated in terms of: the cost of designing a suitable set of test cases which can reveal the presence of bugs; the cost of running those tests, which also requires a considerable amount of time; the cost of detecting them, i.e., the development of a proper “oracle,” which can identify the manifestation of bugs as soon as possible; and the cost of correcting them. All these activities have in common the same testing purpose: evaluating the product quality for increasing the software engineering confidence in the proper functioning of the software. However, it must be made clear that testing cannot show the absence of defects; it can only reveal that software defects are present \[

In this chapter, we refer to the definition of the “Software Testing” introduced in \[

Before continuing the presentation it is important to clarify the terminology relative to the terms “fault,” “defect,” and “failure” that we will use. Although their meanings are strictly related, there are some distinctions between them. As discussed in \[

Testing reveals failures and a consequent analysis stage is needed to identify the faults that caused them. In particular, it is possible that many different failures can result from a single fault, and the same failure can be caused by different faults.

The chapter is organized as follows: in [Section 2](#S0065245817300529.xhtml#s0015) we present basic concepts of testing including types of test (static and dynamic), test levels, and objectives characterizing the testing activity; in [Section 3](#S0065245817300529.xhtml#s0065) we address most prominent test generation techniques and tools; [Section 4](#S0065245817300529.xhtml#s0110) targets challenging aspects of software testing, whereas [Section 5](#S0065245817300529.xhtml#s0150) identifies the role of software testing in relevant software processes. Finally, [Section 6](#S0065245817300529.xhtml#s0170) outlines needs and trends of software testing for emerging application domains, and [Section 7](#S0065245817300529.xhtml#s0225) draws discussion and conclusions.

## 2 Basic Concepts of Testing

The one term testing involves different concepts, refers to a full range of test techniques, even quite different from one other, and embraces a variety of aims. In this section we provide some basic concepts of software testing useful in the remaining of this chapter.

### 2.1 Type of Tests

Since the 1980, the widespread use of modern technologies has led a large part of the software engineering to focus its attention on quality, usability, safety, and other characteristic attributes of software applications. In particular, interest was captured both by the process for software development and by its results. Using their experience software engineering researchers have gradually arrived at the conviction that only the joint between a mature and well-established development process with specific techniques for the quantitative evaluation of the attributes of interest of the artifacts produced can guarantee high quality and reliable applications. Therefore, research has been split into two sets, with of course some natural intersections and points of contact: the former interested to the process (software process improvement \[SPI\]) \[

Frameworks such as CMM \[

#### 2.1.1 Static Techniques

Static techniques are based on the (manual or automated) examination of project documentation, of software models and code, and of other related information about requirements and design. Thus, static techniques can be employed all along software development, and their earlier usage is of course highly desirable.

Considering a generic development process (see [Section 5](#S0065245817300529.xhtml#s0150) for more details), they can be applied \[

*   • at the requirements stage for checking language syntax, consistency and completeness, as well as the adherence to established conventions;
*   • at the design phase for evaluating the implementation of requirements and detecting inconsistencies (for instance between the inputs and outputs used by high-level modules and those adopted by submodules);
*   • during the implementation phase for checking that the form adopted for the implemented products (e.g., code and related documentation) adheres to the established standards or conventions, and that interfaces and data types are correct.

Traditional static techniques include \[

The processes implied by the above techniques are heavily manual, error-prone, and time-consuming. To overcome these problems, researchers have proposed static analysis techniques relying on the use of formal methods \[

In the middle between static and dynamic analysis techniques, there is symbolic execution \[

#### 2.1.2 Dynamic Techniques

Dynamic techniques \[

Testing properly said is based on the execution of the code on valued inputs. Of course, although the set of input values can be considered infinite, those that can be run effectively during testing are finite. It is in practice impossible, due to the limitations of the available budget and time, to exhaustively exercise every input of a specific set even when not infinite. In other words, by testing we observe some samples of the program behavior. A test strategy therefore must be adopted to find a trade-off between the number of chosen inputs and overall time and effort dedicated to testing purposes. Different techniques can be applied depending on the target and the effect that should be reached. We will describe test selection strategies in [Section 3](#S0065245817300529.xhtml#s0065).

### 2.2 Objectives of Testing

Software testing can be applied for different purposes, such as verifying, that the functional specifications are implemented correctly, or that the system shows specific nonfunctional properties such as performance, reliability, and usability. A (certainly noncomplete) list of relevant testing objectives includes \[

*   • Acceptance/qualification testing: it is the final test action prior to deploying a software product. Its main goal is to verify that the software respects the customer requirement. Generally, it is run by or with the end users to perform those functions and tasks the software was built for;
*   • Installation testing: the system is verified upon installation in the target environment. Installation testing can be viewed as system testing conducted once again according to hardware configuration requirements. Installation procedures may also be verified;
*   • Alpha testing: before releasing the system, it is deployed to some in-house users for exploring the functions and business tasks. Generally, there is no test plan to follow, but the individual tester determines what to do;
*   • Beta testing: the same as alpha testing but the system is deployed to external users. In this case the amount of detail, the data, and approach taken are entirely up to the individual testers. Each tester is responsible for creating their own environment, selecting their data, and determining what functions, features, or tasks to explore. Each tester is also responsible for identifying their own criteria for whether to accept the system in its current state or not;
*   • Conformance testing/functional testing: the test cases are aimed at validating that the observed behavior conforms to the specifications. In particular, it checks whether the implemented functions are as intended and provide the required services and methods. This test can be implemented and executed against different test targets, including units, integrated units, and systems;
*   • Nonfunctional testing: it is specifically aimed at verifying nonfunctional properties of the system such as performance, reliability, usability, and security;
*   • Regression testing: it is the selective reexecution of test cases to verify that code modifications have not caused unintended effects and that the system or component still complies with requirements. In practice, the objective is to show that a system which previously passed the tests still does. Notice that a trade-off must be made between the assurance given by regression testing every time a change is made and the resources required to do that.

### 2.3 Test Levels

During the development life cycle of a software product, testing is performed at different levels and can involve the whole system or parts of it. Depending on the process model adopted, then, software testing activities can be articulated in different phases, each one addressing specific needs relative to different portions of a system. Whichever the process adopted, we can at least distinguish in principle between unit, integration, system, and regression test \[

#### 2.3.1 Unit Test

A unit is the smallest testable piece of software, which may consist of hundreds or even just a few lines of source code, and generally represents the result of the work of one programmer. The unit test purpose is to ensure that the unit satisfies its functional specification and/or that its implemented structure matches the intended design structure \[

Unit tests can also be applied to check interfaces (parameters passed in correct order, number of parameters equal to number of arguments, parameter, and argument matching), local data structure (improper typing, incorrect variable name, inconsistent data type), or boundary conditions.

#### 2.3.2 Integration Test

Generally speaking, integration is the process by which software pieces or components are aggregated to create a larger component. Integration testing is specifically aimed at exposing the problems that can arise at this stage. Even though the single units are individually acceptable when tested in isolation, in fact, they could still result in incorrect or inconsistent behavior when combined in order to build complex systems. For example, there could be an improper call or return sequence between two or more components \[

Integration testing thus is aimed at verifying that each component interacts according to its specifications as defined during preliminary design. In particular, it mainly focuses on the communication interfaces among integrated components.

There are not many formalized approaches to integration testing in the literature, and practical methodologies rely essentially on good design sense and the testers intuition. Integration testing of traditional systems was done substantially in either a nonincremental or an incremental approach.

In a nonincremental approach the components are linked together and tested all at once (“big-bang” testing) \[

In modern Object Oriented, distributed systems, approaches, such as top-down or bottom-up integration and their practical derivatives, are no longer usable, as no “classical” hierarchy between components can be generally identified. Some other criteria for integration testing imply integrating the software components based on identified functional threads \[

#### 2.3.3 System Test

System test involves the whole system embedded in its actual hardware environment and is mainly aimed at verifying that the system behaves according to the user requirements. In particular, it attempts to reveal bugs that cannot be attributed to components as such, to the inconsistencies between components, or to the planned interactions of components and other objects (which are the subject of integration testing).

Summarizing, the primary goals of system testing can be \[

System testing should therefore ensure that each system function works as expected, failures are exposed and analyzed, and additionally that interfaces for export and import routines behave as required.

Generally, system testing includes testing for performance, security, reliability, stress testing, and recovery \[

A further test level, called Acceptance Test, is often added to the above subdivision. This is, however, more an extension of system test, rather than a new level. It is in fact a test session conducted over the whole system, which mainly focuses on the usability requirements more than on the compliance of the implementation against some specification. The intent is hence to verify that the effort required from end users to learn to use and fully exploit the system functionalities is acceptable.

#### 2.3.4 Regression Test

Properly speaking, regression test is not a separate level of testing (it is listed among test objectives in [Section 2.2](#S0065245817300529.xhtml#s0035)), but may refer to the retesting of a unit, a combination of components or a whole system after modification, in order to ascertain that the change has not introduced new faults \[

As software produced today is constantly in evolution, driven by market forces and technology advances, regression testing takes by far the predominant portion of testing effort in industry. Since both corrective and evolutive modifications may be performed quite often, to rerun after each change all previously executed test cases would be prohibitively expensive \[

Selective regression test techniques \[

## 3 Test Cases Generation

Test cases generation is among the most important and intensive activities of software testing. A lot of research has been devoted in the last decades to automatic test case generation with the consequent development of different techniques and tools. In this section, we provide an overview of prominent test case generation approaches evidencing the main issues and challenges of each of them.

### 3.1 Search-Based Testing

Search-based software testing is one of the emerging methodologies for automated test generation. It is based on an heuristic, such as a genetic algorithm \[

Due to their versatility, search-based approaches have been adopted in several areas such as \[

Common weaknesses of search-based testing are related to the interaction with external environment, the definition of the fitness function, and the automated oracle. In the former case, the main difficulty is related to the handling interactions with external environment or components with which the system under test could be dependent. In particular, issues could be risen in checking the existence of files or directories. In literature, possible solutions propose to include, in the file or database, test data that can be read back by the program under test, or to use mock objects.

In case of the fitness functions, due to their heuristics nature, there is the possibility they fail to give adequate guidance to the search. A common example is the so-called flag problem in structural test data generation \[

About the automated oracle, notwithstanding the huge interest devoted to this topic, reducing the human activity in the evaluation of the testing results is still an issue. Indeed, available proposals for fitness functions are more focused on maximizing the (structural) coverage, while minimizing the testing effort. The seeding work of \[

### 3.2 Model-Based Testing

In recent years, model-based testing (MBT) has become increasingly successful thanks to the emergence of model-centric development paradigms, such as UML and MDA \[

The four main approaches known as model-based testing are \[

However, model-based testing suffers from some drawbacks that may prevent its use in some application areas, such as the availability of a system specification, which not always exists in practice. Moreover, when it exists, this specification should be complete enough to ensure some relevance of the derived test suite. Finally, this specification cannot include all the implementation details and is restricted to a given abstraction level. Therefore, to become executable, the derived test cases need to be refined into more concrete interaction sequences. Automating this process still remains an open problem.

Despite the continuous evolving of MBT field, as it could be observed in the increasing number of MBT techniques published at the technical literature, there is still a gap between research related to MBT and its application in the software industry. The authors of \[

### 3.3 Black-Box vs White-Box Testing

In this section, alternative classifications of test techniques are provided: the first, called black-box testing, is based on the input/output behavior of the system ([Section 3.3.1](#S0065245817300529.xhtml#s0085)); the second, called white-box testing, is based on the structure and internal data of the software under test ([Section 3.3.2](#S0065245817300529.xhtml#s0090)); the third called gray-box testing trying to mix the previous one ([Section 3.3.3](#S0065245817300529.xhtml#s0095)). Generally, the presented test techniques are not alternative approaches but can be used in combination as they use and provide different sources of information \[

#### 3.3.1 Black-Box Testing

Black-box testing, also called functional testing, relies on the input/output behavior of the system. In particular, the system is subjected to external inputs, so that the corresponding outputs are used to verify the conformance of the system to the specified behavior, with no assumptions of what happens in between. Therefore, in this process we assume knowledge of the (formal or informal) specification of the system under test, which can be used to define a behavioral model of the system (a transaction flowgraph) \[

*   • Testing from formal specifications: in this case it is required that specifications be stated in a formal language, with a precise syntax and semantics. The tests are hence derived automatically from the specification, which are also used for deriving inductive proofs for checking the correct outcome \[ 
*   • Equivalence partitioning: the functional tests are derived from the specifications written in structured, semiformal language. The input domain is partitioned into equivalence classes so that elements in the same class behave similarly. In this context, the category partition is a well-known and quite intuitive method, which provides a systematic, formalized approach to partition testing \[ 
*   • Boundary-values analysis: this is a complementary approach to equivalence partitioning, and concentrates on the errors occurring at boundaries of the input domain. The test cases are thus chosen near the extremes of the class \[ 
*   • Random methods: they consists of generating random test cases based on a uniform distribution over the input domain. It is a low-cost technique because large sets of test patterns can be generated cheaply without requiring any preliminary analysis of software \[ 
*   • Operational profile: test cases are produced by a random process meant to produce different test cases with the same probabilities with which they would arise in actual use of the software \[ 
*   • Decision tables: the decision tables are rules expressed in a structural way used to express the test experts’ or design experts’ knowledge. Decision tables can be used when the outcome or the logic involved in the program is based on a set of decisions and rules which need to be followed \[ 
*   • Cause–effect graphs: these are combinatorial logic networks that can be used to explore in systematic way the possible combinations of input conditions. By analyzing the specification, the relevant input conditions or causes, and the consequent transformations and output conditions, the effects are identified and modeled into graphs linking the effects to their causes \[ 
*   • Combinatorial testing: in combinatorial testing, test cases are designed to execute combinations of input parameters \[ 
*   • State transition testing: this type of testing is useful for testing state machine and also for navigation of graphical user interface \[ 
*   • Evidence-based testing: in evidence-based software engineering (EBSE) the best solution for a practical problem should be identified based on evidence \[ 
    
    One of the points against the black-box testing is its dependence on the specification's correctness and the necessity of using a large amount of inputs in order to get good confidence of acceptable behavior.
    

#### 3.3.2 White-Box Testing

The white-box testing, also called structural testing, requires complete access to the object's structure and internal data, which means the visibility of the source code. The tests are derived from the program's structure, which is also used to track which parts of the code have been executed during testing. For this, some of the commonly used techniques for test case selection are

*   • Control flow-based criteria: these techniques use the control flow graph representation of a program in which nodes correspond to sequentially executed statements while edges represent the flow of control between statements. The aim of white-box testing criteria is to cover as much as possible the control flow graph, limiting the number of selected test cases. In particular, they differentiate in: statement coverage, which is based on executable statements; branch coverage, which focuses on the blocks and case statements that affect the control flow; condition coverage, which relies on subexpressions independently of each other; path coverage, which is based on the possible paths exercised through the code \[ 
*   • Data flow coverage: in data flow testing, a data definition of a variable is a location where a value is stored in memory (definition) and a data use is a location where the value of the variable is accessed for computations (c-use) or for predicate uses (p-use). The data flow testing goal is to generate tests that execute program subpaths from definition to use. Traditional data flow analysis techniques work on control flow graphs annotated with specific information on data usage \[ 
    
    #### 3.3.3 Gray-Box Testing
    
    The gray-box testing tries to combine the two aforementioned proposals \[
    
    ### 3.4 Symbolic Execution
    
    Symbolic execution is a popular program analysis technique, introduced in the 1970s, that has found interest in recent years in the research community, with particular emphasis on applications to test generation \[
    
    The main challenges of symbolic execution in processing real-world code are related to \[
    
    *   • Environment interactions: interactions with the file system or the network through libraries and system calls could cause side-effects and affect the execution. Evaluating any possible interaction outcome is generally unfeasible since it could generate a large number of execution states. A typical strategy is to consider popular library and system routines and create models that can help the symbolic engine to analyze only significant outcomes.
    *   • State space explosion and path selection: the existence of real-world looping programs might exponentially increase the number of execution states and prevent the symbolic execution engine to exhaustively explore all the possible states within a reasonable amount of time. In practice, heuristics are used to guide and prioritize states exploration. In addition, efficient mechanisms for evaluating multiple states in parallel are implemented in symbolic engines.
    *   • Constraint solver limitations: constraint solvers suffer from a number of limitations when they have to deal with nonlinear constraints over their elements. Symbolic execution engines normally rely on optimizations and algebraic simplifications.
    
    However, to overcome the limitations of symbolic execution due to path explosion and the time spent in constraint solving, a standard approach consists into combining concrete and symbolic executions of the code under test. This approach is known as concolic testing \[
    
    Symbolic execution has been included in several recent tools offering the capability to systematically exploring many possible execution paths at the same time without necessarily requiring concrete inputs. The most common ones evidencing the growing impact of symbolic execution in practice are
    
    *   • Symbolic Java PathFinder (Symbolic JPF): it is a symbolic execution framework that implements a nonstandard bytecode interpreter on top of the Java PathFinder model checking tool \[ 
    *   • CUTE and jCUTE: CUTE (a concolic unit testing engine) and jCUTE (CUTE for Java) handle multithreaded programs that manipulate dynamic data structures using pointer operations \[ 
    *   • KLEE: it is a symbolic execution tool, capable of automatically generating tests that achieve high coverage on a diverse set of complex and environmentally intensive programs \[ 
        
        ### 3.5 Nonfunctional Testing
        
        An important aspect for software testing is the possibility of determine and evaluate properties of the product such as determine how fast the product responds to a request or how long it takes to do an action. Nonfunctional testing is performed at all test levels and is focused on software attributes such performance, security, scalability, and so on. Nowadays, there exist more than 150 types of nonfunctional testing. Here below, the most common nonfunctional testing types are briefly schematized:
        
        *   • Performance testing: it is specifically aimed at verifying that the system meets the specified performance requirements. It usually targets validation of response times, throughput, resource-utilization levels, and other specific performance characteristics of the software under test. However, the term performance testing is a general one that many time is associated to various attributes or characteristics of nonfunctional testing. We refer to \[ 
        *   • Load testing: it focuses on assessing the behavior of a system under pressure in order to detect load-related problems where the term load refers to the rate at which different service requests are submitted to the system under test (SUT) \[ 
        *   • Stress testing: it is the process of putting a system far beyond its capabilities to verify its robustness and/or to detect various load-related problems. Contrary to load testing in which the maximum allowable load is generated, in stress testing, the load generated is more than what the system is expected to handle \[ 
        *   • Volume testing: it is the process in which internal program or system limitations, such for instance storage requirements, are tried. It involves the ability of the systems to exchange data and information \[ 
        *   • Failover testing: it validates a system's ability to be able to allocate extra resource when it encounters heavy load or unexpected failure so to continue normal operations \[ 
        *   • Security testing: it assesses whether security properties related to confidentiality, integrity, availability, authentication, authorization, and nonrepudiation are correctly implemented. Security testing demonstrates either the conformance with the security properties or addresses known vulnerabilities by means of malicious, nonexpected input data set \[ 
        *   • Reliability testing: testing is used as a means to improve reliability; in such a case, the test cases must be randomly generated according to the operational profile, i.e., they should sample more densely the most frequently used functionalities \[ 
        *   • Compatibility testing: it is the process for verifying whether the software can collaborate with different hardware and software facilities or with different versions or releases of the same hardware or software \[ 
        *   • Usability testing: it evaluates the ease of using and learning the system and the user documentation, as well as the effectiveness of system functioning in supporting user tasks, and, finally, the ability to recover from user errors. This testing is particularly important when testing GUI \[ 
        *   • Scalability testing: it is focused on verifying the ability of the software to increase and scale up on any of its nonfunctionality requirements such as load, number of transactions, and volume of data \[ 
            
            ## 4 Test Challenges
            
            Beyond decades of research activities, techniques, and actors in software testing, there are still many aspects that remain more challenging due to the complexity, pervasiveness, and criticality of continual software development. In this section, we overview several outstanding research challenges that need to be addressed to advance the state of the art in software testing and represent the directions to be followed for coping with the rapid advances of the software market.
            
            ### 4.1 Oracle Problem
            
            An important component of testing is the oracle. Indeed, a test is meaningful only if it is possible to decide about its outcome. The difficulties inherent to this task, often oversimplified, had been early articulated in \[
            
            In a scenario in which a limited number of test cases are executed, the oracle can be the tester himself/herself, who can either inspect a posterior the test log or even decide a priori, during test planning, the conditions that make a test successful and code these conditions into the employed test driver \[
            
            Oracle can be derived by the analysis of textual (natural language) documentation describing the functionalities expected from the SUT to varying degrees. The partial and ambiguous nature of this documentation has often forced the manual oracle decisions. However, as overviewed in \[
            
            When the tests cases are automatically derived or also when their number is quite high, in the order of thousands or millions, a manual log inspection or codification of the test results is not thinkable. Automated oracles must then be implemented.
            
            In this case, a possible solution is to use pseudo-oracle \[
            
            However, most of the available proposals for oracle definition are derived from a specification of the expected behavior \[
            
            *   • Model-based specification languages: the purpose is to exploit the models and a syntax that defines desired behavior in terms of its effects on the model so to derive the expected oracle. Different proposals discuss how to use the abstract specification to define high-level test oracles \[ 
            *   • State transition systems: this kind of approaches focuses on the formal modeling of the system thought state transition systems. In particular, they focus on the reaction of a system to stimuli, i.e., transitions, and abstract a property of the states. A rigorous empirical evaluation of test oracle construction techniques using state transition systems is provided in \[ 
            *   • Assertions and contracts: if assertions could be embedded into the program so to provide run-time checking capability, conditions are instead expressly specified to be used as test oracles. As consequence, the produced execution traces could be logged and analyzed so to derive the oracle verdicts \[ 
            *   • Algebraic specifications: the purpose is to define equations over program operations that hold when the program is correct. The software is represented in terms of equational axioms that specify the required properties of the operations. Typically, these languages employ first-order logic to prove properties of the specification, like the correctness of refinements. Abstract data types (ADT), which combine data and operations over that data, are well suited to algebraic specification \[ 
                
                The formal specifications have the advantage that they can be used both for test case derivation and oracle specification as well. However, the gap between the abstract level of specifications and the concrete level of executed tests only allows for partial oracles implementations, i.e., only necessary (but not sufficient) conditions for correctness can be derived \[
                
                In view of these considerations, it should be evident that the oracle might not always judge correctly. So the notion of coverage of an oracle is introduced to measure its accuracy. It could be measured for instance by the probability that the oracle rejects a test (on an input chosen at random from a given probability distribution of inputs), given that it should reject it \[
                
                ### 4.2 Full Automation
                
                An important challenge of decades of research in software testing has been to improve the degree of attainable automation, either by developing advanced techniques for generating the test inputs or, beyond test generation, by finding innovative support procedures to automate the testing process \[
                
                Test automation tools promise to increase the number of tests they run and the frequency at which they run them by many orders of magnitude. Test automation can be incredibly effective, giving more coverage and new visibility into the software under test. However, 100% automatic testing remains still a dream \[
                
                Practitioners frequently report disastrous failures in the attempt to reduce costs by automating software tests, particularly at the level of system testing \[
                
                The trade-off between automated and manual testing is discussed in literature. The authors of \[
                
                An attempt in this direction is represented by perpetual testing, also known as continuous testing \[
                
                The principle of continuous testing is today a key feature of DevOps which extends agile principles to entire software delivery pipeline \[
                
                Finally, existing techniques aim to reduce automation costs by automating test automation. The main approach consists into a sequence of natural language test steps enabling a sequence of procedure calls with accompanying parameters that can drive testing without human intervention. This technique has been proven effective in reducing the cost of test automation by automating over 82% of the steps contained in a test suite \[
                
                ### 4.3 Scalability of Testing
                
                The complexity of software systems is not only caused by their functionalities, but it is also due to the complexity of the platform and environment in which they run. Mobile devices, distributed wireless networked and virtualized environment, large-scale clusters, and mobile clouds are just some examples. Additionally, in settings like software as a service (SaaS) \[
                
                Recent studies focus on scalability of mutation testing which requires much time and computational resources to execute the overall test suite against all mutants. An empirical study of scalability of selective mutation testing is proposed in \[
                
                ### 4.4 Test Effectiveness
                
                Evaluating the program under test, measuring the efficacy of a testing technique, or judging whether testing is sufficient and can be stopped are important aspects of the software testing, which in turn would require having measures of the effectiveness. The following sections provide details about the different aspects of effectiveness.
                
                #### 4.4.1 Measuring the Software
                
                For evaluating the program under test different measurements and approaches can be applied as reported in \[
                
                *   • Linguistic measures: these are based on proprieties of the program or of the specification text. This category includes for instance the measurement of: sources lines of code (LOC), statements, number of unique operands or operators, and function points;
                *   • Structural measures: these are based on structural relations between objects in the program and comprise control flow or data flow complexity. These can include measurements relative to the structuring of program modules, e.g., in terms of the frequency with which modules call each other;
                *   • Hybrid measures: these may result from the combination of structural and linguistic properties;
                *   • Fault density: this is a widely used measure in industrial contexts and foresees the counting of the discovered faults and their classification by their type. For each fault class, fault density is measured by the ratio between the number of faults found and the size of the program.
                
                #### 4.4.2 Measuring the Testing Technique
                
                For evaluating the testing approach, sometimes, coverage/thoroughness measures can be adopted. In this case, adequacy criteria evaluate the testing approach through the percentage of exercised set of elements identified in the program or in the specification by testing. However, the widespread adopted methods focus on the evaluation of the fault detection effectiveness of the considered testing technique. With different degrees of formalization, these proposals measure how much the test cases are able to revealing categories of likely or predefined faults. Among them, mutation analysis \[
                
                Mutation testing can be adopted at any level of testing (unit, integration level, system level) and can be applied both for white-box, black-box, or gray-box testing. In literature, there are plenty of proposals and tools for many programming languages. We refer to \[
                
                #### 4.4.3 Test Cases Selection and Prioritization
                
                In software testing, to improve fault detection rate at a given test execution time, common solutions rely on the application of proper strategies for test cases selection or prioritization. Test case selection aims to reduce the cardinality of the test suites while keeping the same effectiveness in terms of coverage or fault detection rate; test case prioritization aims at defining a test execution order according to some criteria (e.g., coverage and fault detection rate), so that those tests that have a higher priority are executed before the ones having a lower priority.
                
                Many proposals address test cases selection for regression systems, aiming to speed up testing with a focus on detecting change-related faults \[
                
                Some recent proposals try to automate test cases selection techniques using information retrieval \[
                
                Test case prioritization techniques \[
                
                *   • the rate of fault detection, namely, the likelihood of revealing faults earlier in a run of regression tests;
                *   • the likelihood of revealing regression errors related to specific code changes earlier in the regression testing process \[
                *   • the coverage of code under test;
                *   • the confidence in the reliability of the system under test.
                
                In practice, the test case prioritization problem may be intractable, so test case prioritization techniques rely typically on heuristics. A review of such prioritization techniques is presented in \[
                
                ## 5 Testing Process
                
                During recent years, software testing has increased its role in the process of development. It is no longer focused on the defects detection after code completion, but it is now an integrated and significant activity performed during the whole software life cycle. Its critical nature and the importance for the overall quality of the final products led adopting the good practice of starting its management at the early stages of software development during the requirements analysis and proceeding with its organization systematically and continuously during the entire development process up to the code level.
                
                Without referring to any specific software development process, usually the basic development phases can be summarized as in the following \[
                
                *   • Requirements analysis: services, constraints, goals, and features of the overall system are established and organized. The list of requirements specifies the guidelines that the project must adhere to. At the end of this phase a set of documented, actionable, measurable, testable, and traceable requirements should be defined to a level of detail sufficient for system design;
                *   • System and software design: this phase targets both hardware and software requirements and establishes the overall system architecture. The representation of the system is usually provided in terms of functionalities easily transformable into one or more executable applications/programs;
                *   • Implementation: the established design is implemented in order to satisfy the list of requirements identified in the requirement analysis and definition phase. The implemented units or subsystems are integrated into a complete system to be properly tested;
                *   • Validation and testing: quality attributes as well as requirement assessment are calculated and validated. Different test techniques can be included in the process development, each one targeting a different aspect of the proposed system.
                
                Considering in particular the validation and testing phase, even if its management can depend strictly on the development process adopted for delivering the software products, the main phases can be resumed in \[
                
                *   • Planning: as for any other process activity, the testing must be planned and scheduled. Thus, the time and effort needed for performing and completing software testing must be established in advance during the early stages of development. This also includes the specification of the personnel involved, the tasks they must to perform, and the facilities and equipment they may use;
                *   • Test cases generation: according to the test plan constraints a set(s) of the test cases must be generated by using a (several) test strategy(ies);
                *   • Test cases execution: the test cases execution may involve testing engineers, outside personnel or even customers. It is important to document every action performed in order to allow the experiments’ duplication and meaningful and truthful evaluations of the results obtained;
                *   • Test results analysis: the collected testing results must be evaluated to determine whether the test was successful (the system performs as expected, or there are no major unexpected outcomes) and used for deriving measures and values of interest;
                *   • Problem reporting: a test log documents the testing activity performed. This should contain, for example, the date in which a test was conducted, the data of the people who performed the test, the information about the system configuration and any other relevant data. Anomalies or unexpected behaviors should be also reported;
                *   • Postclosure activities: the information relative to failures or defects discovered during testing execution are used for evaluating the performance and the effectiveness of the developed testing strategy(ies) and determining whether the process development adopted needs some improvements.
                
                In the remaining of this section some of the most important development processes are briefly introduced and the role of testing inside them discussed.
                
                ### 5.1 Sequential Models
                
                One of the first models to be designed was the waterfall model (W-model), also known as the cascade model, where the software development life cycle was constructed from a sequential set of stages \[
                
                The V-model is the successive variation of the W-model, where a V\-shape folded at the coding level is included. It was important to demonstrate that testing activities should be planned and designed as early as possible in the life cycle. Sometimes the V-model can be used in large projects which can include several subsystems and third-party systems.
                
                The most common alternatives of the sequential approaches are evolutionary ones which are based on iterations. In this case, the system is not defined in advance but evolves through the evaluation of the achieved intermediate results.
                
                ### 5.2 Iterative Models
                
                During the last 10 years, part of software research has been dedicated to the improvement of the development process (SPI initiatives). In this context, the CMM model (Capability Maturity Model) \[
                
                As summarized in \[
                
                Other methods for managing the program improvement are the IDEAL framework \[
                
                The IDEAL method is an integrated approach for SPI defined by the SEI which identifies five phases: (i) initiating, which specifies the business goals and objectives that will be realized or supported; (ii) diagnosing, which identifies the organization's current state with respect to a related standard or reference model; (iii) establishing, which develops plans to implement the chosen approach; (iv) acting, which brings together everything available to create a best guess solution specific to organizational needs and puts the solution in place; and (v) leveraging, which summarizes lessons learned regarding processes used to implement IDEAL.
                
                The RUP, which is a detailed refinement of the Unified Process (UP) \[
                
                The RUP structure is characterized by: a static structure that describes the process (who is doing what, how, and when); dynamic structure that details how the process rolls out over time; an architecture-centric process that defines and details the architecture; a use-case driven process which specifies how use cases are used throughout the development cycle.
                
                The RUP encourages testing early by offering a number of mechanisms to integrate testing more closely with the software development effort. In particular, RUP targets to: (i) making test a distinct discipline; (ii) using an iterative development approach; (iii) continuously verifying quality and letting use cases drive development; (iv) scheduling implementation based on risk; (v) managing changes strategically; and (vi) using the right-sized process.
                
                ### 5.3 Agile Development Process
                
                The term agile software development was created by the Agile Manifesto \[
                
                In the agile environment, testing is a frequent activity as small amounts of code are tested immediately upon being written. According to the Manifesto for agile software development, agile main points are (i) individuals and interactions over processes and tools; (ii) working software over comprehensive documentation; (iii) customer collaboration over contract negotiation; and (iv) responding to change over following a plan.
                
                The intent is to produce high quality software in a cost-effective and timely manner, and in the meantime, meet the changing needs of end users. In an agile environment, testing is often included within development in the form of test driven development (TDD) \[
                
                By developing only enough code to pass the tests and then using the refactoring as an improvement method for the design quality, TDD leads to better code quality and improves the confidence in the code as well as increasing the productivity.
                
                Recent applications of agile software development are the XP (eXtreme Programming) and Scrum \[
                
                The Scrum is more focused on the delivering of objected-oriented software \[
                
                Basic adjectives characterizing Scrum implementations are transparency (visibility), inspection, and adaptation. Transparency or visibility means that any aspect of the process that affects the outcome must be visible and known to everybody involved in the process. Inspection requires that various aspects of the process must be inspected frequently enough so that unacceptable variances in the process can be detected. Adaptation requires that the inspector should adjust the process if one or more aspects of the process are in an unacceptable range.
                
                ## 6 Domain-Specific Testing
                
                Recent years have witnessed the emergence of domain-specific approaches in software testing. These approaches are tailored to the specific needs of the domain and leverage domain knowledge to adapt and customize well-known testing solutions. Specifically, in the last decades software development is driven by emerging trends such as the widespread diffusion of mobile technology, cloud infrastructures adoption, as well as big data analysis and software as a service paradigm that point out new constraints and challenges for the testing activity. In the following of this section, we give a brief overview of different aspects and solutions for software testing applied into several domain-specific environments.
                
                ### 6.1 Cloud-Based Testing
                
                Cloud computing is henceforth an accepted alternative for deploying applications and services. Businesses desire to achieve higher level operational performance and flexibility while keeping the development and deployment cost as lower as possible. Meanwhile, cloud computing has an high impact in software testing with the diffusion of a new testing paradigm known as testing as a service (TaaS). TaaS in a cloud infrastructure is a new business and service model, which provides static or dynamic on-demand testing services in the cloud and delivers them as a service to customers.
                
                The main advantages of cloud-based testing deal with \[
                
                *   • Reducing the testing costs and time. Cloud computing offers unlimited storage as well as virtualized resources and shared cloud infrastructures that can help to eliminate required computer resources and licensed software costs as well as to reduce the execution time of large test suites in a cost-effective manner. This allows large IT companies to support many production lines which require diverse computing resources and test tools;
                *   • Performing on-demand test services to conduct large-scale performance and scalability online validation;
                *   • Performing testing of dynamic, complex, distributed applications such as mobile and web applications, leveraging multiple operating systems and updates, multiple browser platforms and versions, different types of hardware, and a large number of concurrent users.
                
                The authors of \[
                
                There are three main different forms of testing as service (TaaS) in a cloud environment. Each of them has different focuses and objectives \[
                
                *   • Testing on clouds. In this form, software applications are deployed and executed on a cloud, and validated using the provided test services given by TaaS vendors. The major objective here is to take the advantage of large-scale test simulations and elastic computing resources on a cloud;
                *   • Testing over clouds. In this form, software applications are deployed and validated based on different clouds (such as private clouds, public, or hybrid clouds). A typical software system crossing multiple clouds is structured with components, service software, and servers deployed crossing over several clouds;
                *   • Testing of a cloud. It validates the quality of a cloud infrastructure according to the specified capabilities and service requirements.
                
                Besides the many advantages in using cloud-based systems, there are yet many realistic problems of cloud service testing that need to be solved \[
                
                *   • On-demand test environment setup. There is a lack of supporting solutions to assist engineers to setup a required test environment in a cloud using a cost-effective way. To overcome these limitations, solutions aiming to empower the cloud applications with self-configuration, self-healing, and self-protection capabilities are provided;
                *   • The heterogeneity and lack of standards in test tools and their connectivity and interoperability to support testing services;
                *   • Assuring and assessing user privacy and security of cloud-based applications inside a third-party cloud infrastructure.
                
                Finally, the authors of \[
                
                ### 6.2 SOA Testing
                
                As described in [Section 3.3](#S0065245817300529.xhtml#s0080), traditional testing approaches are divided into three major classes: black-box, white-box, and gray-box testing. Considering the specific domain of SOA testing while black-box approaches keep the same target of traditional ones, white-box and gray-box proposals assume a slightly different meaning. Indeed, in SOA white-box testing two different points of view can be identified: coverage measured at the level of a service composition (orchestration or choreography) and coverage of a single service internals. Generally, validation of service orchestrations is based on the Business Process Execution Language description^([²](#fn2))
                
                If, on the one side, there are several approaches for structural testing of service compositions, there are few proposals for deriving structural coverage measures of the invoked services. The reason for this is that independent web services usually provide just an interface, enough to invoke them and develop some general (black-box) tests, but insufficient for a tester to develop an adequate understanding of the integration quality between the application and independent web services.
                
                In the rest of this section, a survey of some proposed approaches and tools for supporting SOA testing is presented. Additionally, since black, white, and gray-box testing, albeit successfully executed, do not prevent security weaknesses, an overview of this important aspect is presented in [Section 6.2.4](#S0065245817300529.xhtml#s0200).
                
                #### 6.2.1 SOA Black-Box Testing
                
                As a common guideline, SOA black-box testing relies on the functionality provided by the web services. Commonly, the use of the (formal) specification or the XML Schema datatype^([³](#fn3))
                
                #### 6.2.2 SOA White-Box Testing
                
                Most often white-box testing of SOA applications is devoted to the validation of web service compositions (WSC). Validation of WSCs can be usually addressed performing structural coverage testing of a WSC specification. As overviewed in \[
                
                #### 6.2.3 SOA Gray-Box Testing
                
                In the context of service-oriented architectures (SOAs), where independent web services can be composed with other services to provide richer functionality, interoperability testing becomes a major challenge. Independent web services usually provide just an interface, enough to invoke them and develop some general functional (black-box) tests, but insufficient for a tester to develop an adequate understanding of the integration quality between the application and the independent web services. To address this lack, gray-box proposals, trying to “whitening” the SOA testing, can be considered \[
                
                #### 6.2.4 SOA Security Testing
                
                Security aspects are highly critical in designing and developing web services. It is possible to distinguish at least two kinds of strategies for addressing protective measures of the communication among web services: security at the transport level and security at the message level. Enforcing the security at the transport level means that the authenticity, integrity, and confidentiality of the message (e.g., the SOAP message) are completely delegated to the lower-level protocols that transport the message itself from the sender to the receiver. Such protocols use public key techniques to authenticate both the end points and agree to a symmetric key, which is then used to encrypt packets over the (transport) connection. Since SOAP messages may carry vital business information, their integrity and confidentiality need to be preserved, and exchanging SOAP messages in a meaningful and secured manner remains a challenging part of system integration. Unfortunately, those messages are prone to attacks based on an on-the-fly modification of SOAP messages (XML rewriting attacks or XML injection) that can lead to several consequences such as unauthorized access, disclosure of information, or identity theft. Message-level security within SOAP and web services is addressed in many standards such as WS-Security,^([⁴](#fn4))
                
                The activity of fault detection is an important aspect of (web) service security. Indeed, most breaches are caused when a system component is used in an unexpected manner. Improperly tested code, executed in a way that the developer did not intend, is often the primary culprit for security vulnerability. Robustness and other related attributes of web services can be assessed through the testing phase and are designed first off by analyzing WSDL document to know what faults could affect the robustness quality attribute of web services, and secondly by using the fault-based testing techniques to detect such faults. Focusing in particular on testing aspects, the different strategies and approaches that have been developed over the years can be divided into passive or active mechanisms \[
                
                Passive mechanisms consist of observing and analyzing messages that the component under test exchanges with its environment and are specially used either for fault management in networks or for checking whether a system respects its security policy. Active testing is based on the generation and the application of specific test cases in order to detect faults.
                
                All the techniques have the purpose of providing evidence in security aspects, i.e., that an application faces its requirements in the presence of hostile and malicious inputs. Like functional testing, security testing relies on what is assumed to be a correct behavior of the system, and on nonfunctional requirements. However, the complexity of (web) security testing is bigger than functional testing, and the variety of different aspects that should be taken into consideration during a testing phase implies the use of a variety of techniques and tools. An important role in software security is played by negative testing \[
                
                *   • Fuzz testing: it involves generating semivalid data and submitting them in defined input fields or parameters (files, network protocols, API calls, and other targets) in an attempt to break the program and find bugs. Semivalid data are correct enough to keep parsers from immediately dismissing them, but still invalid enough to cause problems. Fuzzing covers a significant portion of negative test cases without forcing the tester to deal with each specific test case for a given boundary condition. In the specific area of web service security, fuzzing inputs can often be generated by programmatically analyzing the WSDL or sample SOAP requests and making modifications to the structure and content of valid requests. File fuzzing strategy is also used for detecting XML data vulnerability; 
                *   • Injection: in general, web services can interact with a variety of systems and for this reason they must be resistant to injection attacks when external systems are accessed or invoked. The most prevalent injection vulnerabilities include SQL injection, command injection, LDAP injection, XPath injection, and code injection. Recently, SQL Injection attack has become a major threat to web applications. SQL injection occurs when a database is queried with an SQL statement which contains some user-influenced inputs that are outside the intended parameters range; 
                *   • Policy-based testing: an important aspect in the security of modern information management systems is the control of accesses. Data and resources must be protected against unauthorized, malicious or improper usage or modification. For this purpose, several standards have been introduced that guarantee authentication and authorization, such for instance the eXtensible Access Control Markup Language (XACML),^([⁵](#fn5)) 
                    
                    ### 6.3 GUI-Based Testing
                    
                    Currently, with the widespread use of graphical user interface (GUI), the GUI testing is receiving a lot of attention. However, the GUI development includes different activities that force to face the GUI testing from different perspectives such as test coverage, test case generation, and test oracle and regression testing. Among these, the test case generation is one of the most important and therefore the one that received most attention in literature. As stated in \[
                    
                    Referring to the classification provided into \[
                    
                    *   • Based on finite state machines: this kind of approach is the most adopted for the GUI testing. Usually the input and output sequences are used for generating hierarchal models based on them. FSM can be then exploited for different testing approaches such as coverage for all-paths and all-transitions. Peculiarities of such kind of testing are \[ 
                    *   • Goal-driven approaches: these proposals exploit the definition of predefined goals that can be used both as input and as output, by generating sequences of actions, which reach these goals. These sequences of actions are used as test cases for GUIs. This technique allows the analysis of user interactions using model checking, and the synthesis of user interactions to executable GUI applications; 
                    *   • Based on abstractions: in these proposals, abstractions may be based on structural features of GUI applications, e.g., the enabledness of a button (enabled or disabled) using a Boolean value, or the current value of slider control using an integer value. Abstraction can be either manually inferred or automatically derived by static analysis of the code \[ 
                    *   • Model-based approaches: all these techniques require the creation of a model of the software or its GUI, and algorithms to use the model to generate test cases. In some cases, the models are created manually; in others, they are derived in an automated manner. Also the test case generation for some techniques is manual, but for most is automated. In \[ 
                        
                        ### 6.4 Mobile Testing
                        
                        Rapid advances of mobile technology and wireless networking push the wide adoption of mobile applications in different critical domains, from banking to mobile cyber-physical systems, to patients monitoring. According to the recent studies, the market for cloud-based mobile applications will grow exponentially in the next years. To guarantee the reliability and security of such mobile applications, their testing is required on many different configurations of devices and operating systems. Approaches to make such testing automated, systematic, and measurable are needed. According to recent studies \[
                        
                        Recent research addresses mobile testing as a service (MTaaS) \[
                        
                        *   • Use of test automation: traditional testing of mobile applications, often done by manual execution of test cases and visual verification of the results, is an effort-intensive and time-consuming process. Automating the testing activities produces a great reduction of costs and effort in the whole mobile applications software development life cycle;
                        *   • Use of emulators and actual devices: emulators can be useful for testing features of the application that are device independent. However, due to diversity in mobile hardware, actual devices will be used for validating the results;
                        *   • Testing the mobile environment for application complexity: this is needed in order to address the varieties of mobile and wireless technologies, like Wi-Fi, WiMax, 3G, 4G, etc., as well as to validate performance and robustness of the mobile system in real-world network conditions;
                        *   • Testing on heterogeneous mobile platforms: the applications will be tested on different platforms for checking compatibility with different mobile operating systems;
                        *   • Large-scale on-demand mobile test services: they allow to implement testing techniques and strategies responding to on-demand requests of test generation, execution, and control.
                        
                        ### 6.5 Big Data Testing
                        
                        Big data provides not only large amounts of data but also various data types such as images, videos, interactive maps, time stamps, and associated metadata. The main four characteristics of big data are volume, variety, velocity, and value. Data is continuously being generated from machines, sensors from Internet of Things, mobile devices, network data traffic, and application logs. This requires advances in data storage, mining and business intelligence technologies making it possible to preserve increasing amounts of data generated directly or indirectly by users and analyze it to yield valuable new insights \[
                        
                        Big data also present new challenges with respect to their maintenance, testing, and benchmarking. While big data systems have advanced their capabilities of data analysis, scalability, processing and fault tolerance, database testing, and benchmarking have not moved forward to provide data generators, data sets, and workloads. The authors of \[
                        
                        Experimental studies often reuse data sets from well-known standardized benchmarks for performance evaluation of database systems, like TPC-C \[
                        
                        The main limitations of existing approaches of benchmarking and testing of big data systems are about the lack of realistic data sets. Existing data sets are build on simplistic assumptions such as uniform distributions or oversimplified schema that often are not representative for real-world data. An attempt to overcome these limitations is to automatically extract the domain information from a ground truth data set, which is often available in practice. This information is then integrated into a data generator specification for a specific target environment and then used to create a concrete data generator instance that is able to mimic the original data set \[
                        
                        Different solutions to generate representative data sets in the big data context and to control the size of the test set, deal with input space partitioning testing associated to input domain model. The tester partitions the input domain model, selects test values from partitioned blocks, and applies combinatorial coverage criteria to generate tests. Parallel computing and Hadoop are used to speed up data generation \[
                        
                        Finally, the evaluation and testing of big data analytic systems requires more complex, realistic, and universally useful workload specifications that involve machine learning algorithms, information extraction, and graph analysis/mining.
                        
                        ### 6.6 Automotive Testing
                        
                        In automotive domain, one of the most important aspects is security. Currently, existing solutions for security assessment of software systems basically perform either static analysis (i.e., the software is not executed) or dynamic analysis (performed by executing the software on specific inputs), although any life cycle will likely apply a combination of both. A 2009 survey carried out within the NIST SAMATE project^([⁶](#fn6))
                        
                        *   • Static analysis: aids analysts in locating security-related issues;
                        *   • Source code fault injection: the source code is instrumented by inserting changes and then executed to observe the changes in state and behavior that emerge;
                        *   • Dynamic analysis: refers generically to security testing approaches, such as coverage-based or profiling;
                        *   • Architectural analysis: aims at identifying flaws in the software architecture and determining resulting risks to information assets;
                        *   • Pedigree analysis: identifies software coming from an external source (e.g., open-source software);
                        *   • Binary code analysis and disassembler analysis: both categories review binary code. Since source code is not needed, they can be applied to commercial off-the-shelf (COTS) components;
                        *   • Binary fault injection: focuses on likely faults in the real-time operation of the software (e.g., memory faults or other error conditions provided by the processor);
                        *   • Fuzzing: a form of negative testing, in which the software is exercised under random invalid data, generally specific to a particular type of input;
                        *   • Malicious code detectors: search for malicious logic embedded in programs;
                        *   • Bytecode analysis: bytecode contains more semantic information about the program execution than an equivalent binary. Bytecode analysis tools are actively investigated.
                        
                        Many works try to transfer existing security assessment methods to the automotive domain, addressing specific risks and challenges of automotive software. Nowadays, several works \[
                        
                        The widespread utilization of model-based design and production code generation in the automotive development process enables the application of automatic verification and validation techniques earlier in the software life cycle, and at an higher level of abstraction using for instance Simulink models \[
                        
                        However, many testing methodologies and tools are customized to address specific challenges of the automotive domain. In \[
                        
                        Other security testing activities are aimed at finding implementation errors that could be exploited by an outside attacker to cause potential functionality problems. Such activities are also used to establish to what extent the target system can resist an attack and generally consist of: (i) functional automotive security testing able to ensure general compliance with the specifications and standards for the security functionality implemented, encryption algorithms and authentication protocols of a vehicular IT system; (ii) vulnerability scanning applied to all relevant applications, source codes, networks, and backend infrastructures of an automotive system in order to test the system for common security vulnerabilities such as security loopholes or security configurations with known weaknesses taken from a continuously updated database of automotive security vulnerabilities; (iii) fuzzing that is used to expose the implementation to unexpected, invalid, or random input in the hope that the target will react in an unexpected way and, as a result, uncover new vulnerabilities; (iv) penetration tests applied in a final step to test security of the whole system by applying attacking methods conducted by trusted individuals to check whether ECUs are vulnerable and could allow unauthorized users access.
                        
                    
                    ## 7 Discussion and Conclusions
                    
                    This chapter presented a journey through the world of software testing and its emerging techniques, ranging over many fields from definition to organization, from its applicability and analysis of effectiveness, to the challenges and specific issues of some of the most important application domains. However, due to the vast and articulated research discipline, the covering into one chapter of all ongoing and foreseen research directions and emerging technologies is impossible. Indeed, this chapter proposes broadness against depth overview and it is an attempt to depict a comprehensive and extensible roadmap of the most important topics, challenges, and future directions of testing activity. [Fig. 1](#S0065245817300529.xhtml#f0010) provides a graphical overview of the main chapter contents.
                    
                    ![Fig. 1 Software testing roadmap.](images/S0065245817300529/f03-01-9780128151198.jpg)
                    
                    Fig. 1 Software testing roadmap.
                    
                    This chapter would be a reference of the most recent testing techniques and presented an almost complete overview of the new methods, approaches, and tools useful to the reader for managing, controlling, and evaluating software testing development. It targets students, researchers, software developers, and practitioners looking for solutions for their problems and improvements in the different activities of the testing process. As emerged from this chapter, software testing is not an isolated activity; it has many fruitful relations between different areas of software engineering and many times it is the bridge between different disciplines.
                    
                    Due to the increasing complexity of software systems and the variety of execution environments, software testing will continue to be a key activity in the software development process and quality assurance.
                    
                    Over the years software testing has had to keep the path of the trends, innovations, and modifications provided by the new software development paradigms. In order to trigger always updated and practical solutions, software testing needs to learn from the state of practice and to elaborate the future vision useful to predict the problems, market exigencies, and quality issues that could rise. In particular, the growth of cloud computing brings the need of benchmarks and on-demand test environment construction to measure the performance and scalability metrics of new applications considering the special features of cloud such as dynamic scalability, scalable testing environments, SLA-based requirements, and cost-models. New testing methods will be developed to assess compatibility, interoperability, and multitenancy ability of cloud applications that must be able to work across multiple environments, various cloud platforms, client technologies, and browsers.
                    
                    Possible suggestions for more in-depth and effective methodologies and approaches can be the use of realistic settings and large-scale systems as well as the simulation or involvement of real stakeholders working simultaneously in distributed environments. In particular, large-scale and software intensive IT systems are created by integrating and orchestrating independently controlled and managed systems. The most limiting factor of their development is software validation, which typically requires very costly and complex testing processes. Existing approaches for testing these systems focus on orchestrating the different phases of the testing process including test operation, test injection, monitoring and reporting, sometimes according to response time, bandwidth usage, throughput, and adaptability, with the aim of continuous integration and deployment. New testing techniques able to deal with the inherent complexity of these systems will be based on the divide-and-conquer principle, which is commonly used for architecting complex software. They will leverage a novel test orchestration theory and toolbox enabling the creation of complex test suites for large systems as the composition of simple testing units. These new solutions will allow the reusability of testing knowledge, architectures, and code, making testing activity more effective and less expensive. Moreover, these new testing techniques, based on the orchestration topology of simple test cases, will also target the important problem of automated partial oracle derivation of tests of large systems by inferring test oracle specification from the composition of expected and obtained outputs of the executed testing units.
                    
                    An important role is given by the possibility of leveraging the software testing proposals from the specific programming language and execution environment so that high-level, application-independent attributes such as trust, security, and performance can be easily and automatically verified with a drastic reduction of testing time and effort.
                    
                    Considering in particular the new collaborative and distributed software development processes such as Agile, Scum, and DevOp, the testing techniques should make easier the simultaneous verification and the automatic alignment of test activity with decomposition and distribution of the target systems. Additionally, due to the short development time, new proposals drastically decreasing learning time and addressing the multiple levels of IT personnel are becoming a real pressing so improve software testing and productivity.
                    
                    Moreover, due to the increasing popularity of social networking services and their massive integration into the users’ everyday life, another future target of testing activity is represented by the specific requirements of these services. Besides, performance and scalability validation of the decentralized online social networks, new testing techniques will be devoted to assess security and privacy of users’ personal data in order to prevent local attacks. These techniques will specifically target assessment of privacy and sharing information policies as well validation of decentralized management of users’ social profiles and data storage solutions.
                    
                    Finally, the recent trend of adopting correct or secure-by-design development process forces testing activity to propose tools and methodology useful for testing and analyzing design level artifacts. In particular, simulation, model checking, and model-based approaches should be the key success for improving the quality of the developed systems.
                    
                     
                    
                    ## References
                    
                    \[1\] Ammann P., Offutt J. *Introduction to Software Testing.* Cambridge University Press; 2016.
                    
                    \[2\] Dijkstra E.W. *Notes on Structured Programming.* Eindhoven: Technische Hogeschool Eindhoven; 1970.
                    
                    \[3\] Bertolino A. Software testing. In: Abran A., Bourque P., Dupuis R., Moore J.W., eds. *Guide to the Software Engineering Body of Knowledge—SWEBOK.* Piscataway, NJ: IEEE Press; 2001:076951000069 ISBN: 0769510000.
                    
                    \[4\] Thayer R.H., Hunter R. *Software Process Improvement.* IEEE Computer Society; 2001.
                    
                    \[5\] Paulk M. Capability Maturity Model for software. In: Wiley Online Library; 1993. *Encyclopedia of Software Engineering.*.
                    
                    \[6\] Emam K.E., Melo W., Drouin J.-N. *SPICE: The Theory and Practice of Software Process Improvement and Capability Determination.* IEEE Computer Society Press; 1997.
                    
                    \[7\] Kruchten P. *The Rational Unified Process: An Introduction.* Addison-Wesley Professional; 2004.
                    
                    \[8\] Bertolino A., Marchetti E. A brief essay on software testing. In: Thayer R.H., Christensen M.J., eds. Wiley-IEEE Computer Society Press; . *Software Engineering, The Development Process.* 2005;vol. 3.
                    
                    \[9\] Guttag J.V., Horning J.J. *Larch: Languages and Tools for Formal Specification.* Springer Science & Business Media; 2012.
                    
                    \[10\] Cadar C., Sen K. Symbolic execution for software testing: three decades later. *Comm. ACM.* 2013;56(2):82–90.
                    
                    \[11\] Gligoric M., Negara S., Legunsen O., Marinov D. An empirical evaluation and comparison of manual and automated test selection. In: ACM; 2014:361–372. *Proc. of the 29th ACM/IEEE Int. Conf. on Automated Software Engineering.*.
                    
                    \[12\] Xanthakis S., Ellis C., Skourlas C., Le Gall A., Katsikas S., Karapoulios K. Application of genetic algorithms to software testing. In: 1992:625–636. *Proceedings of the 5th International Conference on Software Engineering and Applications.*.
                    
                    \[13\] Miller W., Spooner D.L. Automatic generation of floating-point test data. *IEEE Trans. Softw. Eng.* (3):1976;223–226.
                    
                    \[14\] McMinn P. Search-based software testing: past, present and future. In: IEEE; 2011:153–163. *2011 IEEE Fourth International Conference on Software Testing, Verification and Validation Workshops (ICSTW).*.
                    
                    \[15\] Harman M., Hu L., Hierons R., Wegener J., Sthamer H., Baresel A., Roper M. Testability transformation. *IEEE Trans. Softw. Eng.* 2004;30(1):3–16.
                    
                    \[16\] McMinn P., Stevenson M., Harman M. Reducing qualitative human oracle costs associated with automatically generated test data. In: ACM; 2010:1–4. *Proceedings of the First International Workshop on Software Test Output Validation.*.
                    
                    \[17\] Lano K. *Model-Driven Software Development with UML and Java.* Course Technology Press; 2009.
                    
                    \[18\] Utting M., Pretschner A., Legeard B. A taxonomy of model-based testing approaches. *Soft. Test. Verification Reliab.* 2012;22(5):297–312.
                    
                    \[19\] Utting M., Legeard B. *Practical Model-Based Testing: A Tools Approach.* Morgan Kaufmann; 2010.
                    
                    \[20\] Dias-Neto A.C., Travassos G.H. A picture from the model-based testing area: concepts, techniques, and challenges. *Adv. Comput.* 2010. ;80:45–120. [https://doi.org/10.1016/S0065-2458(10)80002-6](https://doi.org/10.1016/S0065-2458\(10\)80002-6), [http://www.sciencedirect.com/science/article/pii/S0065245810800026](http://www.sciencedirect.com/science/article/pii/S0065245810800026).
                    
                    \[21\] Khan M.E., Khan F., et al. A comparative study of white box, black box and grey box testing techniques. *Int. J. Adv. Comput. Sci. Appl.* 2012;3(6).
                    
                    \[22\] Bhat A., Quadri S.M.K. Equivalence class partitioning and boundary value analysis–a review. In: 2015:1557–1562. *2015 2nd International Conference on Computing for Sustainable Global Development (INDIACom).*.
                    
                    \[23\] Myers G.J., Sandler C., Badgett T. *The Art of Software Testing.* John Wiley & Sons; 2011.
                    
                    \[24\] Arcuri A., Briand L. Formal analysis of the probability of interaction fault detection using random testing. *IEEE Trans. Softw. Eng.* 0098-55892012. ;38(5):1088–1099. [https://doi.org/10.1109/TSE.2011.85](https://doi.org/10.1109/TSE.2011.85).
                    
                    \[25\] Lyu M.R., et al. *Handbook of Software Reliability Engineering.* California: IEEE Computer Society Press; 1996.
                    
                    \[26\] Nie C., Leung H. A survey of combinatorial testing. *ACM Comput. Surv.* 0360-03002011. ;43(2):11:1–11:29. [https://doi.org/10.1145/1883612.1883618](https://doi.org/10.1145/1883612.1883618).
                    
                    \[27\] Lee D., Yannakakis M. Principles and methods of testing finite state machines—a survey. *Proc. IEEE.* 1996;84(8):1090–1123.
                    
                    \[28\] Lynch N.A., Tuttle M.R. *An Introduction to Input/Output Automata.* Massachusetts Institute of Technology. Laboratory for Computer Science; 1988.
                    
                    \[29\] Tretmans J., Hierons R.M. Model based testing with labelled transition systems. In: Bowen J.P., Harman M., eds. *Formal Methods and Testing.* Springer; 2008:1–38.
                    
                    \[30\] Börger E., Stärk R. *Abstract State Machines: A Method for High-level System Design and Analysis.* Springer Science & Business Media; 2012.
                    
                    \[31\] Tiwari A. *Formal Semantics and Analysis Methods for Simulink Stateflow Models.* Technical report Citeseer; 2002.
                    
                    \[32\] Baier C., Katoen J.-P., Larsen K.G. *Principles of Model Checking.* MIT Press; 2008.
                    
                    \[33\] Kasoju A., Petersen K., Mäntylä M.V. Analyzing an automotive testing process with evidence-based software engineering. *Inf. Softw. Technol.* 0950-58492013. ;55(7):1237–1259. [https://doi.org/10.1016/j.infsof.2013.01.005](https://doi.org/10.1016/j.infsof.2013.01.005), [http://www.sciencedirect.com/science/article/pii/S0950584913000165](http://www.sciencedirect.com/science/article/pii/S0950584913000165).
                    
                    \[34\] Kitchenham B.A., Dyba T., Jorgensen M. Evidence-based software engineering. In: 2004:273–281. *Proceedings. 26th International Conference on Software Engineering.* 0270-5257. [https://doi.org/10.1109/ICSE.2004.1317449](https://doi.org/10.1109/ICSE.2004.1317449).
                    
                    \[35\] Santos R.E., de Magalhães C.V., da Silva F.Q. The use of systematic reviews in evidence based software engineering: a systematic mapping study. In: ACM; 2014:53. *Proceedings of the 8th ACM/IEEE International Symposium on Empirical Software Engineering and Measurement.*.
                    
                    \[36\] Păsăreanu C.S., Visser W. A survey of new trends in symbolic execution for software testing and analysis. *Int. J. Softw. Tools Technol. Transfer.* 2009;11(4):339–353.
                    
                    \[37\] Baldoni R., Coppa E., D’Elia D.C., Demetrescu C., Finocchi I. *A Survey of Symbolic Execution Techniques.* 2016 arXiv preprint arXiv:1610.00502.
                    
                    \[38\] Sen K. Concolic testing. In: New York, NY: ACM; 2007:571–572. *Proceedings of the Twenty-second IEEE/ACM International Conference on Automated Software Engineering, ASE '07.*. [https://doi.org/10.1145/1321631.1321746](https://doi.org/10.1145/1321631.1321746) 978-1-59593-882-4.
                    
                    \[39\] Pasareanu C.S., Mehlitz P.C., Bushnell D.H., Gundy-Burlet K., Lowry M., Person S., Pape M. Combining unit-level symbolic execution and system-level concrete execution for testing NASA software. In: ACM; 2008:15–26. *Proceedings of the 2008 International Symposium on Software Testing and Analysis.*.
                    
                    \[40\] Sen K., Marinov D., Agha G. CUTE: a concolic unit testing engine for C. *SIGSOFT Softw. Eng. Notes.* 0163-59482005. ;30(5):263–272. [https://doi.org/10.1145/1095430.1081750](https://doi.org/10.1145/1095430.1081750).
                    
                    \[41\] Cadar C., Dunbar D., Engler D. KLEE: unassisted and automatic generation of high-coverage tests for complex systems programs. In: 2008:209–224. *Proc. of the 8th USENIX Conf. on Operating Systems Design and Implementation, OSDI'08.*. [http://dl.acm.org/citation.cfm?id=1855741.1855756](http://dl.acm.org/citation.cfm?id=1855741.1855756).
                    
                    \[42\] Lewis W.E. *Software Testing and Continuous Quality Improvement.* CRC Press; 2016.
                    
                    \[43\] Jiang Z.M., Hassan A.E. A survey on load testing of large-scale software systems. *IEEE Trans. Softw. Eng.* 0098-55892015. ;41(11):1091–1118. [https://doi.org/10.1109/TSE.2015.2445340](https://doi.org/10.1109/TSE.2015.2445340).
                    
                    \[44\] Felderer M., Büchler M., Johns M., Brucker A.D., Breu R., Pretschner A. Chapter One-Security Testing: A Survey. *Adv. Comput.* 2016;101:1–51.
                    
                    \[45\] Dalal S.R., Lyu M.R., Mallows C.L. *Software Reliability.* Wiley Online Library; 2014.
                    
                    \[46\] Geisen E., Bergstrom J.R. *Usability Testing for Survey Research.* Morgan Kaufmann; 2017.
                    
                    \[47\] Pezze M., Zhang C. Automated test oracles: a survey. *Adv. Comput.* 2015;95:1–48.
                    
                    \[48\] Barr E.T., Harman M., McMinn P., Shahbaz M., Yoo S. The oracle problem in software testing: a survey. *IEEE Trans. Softw. Eng.* 2015;41(5):507–525.
                    
                    \[49\] Davis M.D., Weyuker E.J. Pseudo-oracles for non-testable programs. In: ACM; 1981:254–257. *Proceedings of the ACM’81 Conference.*.
                    
                    \[50\] Peters D.K., Parnas D.L. Using test oracles generated from program documentation. *IEEE Trans. Softw. Eng.* 1998;24(3):161–173.
                    
                    \[51\] Mouchawrab S., Briand L.C., Labiche Y., Di Penta M. Assessing, comparing, and combining state machine-based testing and structural testing: a series of experiments. *IEEE Trans. Softw. Eng.* 2011;37(2):161–187.
                    
                    \[52\] Loyola P., Staats M., Ko I.-Y., Rothermel G. Dodona: automated Oracle data set selection. In: New York, NY: ACM; 2014:193–203. *Proceedings of the 2014 International Symposium on Software Testing and Analysis, ISSTA 2014.*. [https://doi.org/10.1145/2610384.2610408](https://doi.org/10.1145/2610384.2610408) 978-1-4503-2645-2.
                    
                    \[53\] Bertolino A. Software testing research: achievements, challenges, dreams. In: IEEE Computer Society; 2007:85–103. *2007 Future of Software Engineering.*.
                    
                    \[54\] Persson C., Yilmazturk N. Establishment of automated regression testing at ABB: Industrial experience report on ‘avoiding the pitfalls’. In: IEEE Computer Society; 2004:112–121. *Proceedings of the 19th IEEE International Conference on Automated Software Engineering.*.
                    
                    \[55\] Hoffman D. Cost benefits analysis of test automation. *STAR West.* 1999;vol. 99.
                    
                    \[56\] Ramler R., Wolfmaier K. Economic perspectives in test automation: balancing automated and manual testing with opportunity cost. In: ACM; 2006:85–91. *Proceedings of the 2006 International Workshop on Automation of Software Test.*.
                    
                    \[57\] Graham D., Fewster M. *Experiences of Test Automation: Case Studies of Software Test Automation.* Addison-Wesley Professional; 2012.
                    
                    \[58\] Saff D., Ernst M.D. Reducing wasted development time via continuous testing. In: IEEE; 2003:281–292. *14th International Symposium on Software Reliability Engineering.*.
                    
                    \[59\] Virmani M. Understanding DevOps & bridging the gap from continuous integration to continuous delivery. In: IEEE; 2015:78–82. *Fifth International Conference on Innovative Computing Technology (INTECH).*.
                    
                    \[60\] Thummalapenta S., Sinha S., Singhania N., Chandra S. Automating test automation. In: 2012:881–891. *2012 34th International Conference on Software Engineering (ICSE).* 0270-5257. [https://doi.org/10.1109/ICSE.2012.6227131](https://doi.org/10.1109/ICSE.2012.6227131).
                    
                    \[61\] Buxmann P., Hess T., Lehmann S. Software as a service. *Wirtschaftsinformatik.* 2008;50(6):500–503.
                    
                    \[62\] Zikopoulos P., Eaton C., et al. *Understanding Big Data: Analytics for Enterprise Class Hadoop and Streaming Data.* McGraw-Hill Osborne Media; 2011.
                    
                    \[63\] Isakowitz T., Bieber M., Vitali F. Web information systems. *Commun. ACM.* 1998;41(7):78–80.
                    
                    \[64\] Baheti R., Gill H. Cyber-physical systems. In: IEEE Control Systems Society; 161–166. *The Impact of Control Technology.* 2011;vol. 12.
                    
                    \[65\] Zhang J., Zhu M., Hao D., Zhang L. An empirical study on the scalability of selective mutation testing. In: IEEE; 2014:277–287. *IEEE 25th International Symposium on Software Reliability Engineering (ISSRE).*.
                    
                    \[66\] Fenton N., Bieman J. *Software Metrics: A Rigorous and Practical Approach.* CRC Press; 2014.
                    
                    \[67\] Jia Y., Harman M. An analysis and survey of the development of mutation testing. *IEEE Trans. Softw. Eng.* 0098-55892011. ;37(5):649–678. [https://doi.org/10.1109/TSE.2010.62](https://doi.org/10.1109/TSE.2010.62).
                    
                    \[68\] Delamaro M.E., Maidonado J.C., Mathur A.P. Interface mutation: an approach for integration testing. *IEEE Trans. Softw. Eng.* 2001;27(3):228–247.
                    
                    \[69\] Belli F., Budnik C.J., Hollmann A., Tuglular T., Wong W.E. Model-based mutation testing: approach and case studies. *Sci. Comput. Program.* 2016;120:25–48.
                    
                    \[70\] Martin E., Xie T. A fault model and mutation testing of access control policies. In: 2007:667–676. *Proc. of WWW.*.
                    
                    \[71\] Bertolino A., Daoudagh S., Lonetti F., Marchetti E. XAMUT: XACML 2.0 mutants generator. In: IEEE; 2013:28–33. *IEEE Sixth International Conference on Software Testing, Verification and Validation Workshops (ICSTW).*.
                    
                    \[72\] Shi A., Yung T., Gyori A., Marinov D. Comparing and combining test-suite reduction and regression test selection. In: ACM; 2015:237–247. *Proceedings of the 2015 10th Joint Meeting on Foundations of Software Engineering.*.
                    
                    \[73\] Magalhães C., Barros F., Mota A., Maia E. Automatic selection of test cases for regression testing. In: ACM; 2016:8. *Proc. of the 1st Brazilian Symp. on Systematic and Automated Software Testing.*.
                    
                    \[74\] Gligoric M., Eloussi L., Marinov D. Practical regression test selection with dynamic file dependencies. In: ACM; 2015:211–222. *Proc. of the 2015 Int. Symp.on Software Testing and Analysis.*.
                    
                    \[75\] Srivastava P.R. Test case prioritization. *J. Theoretical Appl. Inf. Technol.* 2008;4(3):178–181.
                    
                    \[76\] Saha R.K., Zhang L., Khurshid S., Perry D.E. An information retrieval approach for regression test prioritization based on program changes. In: IEEE; 268–279. *IEEE/ACM 37th IEEE International Conference on Software Engineering (ICSE).* 2015;vol. 1.
                    
                    \[77\] Rothermel G., Untch R.H., Chu C., Harrold M.J. Test case prioritization: an empirical study. In: 1999:179–188. *IEEE International Conference on Software Maintenance (ICSM ’99).* 1063-6773. [https://doi.org/10.1109/ICSM.1999.792604](https://doi.org/10.1109/ICSM.1999.792604).
                    
                    \[78\] Rothermel G., Untch R.H., Chu C., Harrold M.J. Prioritizing test cases for regression testing. *IEEE Trans. Softw. Eng.* 2001;27(10):929–948.
                    
                    \[79\] Do H., Rothermel G. On the use of mutation faults in empirical assessments of test case prioritization techniques. *IEEE Trans. Softw. Eng.* 2006;32(9):733–752.
                    
                    \[80\] Elbaum S., Rothermel G., Kanduri S., Malishevsky A.G. Selecting a cost-effective test case prioritization technique. *Softw. Qual. J.* 2004;12(3):185–210.
                    
                    \[81\] Bertolino A., Daoudagh S., El Kateb D., Henard C., Le Traon Y., Lonetti F., Marchetti E., Mouelhi T., Papadakis M. Similarity testing for access control. *Inf. Softw. Technol.* 2015;58:355–372.
                    
                    \[82\] Zhang L., Hou S.-S., Guo C., Xie T., Mei H. Time-aware test-case prioritization using integer linear programming. In: ACM; 2009:213–224. *Proceedings of the Eighteenth International Symposium on Software Testing and Analysis.*.
                    
                    \[83\] Wu K., Fang C., Chen Z., Zhao Z. Test case prioritization incorporating ordered sequence of program elements. In: IEEE Press; 2012:124–130. *Proceedings of the 7th International Workshop on Automation of Software Test.*.
                    
                    \[84\] McFeeley B. *IDEAL: A User's Guide for Software Process Improvement.* Technical report DTIC Document; 1996.
                    
                    \[85\] Fowler M., Highsmith J. The Agile Manifesto. *Softw. Dev.* 2001;9(8):28–35.
                    
                    \[86\] Beynon-Davies P., Carne C., Mackay H., Tudhope D. Rapid application development (RAD): an empirical review. *Eur. J. Inf. Sys.* 1999;8(3):211–223.
                    
                    \[87\] Kniberg H. *Scrum and XP from the Trenches.* [Lulu.com](http://Lulu.com); 2015.
                    
                    \[88\] Gao J., Bai X., Tsai W.-T. Cloud testing-issues, challenges, needs and practice. *Soft. Eng. Int. J.* 2011;1(1):9–23.
                    
                    \[89\] Chana I., Rana A., et al. Empirical evaluation of cloud-based testing techniques: a systematic review. *ACM SIGSOFT Soft. Eng. Notes.* 2012;37(3):1–9.
                    
                    \[90\] Gao J., Bai X., Tsai W.-T., Uehara T. Testing as a service (TaaS) on clouds. In: IEEE; 2013:212–223. *IEEE 7th Int. Symp. on Service Oriented System Engineering (SOSE).*.
                    
                    \[91\] Bai X., Li M., Chen B., Tsai W.-T., Gao J. Cloud testing tools. In: 2011:1–12. *IEEE 6th Int. Symp. on Service Oriented System Engineering (SOSE).*.
                    
                    \[92\] Bartolini C., Bertolino A., Lonetti F., Marchetti E. Approaches to functional, structural and security SOA testing. In: IGI Global; 2012:381–401. *Performance and Dependability in Service Computing: Concepts, Techniques and Research Directions.*.
                    
                    \[93\] Bartolini C., Bertolino A., Marchetti E., Polini A. WS-TAXI: a WSDL-based testing tool for web services. In: IEEE; 2009:326–335. *International Conference on Software Testing Verification and Validation (ICST).*.
                    
                    \[94\] Petrova-Antonova D., Kuncheva K., Ilieva S. Automatic generation of test data for XML schema-based testing of web services. In: IEEE; 1–8. *10th International Joint Conference on Software Technologies (ICSOFT).* 2015;vol. 1.
                    
                    \[95\] Bozkurt M., Harman M., Hassoun Y. Testing and verification in service-oriented architecture: a survey. *Softw. Test. Verification Reliab.* 2013;23(4):261–313.
                    
                    \[96\] Hillah L.M., Maesano A.-P., Maesano L., De Rosa F., Kordon F., Wuillemin P.-H. Service Functional Testing Automation with Intelligent Scheduling and Planning. In: New York, NY: ACM; 2016:1605–1610. *Proc. of the 31st Annual ACM Symp. on Applied Computing.*. [https://doi.org/10.1145/2851613.2851807](https://doi.org/10.1145/2851613.2851807) 978-1-4503-3739-7.
                    
                    \[97\] Bartolini C., Bertolino A., Marchetti E., Parissis I. Data flow-based validation of web services compositions: perspectives and examples. In: de Lemos R., Di Giandomenico F., Gacek C., Muccini H., Vieira M., eds. *Architecting Dependable Systems V.* Springer; 2008:298–325.
                    
                    \[98\] Hummer W., Raz O., Shehory O., Leitner P., Dustdar S. Testing of data-centric and event-based dynamic service compositions. *Softw. Test. Verification Reliab.* 2013;23(6):465–497.
                    
                    \[99\] Bartolini C., Bertolino A., Elbaum S., Marchetti E. Whitening SOA testing. In: ACM; 2009:161–170. *Proceedings of the 7th Int. Conf. ESEC-FSE.*.
                    
                    \[100\] Ye C., Jacobsen H.-A. Whitening SOA testing via event exposure. *IEEE Trans. Softw. Eng.* 2013;39(10):1444–1465.
                    
                    \[101\] Benharref A., Dssouli R., Serhani M.A., Glitho R. Efficient traces’ collection mechanisms for passive testing of web services. *Inf. Softw. Technol.* 2009;51(2):362–374.
                    
                    \[102\] Martin E. Automated test generation for access control policies. In: ACM; 2006:752–753. *Companion to the 21st ACM SIGPLAN Symposium on Object-Oriented Programming Systems, Languages, and Applications.*.
                    
                    \[103\] Bertolino A., Daoudagh S., Lonetti F., Marchetti E. The X-CREATE framework: a comparison of XACML policy testing strategies. In: 2012:155–160. *WEBIST.*.
                    
                    \[104\] Memon A.M., Nguyen B.N. Advances in automated model-based system testing of software applications with a GUI front-end. *Adv. Comput.* 2010;80:121–162.
                    
                    \[105\] Qureshi I.A., Nadeem A. GUI testing techniques: a survey. *Int. J. Futur. Comput. Commun.* 2013;2(2):142.
                    
                    \[106\] Banerjee I., Nguyen B., Garousi V., Memon A. Graphical user interface (GUI) testing: Systematic mapping and repository. *Inf. Softw. Technol.* 2013;55(10):1679–1694.
                    
                    \[107\] Arlt S., Ermis E., Feo-Arenis S., Podelski A. *Verification of GUI Applications: A Black-Box Approach.* In: Berlin, Heidelberg: Springer; 2014:236–252. [https://doi.org/10.1007/978-3-662-45234-9\_17](https://doi.org/10.1007/978-3-662-45234-9_17) 978-3-662-45234-9.
                    
                    \[108\] ABI Research's Mobile Application Technologies, $200 Million Mobile Application Testing Market Boosted by Growing Demand for Automation, [https://www.abiresearch.com/press/200-millionmobile-application-testing-market-boos](https://www.abiresearch.com/press/200-millionmobile-application-testing-market-boos).
                    
                    \[109\] Gao J., Tsai W.-T., Paul R., Bai X., Uehara T. Mobile testing-as-a-service (MTaaS)—infrastructures, issues, solutions and needs. In: IEEE; 2014:158–167. *IEEE 15th Int. Symp. on High-Assurance Systems Engineering (HASE).*.
                    
                    \[110\] Starov O., Vilkomir S., Gorbenko A., Kharchenko V. Testing-as-a-service for mobile applications: state-of-the-art survey. In: Zamojski W., Sugier J., eds. *Dependability Problems of Complex Information Systems.* Springer; 2015:55–71.
                    
                    \[111\] Villanes I.K., Costa E.A.B., Dias-Neto A.C. Automated Mobile Testing as a Service (AM-TaaS). In: 2015:79–86. *2015 IEEE World Congress on Services.* 2378-3818. [https://doi.org/10.1109/SERVICES.2015.20](https://doi.org/10.1109/SERVICES.2015.20).
                    
                    \[112\] Michael K., Miller K.W. Big Data: New Opportunities and New Challenges \[Guest editors’ introduction\]. *Computer.* 0018-91622013. ;46(6):22–24. [https://doi.org/10.1109/MC.2013.196](https://doi.org/10.1109/MC.2013.196).
                    
                    \[113\] Abidin A., Lal D., Garg N., Deep V. Comparative analysis on techniques for big data testing. In: 2016:219–223. *2016 Int. Conf. on Information Technology (InCITe)—The Next Generation IT Summit on the Theme—Internet of Things: Connect your Worlds.*. [https://doi.org/10.1109/INCITE.2016.7857620](https://doi.org/10.1109/INCITE.2016.7857620).
                    
                    \[114\] Alexandrov A., Brücke C., Markl V. Issues in big data testing and benchmarking. In: ACM; 2013:1. *Proc. of the Sixth Int. Workshop on Testing Database Systems.*.
                    
                    \[115\] TPC Benchmarks & Benchmark Results, [http://www.tpc.org/](http://www.tpc.org/) (accessed April 2017).
                    
                    \[116\] XMark—An XML Benchmark Project, [http://www.xml-benchmark.org/](http://www.xml-benchmark.org/) (accessed April 2017).
                    
                    \[117\] Li N., Escalona A., Guo Y., Offutt J. A scalable big data test framework. In: 2015:1–2. *2015 IEEE 8th International Conference on Software Testing, Verification and Validation (ICST).* 2159-4848. [https://doi.org/10.1109/ICST.2015.7102619](https://doi.org/10.1109/ICST.2015.7102619).
                    
                    \[118\] Robinson-Mallett C. Coordinating security and safety engineering processes in automotive electronics development. In: 2014:45–48. *Proceedings of the 9th Annual Cyber and Information Security Research Conference.*.
                    
                    \[119\] B. Antonia, C. Antonello, D.G. Felicita, L. Giuseppe, L. Francesca, M. Eda, M. Fabio, M. Ilaria, M. Paolo, Secure Software Engineering for Connected Vehicles: A Research Agenda, Technical reports no. IIT TR-18/2015, [http://www.iit.cnr.it/en/node/36711](http://www.iit.cnr.it/en/node/36711).
                    
                     
                    
                    ![u03-01-9780128151198](images/S0065245817300529/u03-01-9780128151198.jpg)
                    
                    **Francesca Lonetti** is a researcher at CNR-ISTI. She received her Ph.D. in Computer Science from the University of Pisa in 2007, Italy. Her current research focuses on monitoring and testing of software systems. In particular, she is interested in testing of security systems (access control and usage control systems), methodologies and tools for robustness testing of web services, modeling, and validation approaches of nonfunctional properties and business process modeling and assessment. Her expertise on these research topics has been applied in the context of several national and European research projects including Learn PAd, CHOReOS, TAS3, NESSoS, CONNECT, and D-ASAP. She is and has been part of the program committee of several international conferences and workshops in the field, such as ICST, MODELSWARD, AST, and QUATIC. She has been a publications chair of ICST 2012 and proceedings cochair of ICSE 2015. She is/has been a cochair of the 11th IEEE/ACM International Workshop on Automation of Software Test (AST 2016) and the International Workshop on domAin-specific Model-based AppRoaches to vErificaTion and validation (Amaretto 2016).
                    
                    ![u03-02-9780128151198](images/S0065245817300529/u03-02-9780128151198.jpg)
                    
                    **Eda Marchetti** is a researcher at CNR-ISTI. She graduated summa cum laude in Computer Science from the University of Pisa (1997) and got a Ph.D. from the same University (2003). Her research activity focuses on software testing and in particular security testing, testing of access control systems, model-based testing, SOA, and component-based testing. She has taking the role of WP coordinator in recently concluded projects including TAS3, Presto4u. She has been involved in several EU project: TELCERT, CONNECT, CHOReOS, NESSoS, and TAROT. She is currently involved in the monitoring and testing process of Learn PAd. She has served as a reviewer for several international conferences and journals, and she has been part of the organizing and program committee of several international workshops and conferences. She has (co)authored over 50 papers in international journals and conferences.
                    
                    * * *
                    
                
            
        
    

Chapter Four 

# Optimizing the Symbolic Execution of Evolving Rhapsody Statecharts

Amal Khalil; Juergen Dingel    ^()School of Computing, Queen's University, Kingston, ON, Canada

## Abstract

Model-driven engineering (MDE) is an iterative and incremental software development process. Supporting the analysis and the verification of software systems developed following the MDE paradigm requires to adopt incrementality when carrying out these crucial tasks in a more optimized way.

Communicating state machines are one of the various formalisms used in MDE tools to model and describe the behavior of distributed, concurrent, and real-time reactive systems (e.g., automotive and avionics systems). Modeling the overall behavior of such systems is carried out in a modular way and on different levels of abstraction (i.e., it starts with modeling the behavior of the individual objects in the system first then modeling the interaction between these objects). Similarly, analyzing and verifying the correctness of the developed models to ensure their quality and their integrity is performed on two main levels. The intralevel is used to analyze the correctness of the individual models in isolation of the others, while the interlevel is used to analyze the overall interoperability of those that are communicating with each other.

One way to facilitate the analysis of the overall behavior of a system of communicating state machines is to build the global state space (also known as the global reachability tree) of the system. This process is very expensive and in some cases it may suffer from the state explosion problem. Symbolic execution is a technique that can be used to construct an abstract and a bounded version of the system global state space that is known as a symbolic execution tree (SET), yet the size of the generated trees can be very large especially with big and complex systems that are composed of multiple objects. As the system evolves, one way to avoid regenerating the entire SET and repeating any SET-based analyses that have been already conducted is to utilize the previous SET and its analysis results in optimizing the process of generating the SET of the system after the change. In this chapter, we propose two optimization techniques to direct the successive runs of the symbolic execution technique toward the impacted parts of an evolving state machine model using memoization (MSE) and dependency analysis (DSE), respectively. The evaluation results of both techniques showed significant reduction in some cases compared with the standard symbolic execution technique.

### Keywords

Model-driven engineering; Symbolic execution; Incremental verification; State-based behavioral models; State machines; Memoization; Dependency analysis; Model-based analysis

## 1 Introduction

Model-driven engineering (MDE) is a model-centric software engineering approach that aims at improving the productivity and the quality of software artifacts by focusing on models as first-class artifacts in place of code. MDE has been widely used for over a decade in many domains such as automotive and telecommunication industries. Iterative-incremental development and model-based analysis are central to MDE in which artifacts typically undergo several iterations and refinements during their lifetime that may require changes to their initial design versions. As these models evolve, it is necessary to assess their quality by repeating the analysis and the verification of these models after every iteration or refinement. This process, if not optimized, can be very tedious and time consuming.

State machines are a visual state-based formalism used to describe the behavior of reactive systems and they are found, with some variation, in every MDE tool (e.g., IBM Rational Rhapsody's Statecharts, IBM Rational Software Architect's UML-RT, or MathWorks Simulink's Stateflow).

Symbolic execution is a well-known analysis technique that is used to analyze the execution paths of behavioral software artifacts (e.g., programs \[[1](#S0065245817300487_3.xhtml#bb0010)\] and state-based models \[[2](#S0065245817300487_3.xhtml#bb0015), [3](#S0065245817300487_3.xhtml#bb0020)\]). The output of the analysis is a symbolic execution tree (SET) which provides the basis for various types of analysis and verification. One of the key challenges of symbolic execution is scalability, especially when applied to big, complex artifacts where the size of the output SET becomes very large. Repeating the entire analysis even after small changes is not the best solution.

This chapter describes research investigating two complementary optimization techniques that leverage the similarities between state machine versions to reduce the cost of symbolic execution of the evolved version.

This research is motivated by a number of facts. First, symbolic execution has been shown to be a very powerful method for the analysis of programs and there are already several commercial code analysis tools built based on it (e.g., CodeSonar \[[4](#S0065245817300487_3.xhtml#bb0025)\]). Similarly, the technique has been adopted and applied in the context of state-based models (e.g., the IAR visualSTATE—Verificator \[[5](#S0065245817300487_3.xhtml#bb0030)\]). Second, there is an interest from our industrial partner, General Motors Corporation (GM), to improve the model-level analysis capabilities of the IBM Rhapsody tool. Third, research on optimizing the symbolic execution of evolving programs has been recently addressed \[[6](#S0065245817300487_3.xhtml#bb0035), [7](#S0065245817300487_3.xhtml#bb0040)\], however, to the best of our knowledge we are the first to consider such optimizations for the symbolic execution of evolving state machines.

### 1.1 Research Statement and Scope

The main goal of this research is to prove that the efficiency and cost of symbolic execution of evolving state machines can be measurably improved using incremental analysis.

Since we aim to use IBM Rhapsody Statecharts as the input state-based models to build a proof of concept implementation of our proposed techniques, we will only use IBM related tools (e.g., the IBM Rational Rhapsody Developer RulesComposer Add-On and the IBM Rational Rhapsody DiffMerge) to develop the different components of our proposed architectures as presented in [Section 4](#S0065245817300487_1.xhtml#s0125) and [5](#S0065245817300487_1.xhtml#s0165).

Rhapsody Statecharts offer a full set of advanced features for specifying reactive behavior. Supporting the entire set of these features is beyond the scope of this work, however, we have selected a subset that contains the most frequently used features. This includes composite and orthogonal states, interlevel transitions (also known as group transitions), and condition and junction connectors. History connectors are an example of an advanced feature that is not supported.

The prototype implementation of our proposed techniques is based on the KLEE symbolic execution engine \[[8](#S0065245817300487_3.xhtml#bb0045)\]. Since KLEE supports only C code, we consider only a subset of Java or C++ action code that has the same syntax as C code, including basic assignment statements, conditional statements, and iterative statements. The data types supported are the basic data types including characters, Booleans, and integers. We also consider the statements used in action code for sending events.

The Statechart models to be used in the evaluation were selected in accordance with the aforementioned assumptions.

### 1.2 Contributions

The proposed research aims to improve the current state of the art in the area of model-based analysis in an evolutionary software development environment. Our contributions specifically include (1) the development, formalization, and proof-of-concept implementation of the proposed optimization techniques mentioned in [Section 5](#S0065245817300487_1.xhtml#s0165), (2) an evaluation that will provide the results showing the benefits of our research methodology, and (3) a concrete example of research that can enrich the analysis capabilities of an existing MDE tool.

### 1.3 Chapter Organization

[Section 2](#S0065245817300487_1.xhtml#s0030) gives an overview of the background. [Section 3](#S0065245817300487_1.xhtml#s0095) discusses the related work. [Section 4](#S0065245817300487_1.xhtml#s0125) presents our standard symbolic execution technique for individuals and communicating Rhapsody Statecharts. [Section 5](#S0065245817300487_1.xhtml#s0165) demonstrates the optimization ideas employed in this research. [Section 6](#S0065245817300487_2.xhtml#s0230) explains the implementation details of the proposed work. [Section 7](#S0065245817300487_2.xhtml#s0260) outlines the evaluation procedure and presents and discusses the evaluation results. [Section 8](#S0065245817300487_3.xhtml#s0295) concludes the work presented in this chapter and outlines future work.

## 2 Background

In this section we provide the background information of the main technologies used in this research. First, we introduce the modeling context used and the types of models considered. Then, we present an overview of symbolic execution and dependence analysis. Finally, we specify the tools we use to realize model differencing and model transformation tasks.

### 2.1 Modeling and Analysis in the IBM Rational Rhapsody Developer MDE Tool

The IBM Rational Rhapsody Developer framework \[[9](#S0065245817300487_3.xhtml#bb0050)\] is one of the commercial tools that support model-driven development, where models are the primary artifacts for software development and are iteratively refined until code can be automatically generated by the tool. The tool is heavily used in practice (e.g., in the automotive industry). It has a number of specialized models (or diagrams) used to describe a software system at different levels of abstraction. We refer only to the two types of models we use in this work: object model diagram (OMD) and Statecharts. A detailed description of all features supported by these models is outside the scope of this work. For simplicity, only a limited set of these features is used in the illustrative example shown in [Fig. 1](#S0065245817300487_1.xhtml#f0130).

![Fig. 1 The base version ABV0 of an example model AB of two communicating objects. (A) The Object Model Diagram (OMD) of our simple model AB. (B) The Statechart of object itsA in (A). (C) The Statechart of object itsB in (A).](images/S0065245817300487/f04-01-9780128151198.jpg)

Fig. 1 The base version AB^(V0) of an example model AB of two communicating objects. (A) The Object Model Diagram (OMD) of our simple model AB. (B) The Statechart of object itsA in (A). (C) The Statechart of object itsB in (A).

#### 2.1.1 Rhapsody Object Model Diagrams

The OMDs are used to specify the structure and the static relationships of the classes and objects in a software system. Rhapsody's OMDs serve, to some extent, the same purpose as the UML's composite structure diagrams, class diagrams and object diagrams. The top-level object in an OMD is usually a composite class that represents the root class of the system and which is also considered as the system container. The IBM Rational Rhapsody code generator directly translates the elements and relationships modeled in an OMD into source code in a specified high-level language (e.g., C, C++, C#, Java, or Ada). [Fig. 1A](#S0065245817300487_1.xhtml#f0130) shows a system AB that is composed of two communicating objects: itsA and itsB. Object itsA is of class A that has an integer attribute x that is initialized to 0 and a protocol of a set of three messages: e1, e2, and e3. Similarly, object itsB is of class B that has an integer attribute y that is initialized to 5 and a protocol of three messages: e4, e5, and e6. Message e1 has an integer argument e1Arg1 and message e5 has an integer argument e5Arg1. The behavior of each object is modeled by the Rhapsody Statecharts shown in [Figs. 1B and C](#S0065245817300487_1.xhtml#f0130), respectively.

#### 2.1.2 Rhapsody Statecharts

Rhapsody Statecharts^([a](#S0065245817300487_3.xhtml#fn0010)) (also known as Harel's Statecharts \[[10](#S0065245817300487_3.xhtml#bb0055)\]) are a visual state-based formalism implemented in the IBM Rational Rhapsody framework to describe the behavior of reactive systems. They extend conventional Mealy machines—a type of finite state machines (FSMs) that perform their action only on firing transitions—with advanced features such as hierarchical states, orthogonal regions, and action code in states and transitions. An action is a reactive behavior associated with a state or a transition that can be carried out when, for instance, entering a state, leaving a state, or when firing a transition. Examples of these actions include updating the values of the machine variables or producing an output to be sent to the environment via events. Rhapsody allows the use of C, C++, or Java to express these actions. A transition is defined in the general format: event\[guard\]/action, that specifies the firing event of the transition, an optional guard condition and an optional action code. Events are stimuli delivered to the Statechart from the environment or other objects in the system and they can have optional user-defined parameters (also called arguments). Timeout events are internal events which can be generated using timers within the Statecharts. In contrast with the machine variables, which are considered as global variables that can be accessed anywhere within the Statechart, event arguments are considered as local variables that have a limited scope that is restricted only to the guard and the action code of the transitions that receive their event. A guard is an optional Boolean expression that can be defined over machine variables and events arguments. A transition is fired when its source state is active, its corresponding event is received, its guard evaluates to true and no higher priority transition is enabled. When a transition is fired, its action is executed and, consequently, the system goes to the transition's target state. Besides the standard assignment and conditional statements that can be used in describing the action code of a transition, there is a domain-specific send event statement which is used to generate an output event to be sent to a specified object. An example of such statement is shown in the action Java code of transition itsA\_T2 in [Fig. 1B](#S0065245817300487_1.xhtml#f0130), which is itsB.gen(new e5(5)); that is used to generate event e5 with the event's argument e5Arg1 set to 5 to object itsB. Accordingly, the argument value of the event e5 is stored in a variable called params that can be accessed using the statement params.e5Arg1.

Apart from whether the given Statecharts satisfy their specification, there are a list of basic and intuitive design rules any given Statechart model should satisfy. This includes the reachability of states, the satisfiability of guards and the availability of input events. The task of verifying whether these rules are satisfied looks very simple for Statecharts like the ones in [Fig. 1B and C](#S0065245817300487_1.xhtml#f0130) but it gets more complex as these models get larger and when more advanced modeling features are used, which is the typical case when building industrial real-time systems.

#### 2.1.3 Analysis and Verification of State-Based Models

Existing analysis methods to analyze state-based models are divided into two categories: model-level analysis and code-level analysis. The motivation of the code-level analysis approaches stems from the fact that these models are executable and we can easily generate their corresponding code and use some of the model checkers for C/C++ or Java code or one of the static analysis tools would help in finding possible problems at the code-level. However, it is difficult for a general static analysis tool to figure out the high-level intent of any piece of code we feed to it and therefore they are typically incapable of revealing model-level problems (e.g., unreachable states and dead ends). Also, it is not always the case that we would be able to generate the code, especially with incomplete specifications. Additionally, the results provided from a code-level analysis are typically more detailed which usually makes them less intuitive for designers and modelers. Other challenges include the difficulty of tracing back the errors generated in the code to its source at the model level and to adapt existing analysis tools (e.g., model checkers, symbolic execution engines, or static analysis tools) to handle domain-specific statements found in the generated code. For these reasons, we believe that model-level analysis is the most appropriate way to handle this task. Therefore, the motivation of our research is to highlight the importance of the types of analysis or verification to be carried out on the model level.

### 2.2 Symbolic Execution

Symbolic execution is a program analysis technique that allows the execution of programs in a parametric way using symbolic inputs to derive precise characterizations of their properties and their execution paths. It has first introduced in the 1970s by Clarke \[[11](#S0065245817300487_3.xhtml#bb0060)\] and King \[[1](#S0065245817300487_3.xhtml#bb0010)\] for program testing. Since 2003, much research effort has been devoted to improve the effectiveness, the efficiency, and the applicability of the traditional technique \[[12](#S0065245817300487_3.xhtml#bb0065)–[14](#S0065245817300487_3.xhtml#bb0075)\].

The main idea is to substitute program inputs with symbolic values and then execute the program parametrically such that (1) the values of all program variables are computed as symbolic expressions over the symbolic input values, and (2) all possible execution paths are explored. The result from the symbolic execution of a program is a tree-based structure called SET. The nodes of a SET represent the symbolic program states and the edges represent the transitions between these states. Each program symbolic state consists of a program location, the set of program variables and their symbolic valuations, and a path constraint (PC) which is the conjunction of all the logical constraints collected over the program variables to reach that program location. The feasible paths of a SET characterize all the distinct execution paths of a program. Decision procedures and SMT solvers are used to check the satisfiability of each path constraint (PC).

The resulting SET forms the basis for many program analysis, verification, and testing activities (e.g., bug finding, dead code detection, invariants checking, program equivalence checking, regression analysis, and test case generation). For instance, it can be used to optimize the testing process by generating the minimum number of test cases required to inspect all feasible program paths. [Fig. 2B](#S0065245817300487_1.xhtml#f0010) (resp., [2D](#S0065245817300487_1.xhtml#f0010)) shows the SET of the sample code in [Fig. 2A](#S0065245817300487_1.xhtml#f0010) (resp., [2C](#S0065245817300487_1.xhtml#f0010)). The exploration is carried out in a depth-first manner. Examples of other exploration strategies are breadth first, random, or heuristic-based exploration. Solving the path constraints of the leaf nodes of each SET will provide us with the sample input values that can be used to test each feasible path. Program locations that do not have any corresponding symbolic states in the program SET indicate dead code. For example, program locations 8–9 in the code snippet foo\_V2 are dead code.

![Fig. 2 Symbolic execution of programs—Example 1. (A) Code Snippet of foo\_V1. (B) SET of foo\_V1. (C) Code Snippet of foo\_V2. (D) SET of foo\_V2.](images/S0065245817300487/f04-02p1-9780128151198.jpg)

Fig. 2 Symbolic execution of programs—[Example 1](#S0065245817300487_1.xhtml#enun0035). (A) Code Snippet of foo\_V1. (B) SET of foo\_V1. (C) Code Snippet of foo\_V2. (D) SET of foo\_V2.

One of the biggest challenges in symbolic execution is the path explosion problem especially for large programs and programs with unbounded loops and recursion. Examples of proposed solutions include setting upper bounds for loops, summarizing loop effects, employing some state matching criteria (e.g., state subsumption) for pruning redundant paths and reducing the state space, using heuristics for path finding to achieve some user-defined coverage criteria, or dividing a program into independent parts and run the symbolic execution for each part in parallel \[[14](#S0065245817300487_3.xhtml#bb0075)\]. For example, [Fig. 3B](#S0065245817300487_1.xhtml#f0015) shows a finite version of the SET of the code snippet in [Fig. 3A](#S0065245817300487_1.xhtml#f0015) \[[12](#S0065245817300487_3.xhtml#bb0065)\]. This finitized SET version is obtained by performing a state matching technique called subsumption checking to determine when a symbolic state is revisited and hence pruning the exploration at this point. For any given two symbolic states SS[i] and SS[j], SS[j] is subsumed by SS[i] if both symbolic states represent the same program location and if the concretization of SS[j] is included in the concretization of SS[i]. For example, in [Fig. 3B](#S0065245817300487_1.xhtml#f0015), the symbolic state SS7 is subsumed by the symbolic state SS4 and hence the exploration of the symbolic state SS7 can be avoided.

![Fig. 3 Symbolic execution of programs—Example 2. (A) Code Snippet of testme\_inf \[12\]. (B) A finite SET of testme\_inf.](images/S0065245817300487/f04-03-9780128151198.jpg)

Fig. 3 Symbolic execution of programs—[Example 2](#S0065245817300487_1.xhtml#enun0050). (A) Code Snippet of testme\_inf \[[12](#S0065245817300487_3.xhtml#bb0065)\]. (B) A finite SET of testme\_inf.

Other challenges include (1) the limitation of constraint solvers in solving very complex and nonlinear constraints and (2) the inability to handle external library calls. Examples of proposed solutions include concolic symbolic execution (an variant of the traditional technique that enables the use of concrete values for unmanageable symbolic expressions) \[[15](#S0065245817300487_3.xhtml#bb0080), [16](#S0065245817300487_3.xhtml#bb0085)\], performing constraints simplification and providing models to simulate or abstract the behavior of external modules.

Examples of existing symbolic execution tools are jCUTE and Java PathFinder (JPF) for Java, EXE and its successor KLEE for C and C++, and Pex for the .NET Framework.

Symbolic execution is not restricted only to programs; it has been also applied to a variety of state-based models including Input Output Symbolic Transition Systems \[[2](#S0065245817300487_3.xhtml#bb0015)\], Statecharts \[[17](#S0065245817300487_3.xhtml#bb0090)\], UML State Machines \[[18](#S0065245817300487_3.xhtml#bb0095)\], and recently UML-RT State Machines \[[3](#S0065245817300487_3.xhtml#bb0020)\].

### 2.3 Dependence Analysis

Dependence analysis has been extensively studied in research areas such as program refactoring, parallelization, and optimization. It also supports many activities in software maintenance such as comprehension, slicing, impact analysis, and regression test reduction. Dependence analysis has been primarily studied in the context of programming languages where dependences are defined between statements and variables using their control flow graphs (CFGs). Eventually, the same concept has been adapted for other types of software artifacts to capture potential interactions within such artifacts, e.g., Extended Finite State Machines (EFSMs) \[[19](#S0065245817300487_3.xhtml#bb0100)–[21](#S0065245817300487_3.xhtml#bb0110)\] where interactions are defined between transitions since they are the “active” elements of these types of models. Examples of dependences are control dependence, data dependence, and communication dependence.

In our setting, we transform Rhapsody Statecharts into an EFSMs-like representation called Mealy-like machines (MLMs) (the formal definition on an MLM is presented in [Section 4.1.1](#S0065245817300487_1.xhtml#s0135)), therefore we can adopt the definitions of dependencies from conventional EFSMs. In the sequel, we will refer to a set of definitions for computing these dependences as adopted from \[[22](#S0065245817300487_3.xhtml#bb0115)\] based on the work presented in \[[19](#S0065245817300487_3.xhtml#bb0100)–[21](#S0065245817300487_3.xhtml#bb0110)\].

#### 2.3.1 Control Dependence

Classical definitions of control dependence in sequential programs state that a statement s[j] is control dependent on a statement s[i] if statement s[i] is a conditional that affects the execution of statement s[j]. For example, in an if-then-else construct, statements in the two branches of the conditional statement are control dependent on the predicate. Since state-based formalisms differ from sequential programs, some adapted definitions are given to capture the control dependence in such formalisms. The one that applies to state machines with possible nontermination is called nontermination sensitive control dependence (NTSCD) (see [Definition 2](#S0065245817300487_1.xhtml#enun0015)), which is given in terms of maximal paths (see [Definition 1](#S0065245817300487_1.xhtml#enun0010)).

Definition 1

(Maximal path).

A path in a state machine is defined as a finite sequence of consecutive transitions that are organized such that no state is visited more than once. A path is called maximal if it terminates in an end state (state with no outgoing transitions) or it terminates in a cycle or it reaches the initial state again. A cycle is a set of transitions that forms a strongly connected component.

 

Definition 2

(Nontermination sensitive control dependence).

$\\mathtt{t\_{i}\\mathrm{\\overset{NTSCD}{\\rightarrow}}t\_{j}}$![si1\_e](images/S0065245817300487/si1_e.png) means that t[j] is nontermination sensitive control dependent on a transition t[i] iff:

1.  (1) for all paths π ∈ MaximalPaths(targetState(t[i])), the sourceState(t[j]) belongs to π;
2.  (2) t[i] has at least one sibling t[k] and there exists a path π′ ∈ MaximalPaths(sourceState(t[k])) such that sourceState(t[j]) does not belong to π′;

where MaximalPaths(s) is the set of paths that have s as the source state of the first transition on each path and t[k] is said to be a sibling transition of t[i] if sourceState(t[k]) = sourceState(t[i]).

#### 2.3.2 Data Dependence

Typical data dependence definitions are given in terms of variable definitions and uses. In the context of state machines, a variable is used on a transition if its value appears in the guard of the transition or appears on the right side of an assignment-statement or in the Boolean expression of an if-statement, or in an output-statement in the action code of the transition. A variable is defined on a transition if it appears on the left-hand side of an assignment-statement in the action code of the transition. Based on this, the following definition is given \[[19](#S0065245817300487_3.xhtml#bb0100), [22](#S0065245817300487_3.xhtml#bb0115)\].

Definition 3

(Data Dependence (DD)).

$\\mathtt{t\_{i}\\mathrm{\\overset{DD}{\\rightarrow}}t\_{k}}$![si2\_e](images/S0065245817300487/si2_e.png) means that t[k] is data dependent on t[i] with respect to variable v iff:

1.  (1) v ∈ Def(t[i]), where Def(t[i]) is the set of variables defined by the action code of transition t[i];
2.  (2) v ∈ Use(t[k]), where Use(t[k]) is the set of variables used in the guard or the action code of transition t[k];
3.  (3) there exists a path in the state machine from t[i] to the targetState(t[k]) along which v is not modified.

#### 2.3.3 Communication Dependence

Two transitions are called communication dependent iff: (1) each transition belongs to a different MLM (the formal definition on an MLM is presented in [Section 4.1.1](#S0065245817300487_1.xhtml#s0135)) and (2) one transition is triggered by an event that is generated by the action code of the second transition \[[19](#S0065245817300487_3.xhtml#bb0100), [22](#S0065245817300487_3.xhtml#bb0115)\].

Definition 4

(Communication Dependence (COMD)).

Given two transitions t[i] and t[k], $\\mathtt{t\_{i}\\mathrm{\\overset{COMD}{\\rightarrow}}t\_{k}}$![si3\_e](images/S0065245817300487/si3_e.png) means that t[k] is communication dependent on t[i] iff:

1.  (1) t[i] ∈ T(MLM[i]) and t[k] ∈ T(MLM[k]), where i≠k;
2.  (2) e(t[k])—the event (or trigger) of t[k] is generated by the action code of t[i].

The detailed steps for computing the maximal paths, the nonterminating sensitive control dependence (NTSCD), the data dependence (DD) in an MLM, as well as the communication dependence (COMD) in a model of communicating MLMs are shown in [Algorithm 1](#S0065245817300487_1.xhtml#b0010), [Algorithm 2](#S0065245817300487_1.xhtml#b0015), [Algorithm 3](#S0065245817300487_1.xhtml#b0020), and [Algorithm 4](#S0065245817300487_1.xhtml#b0025), respectively. In our work we consider only data and communication dependences, however, we listed the others for completeness. [Fig. 4](#S0065245817300487_1.xhtml#f0135) depicts the data and communication dependences that exist between the Statecharts describing the behavior of the two objects itsA and itsB of System AB shown in [Fig. 1](#S0065245817300487_1.xhtml#f0130).

Algorithm 1

Maximal Paths Computation

Inputs:

1: An MLM representation of a Rhapsody Statechart model MLM = (S, T, V, s[0]) that is defined in terms of states S, transitions T, variables V and an initial state s[0] ∈ S

2: A mapping, *o**u**t**T**r**a**n**s* : *S*→𝒫(*T*)![si4\_e](images/S0065245817300487/si4_e.png), of states to their outgoing transitions

Output:

1: maximalPaths(MLM)

Steps:

1: endStates(MLM) ← ∅

2: cycles(MLM) ← ∅

3: maximalPaths(MLM) ← ∅

4: for all (s ∈ S)∧(outTrans(s)=∅) do

5:     endStates(MLM) ← endStates(MLM) ∪ {s}

6: end for

7: //Explore the Statechart in depth-first-search manner

8: Push the initial state s[0] into a stack st

9: Mark outTrans(s[0]) as unexplored

10: while st is not empty do

11:     currentStateToExplore ← topElement(st)

12:     for all (t[o] ∈ T)∧(t[o] ∈ outTrans(currentStateToProcess))∧(t[o] is still unexplored) do

13:         if (targetState(t[0])=s[0])∨(targetState(t[0]) ∈ endStates(MLM))∨(targetState(t[0]) ∈ cycles(MLM)) then

14:             Report a maximal path π ← st+targetState(t[o])

15:             maximalPaths(MLM) ← maximalPaths(MLM) ∪ {π}

16:             Mark t[o] as explored

17:         else if targetState(t[0]) ∈ st then

18:             Report a cycle ↺ ← st.subList(indexOf(targetState(t[0])), size(st)) + targetState(t[0])

19:             cycles(MLM) ← cycles(MLM) ∪ {↺}

20:             Report a maximal path π ← st.subList(0, size(st))+targetState(t[0])

21:             maximalPaths(MLM) ← maximalPaths(MLM) ∪ {π}

22:             Mark t[o] as explored

23:         else

24:             Push targetState(t[0]) into st

25:             Mark outTrans(targetState(t[0])) as unexplored

26:             Mark t[o] as explored

27:             Break

28:         end if

29:     end for

30:     Pop currentStateToProcess from st

31:   end while

Algorithm 2

Nonterminating Sensitive Control Dependence (NTSCD) Computation

Inputs:

1: An MLM representation of a Rhapsody Statechart model MLM = (S, T, V, s[0]) that is defined in terms of states S, transitions T, variables V and an initial state s[0] ∈ S

2: maximalPaths(MLM)

Output:

1: A mapping, *C**D* : *T*→𝒫(*T*)![si5\_e](images/S0065245817300487/si5_e.png), of transitions to their control dependent transitions

Steps:

1: // Finding maximalPaths(T)

2: for all t ∈ T do

3:     for all π ∈ maximalPaths(MLM) do

4:         if π.indexOf(targetState(t)) = π.indexOf(sourceState(t) + 1 then

5:             maximalPaths(t) ← maximalPaths(t) ∪ {π}

6:         end if

7:     end for

8: end for

9: // Finding CD(T)

10: for all (t[i] ∈ T) ∧ (siblingTransitions(t[i]).size() ≥1) do

11:     CD(t[i]) ← ∅

12:     for all (s ∈ S) ∧(s ∈ ∀maximalPaths(t[i])) do

13:         if (t[k] ∈ T) ∧ (t[k] ∈ siblingTransitions(t[i])) ∧ (∃π ∈ maximalPaths(t[k])) ∧ (s∉π) then

14:             for all (t[o] ∈ T) ∧ (t[o] ∈ outTrans(s)) do

15:                 CD(t[i]) ← CD(t[i]) ∪ {t[0]}

16:             end for

17:         end if

18:     end for

19:   end for

Algorithm 3

Data Dependence (DD) Computation in an MLM

Inputs:

1: An MLM representation of a Rhapsody Statechart model MLM = (S, T, V, s[0]) that is defined in terms of states S, transitions T, variables V and an initial state s[0] ∈ S

2: A mapping, *U**s**e* : *T*→𝒫(*V*)![si6\_e](images/S0065245817300487/si6_e.png), of transitions to the set of variables each transition uses

3: A mapping, *D**e**f* : *T*→𝒫(*V*)![si7\_e](images/S0065245817300487/si7_e.png), of transitions to the set of variables each transition defines

Output:

1: A mapping, *D**D* : *T*→𝒫(*T*)![si8\_e](images/S0065245817300487/si8_e.png), of transitions to their data dependent transitions with respect to V

Steps:

1: for all t ∈ T such that: (∃v ∈ V) ∧ (v ∈ Use(t)) // i.e., for all transitions that use at least one variable do

2:     for all (v ∈ V) ∧ (v ∈ Use(t)) // i.e., for all the variables that are used in t do

3:         // Apply backward depth-first-search to find the first transitions defining the variable v

4:         Push the sourceState(t) into a stack st

5:         while st is not empty do

6:             currentStateToProcess ← topElement(st)

7:             for all (t[i] ∈ T) ∧ (t[i] ∈ incomingTransition(currentStateToProcess)) ∧ (t[i] has not yet been explored)) do

8:                 DD(t[i]) ← ∅

9:                 if v ∈ Def(t[i]) // i.e., v is defined in t[i] then

10:                     DD(t[i]) ← DD(t[i]) ∪ {t}w.r.t.v

11:                     Mark t[i] as explored

12:                 else

13:                     Mark t[i] as explored

14:                     Push the sourceState(t[i]) into st

15:                     Break

16:                 end if

17:             end for

18:         end while

19:     end for

20: end for

Algorithm 4

Communication Dependence (COMD) Computation

Inputs:

1: A global model/system of n asynchronously communicating MLMs *M* = (*M**L**M*^(*M*), *Q*^(*M*), *s*[0]^(*M*), *V*^(*M*), *V*[0]^(*M*))![si9\_e](images/S0065245817300487/si9_e.png) with MLM^M = (MLM[1], MLM[2], …, MLM[n]) and MLM[i] = (S[i], V[i], E[i], EA[i], T[i], s[0i], V[0i]) is the i^(th) MLM in M

2: A mapping, *S**e**n**d* : T→𝒫(*E*^(*o*))![si10\_e](images/S0065245817300487/si10_e.png), of all transitions in MLM^M to the set of output events each transition may generate as a result of evaluating/executing their action code

Output:

1: A mapping, COMD : T→𝒫(T)![si11\_e](images/S0065245817300487/si11_e.png), of transitions to their communication dependent transitions

Steps:

1: for all MLM[i] ∈ MLM^M do

2:     for all t[x] ∈ T[i] do

3:         COMD(t[x]) ←⌀![si12\_e](images/S0065245817300487/si12_e.png)

4:         for all t[y] ∈ T do

5:             if e(t[x]) ∈ Send(t[y]) ∧ MLM(t[x])≠MLM(t[y]) then

6:                 COMD(t[x]) ← COMD(t[x]) ∪ {t[y]}

7:             end if

8:         end for

9:     end for

10: end for

![Fig. 4 Dependency graph of system ABV0.](images/S0065245817300487/f04-04-9780128151198.jpg)

Fig. 4 Dependency graph of system AB^(V0).

 

### 2.4 Model Differencing

Model differencing is the practice of identifying and locating the changes between different versions of a model. As models evolve, keeping track of their changes is essential for their maintainability during their lifetime. Existing approaches and tools for model differencing depend on some similarity-based matching criteria to guide the search process \[[23](#S0065245817300487_3.xhtml#bb0120)\]. Some of them consider the syntactic similarities between models elements and others try to search for the semantic similarities as well \[[24](#S0065245817300487_3.xhtml#bb0125)\]. In our work, we use the IBM Rational Rhapsody DiffMerge tool to find the differences between Rhapsody Statecharts. The tool compares Rhapsody projects that belong to the same ancestor (i.e., they are all models originating from the same base version) and generates a difference report with the differences between the matched elements in each project. As we notice, the tool depends on some globally unique identifiers which are assigned internally to model elements to match between the elements in each model and then to find the differences between the matched ones.

### 2.5 Model Transformation

Model transformation is the technology that is used in the area of MDE to convert models to other software artifacts (e.g., code) \[[23](#S0065245817300487_3.xhtml#bb0120)\]. When the transformation is carried out to convert a source model to a target model and both models conform to the same meta-model, we call it an endogenous transformation. This type of model transformation is used to perform tasks such as model refactoring and optimization in general. On the other hand when the transformation is carried out to convert a source model to a target model and both models conform to different meta-models, we call this an exogenous transformation. This type of transformation is used handle tasks such as code generation, reverse engineering, and migration. In our setting, we need to perform exogenous transformations to transform Rhapsody Statecharts to our internal MLM representation such that we can symbolically execute the model. Therefore, we use the model transformation technologies offered by the IBM Rational Rhapsody Developer RulesComposer Add-On. The add-on is built based on the Eclipse Modeling Framework (EMF) and it provides the infrastructure required to perform common MDE services such as model and meta-model manipulation, model-to-model transformation, and model-to-text generation. The language used to define model transformations is called Model Query Language (MQL) and the language used to define text templates is called Text Generation Language (TGL) and they are both imperative and proprietary languages. MQL is also used to launch text generations and to define the expressions used within TGL.

### 2.6 Summary

In this section we have presented the background information. First, we have introduced the modeling context used and briefly described the two types of models considered. Namely, the OMDs for describing the structural aspects of the system and the Statecharts for describing the behavioral aspects of the system. We also have showed the basics of two analysis techniques: symbolic execution and dependence analysis. We have introduced symbolic execution of programs with examples showing some of the most common applications of the technique and explaining the state matching criteria used to reduce the state space of programs with loops. Additionally, we have provided the definitions and the algorithms used to compute the three types of dependences that exist between transitions in EFSMs-like representations. Last, we have defined and specified the model differencing and the model transformation tools used in the context of our work.

## 3 Related Work

In this section we first introduce a general description of our classification of the two most common ways used in the literature to reconcile analysis and evolution efficiently in software development: reused-based (artifact-oriented) reconciliation and reduction-based (analysis-oriented) reconciliation \[[25](#S0065245817300487_3.xhtml#bb0130)\]. Second, we discuss related work in the context of the proposed research and based on the two classified reconciliation methods. We review studies that (1) propose approaches for the analysis and the verification of Statecharts-like models and highlight those that are based on symbolic execution, (2) propose incremental analysis or verification techniques for evolving programs and highlight those which are built specifically to improve the efficiency of symbolic execution, and (3) motivate and realize the concept of incremental verification in the context of model-based development.

### 3.1 Two Ways to Reconcile Analysis and Evolution Efficiently

Analysis and verification are crucial and expensive activities in the development of real-time and safety-critical software systems. The prerequisite preparation required to run these activities is not trivial in terms of the time it costs and the technologies it uses. The output from such prerequisite preparation process is a special type of artifact that represents one or more views of the system under development in the input language of the analysis or the verification method to be used. The generation of these analysis-related artifacts is usually done using some transformation or translation technologies that allow the semantic mapping between the artifacts used to build the system and those that are used to analyze and verify it. The output from running the analysis or verification process on these auxiliary or intermediate artifacts is used to verify or disprove the correctness of the analyzed properties. Classical analysis methods were focused on analyzing source code related artifacts (both statically and dynamically) and on the intralevel as well as the interlevel. The intralevel is used to analyze the correctness of the individual artifacts in isolation of the others, while the interlevel is used to analyze the overall interoperability of those models that are communicating with others. With the emergence of MDE and agile methods, analysis techniques have been extended to analyze the more abstract architecture artifacts (both structural and behavioral). Examples of static analysis-related artifacts and their usages include (1) CFGs for static analysis and optimization \[[26](#S0065245817300487_3.xhtml#bb0135)\], (2) dependency graphs for change impact analysis and slicing \[[19](#S0065245817300487_3.xhtml#bb0100)\] and for regression test selection \[[27](#S0065245817300487_3.xhtml#bb0140)\], (3) theorem prover formalization for formal verification \[[28](#S0065245817300487_3.xhtml#bb0145)\], and (4) SETs for reachability analysis, invariant checking and test case generation \[[2](#S0065245817300487_3.xhtml#bb0015), [29](#S0065245817300487_3.xhtml#bb0150)\]. Examples of dynamic analysis-related artifacts include run-time and simulation execution traces which can be used for performance and configuration analysis and run-time errors detection \[[30](#S0065245817300487_3.xhtml#bb0155)\].

With the iterative and incremental development of modern development life-cycles, software systems are continuously evolving. Maintaining and analyzing an ever-changing system is essential for its quality and continuity, yet it is a very expensive process and requires considerable efforts. Looking for effective techniques to optimize the analysis activity of these systems as they evolve is vital and it starts with a better identification and understanding of the subject change (i.e., the type of the change and its location) as well as the type of the analysis to be carried out and of course taking into consideration whether a previous analysis of the same type has been conducted or not. For instance, some refactoring changes such as consistent renaming should not invalidate a previous analysis result but would require a refactoring of the previously created analysis-related artifacts to maintain the correctness of the result. On the other hand, some corrective, modification, addition or deletion changes may or may not invalidate a previous analysis result and hence require a complete or partial regeneration of the analysis-related artifacts and rerunning the analysis on the newly generated analysis-related artifacts.

In the sequel we discuss two different scenarios where optimization opportunities (or reconciliations) may exist.

1.  (1) Reused-based (artifact-oriented) reconciliation: The first scenario is the case where analysis-related artifacts are regularly retained (i.e., not discarded) and they can be used to run different types of analyses (e.g., SETs and dependency graphs). In this case there is an opportunity to optimize the process of regenerating these analysis-related artifacts after a change by reusing the unaffected parts of the already existing ones and regenerating only the change-related parts. The output from this process are complete updated analysis-related artifacts which are consistent with the system in its most recent state (i.e., after the change) and can be used to run any of its related analyses. By distinguishing the newly generated parts from the reused parts, we can also optimize the process of rerunning any previously conducted analyses such that only the newly generated parts of these analysis-related artifacts are considered. Incremental model transformation \[[31](#S0065245817300487_3.xhtml#bb0160)\], extreme model checking \[[32](#S0065245817300487_3.xhtml#bb0165)\], memoized symbolic execution \[[7](#S0065245817300487_3.xhtml#bb0040)\], and regression model checking \[[33](#S0065245817300487_3.xhtml#bb0170)\] are all examples of existing approaches that are based on this reconciliation strategy.
2.  (2) Reduction-based (analysis-oriented) reconciliation: The second scenario is the case where analysis-related artifacts are discarded but there is certainty about the validity of the system in its previous state (i.e., before the change) with respect to a specific type of analysis and the goal is to find the most effective way to rerun the same type of analysis on the system in its current state (i.e., after the change). In this case, one possible opportunity for optimization is to rerun the analysis in a reduced mode or context taking into consideration only the changed parts and their dependencies. The output from this process are partial, yet sufficient, analysis-related artifacts that can be used to run only the same type of analysis and to conclude the overall correctness of the system after the change even though the new analysis does not cover the whole system. Existing work for incremental equivalence checking \[[34](#S0065245817300487_3.xhtml#bb0175)–[39](#S0065245817300487_3.xhtml#bb0200)\], directed incremental symbolic execution \[[6](#S0065245817300487_3.xhtml#bb0035)\], and incremental property checking \[[40](#S0065245817300487_3.xhtml#bb0205)\] employ this idea.

### 3.2 Analysis and Verification of Statechart-Like Models

Model checking-based approaches: The majority of existing analysis methods for Statechart-like models (e.g., UML state machines, UML-RT, STATEMATE, and Stateflow) require a translation to the input language of existing formal verification tools, mainly model checkers such as SPIN \[[41](#S0065245817300487_3.xhtml#bb0210)\] or SMV \[[42](#S0065245817300487_3.xhtml#bb0215)\]. Most of the time, the translation process is nontrivial and it restricts the support of the key features of the model to those supported by the model checker to be used and hence makes integration and use with modern MDE tools difficult. Another category of approaches analyze the C or Java code generated from these models and use one of the model checkers for these languages (e.g., Java Pathfinder \[[43](#S0065245817300487_3.xhtml#bb0220)\] or CBMC—a Bounded Model Checker for C and C++ \[[44](#S0065245817300487_3.xhtml#bb0225)\]). On the other hand, there are fewer approaches that intend to provide domain-specific analysis capabilities by developing domain-specific model checkers that are tailored to the modeling language of interest and hence support more sophisticated features and reduce the semantic gap between the modeling language and the specification language of a general-purpose model checker (e.g., the verification methods implemented within the FUJABA Real-Time tool \[[45](#S0065245817300487_3.xhtml#bb0230)\] or the VIS model checker in a very early version of the Rhapsody tool \[[46](#S0065245817300487_3.xhtml#bb0235)\]).

Symbolic execution-based approaches: Besides the model checking-based approaches, there are several approaches that adopt the symbolic execution analysis technique of programs and use it in the context of state-based models including:

*   • Modechart specifications (a variation of Harel Statecharts that incorporates timing constraints in the models) for test sequences generation \[[47](#S0065245817300487_3.xhtml#bb0240)\];
*   • Labeled Transition Systems (LTSs) for test case generation \[[48](#S0065245817300487_3.xhtml#bb0245)\] and test case selection \[[49](#S0065245817300487_3.xhtml#bb0250)\];
*   • Input Output Symbolic Transition Systems (IOSTSs) \[[2](#S0065245817300487_3.xhtml#bb0015)\] for test purpose definition;
*   • STATEMATE Statecharts \[[17](#S0065245817300487_3.xhtml#bb0090)\] and UML State Machines \[[18](#S0065245817300487_3.xhtml#bb0095)\] for verifying temporal properties of the subject models;
*   • Simulink/Stateflows \[[50](#S0065245817300487_3.xhtml#bb0255)\] for analysis and test case generation of flight software using Java PathFinder and Symbolic PathFinder;
*   • UML-RT State Machines \[[3](#S0065245817300487_3.xhtml#bb0020)\] to support a variety of analyses for this type of models.

Our research belongs to this category of approaches. We use symbolic execution to support the analysis of a slightly different type of state-based models which are Rhapsody Statecharts. Our technique differs from others in that (1) it reuses the off-the-shelf symbolic execution engine KLEE \[[8](#S0065245817300487_3.xhtml#bb0045)\] and (2) it supports the incremental analysis of the subject models as they evolve.

### 3.3 Incremental Analysis and Verification Techniques for Evolving Programs

A comprehensive survey of existing work in this area of research is outside the scope of our study. Therefore, we only provide examples of two categories of work that use similar ideas as ours in building their incrementality approaches, namely, reuse-based (or artifact-oriented) incremental approaches and reduction-based (or analysis-oriented) incremental approaches. We noticed that the majority of existing work belongs to the first category.

Reused-based (artifact-oriented) incremental approaches: In the first category of approaches incrementality is achieved by reusing analysis-related artifacts. Examples of analysis-related artifacts that have been reused in the literature are state-space representations (e.g., abstract reachability trees and SETs) \[[32](#S0065245817300487_3.xhtml#bb0165), [33](#S0065245817300487_3.xhtml#bb0170), [51](#S0065245817300487_3.xhtml#bb0260), [52](#S0065245817300487_3.xhtml#bb0265)\], CFGs and dependency graphs \[[52](#S0065245817300487_3.xhtml#bb0265), [53](#S0065245817300487_3.xhtml#bb0270)\], constraint solving results \[[7](#S0065245817300487_3.xhtml#bb0040), [8](#S0065245817300487_3.xhtml#bb0045), [54](#S0065245817300487_3.xhtml#bb0275)–[56](#S0065245817300487_3.xhtml#bb0285)\], counter example traces \[[40](#S0065245817300487_3.xhtml#bb0205), [57](#S0065245817300487_3.xhtml#bb0290)\], abstraction precisions \[[58](#S0065245817300487_3.xhtml#bb0295)\], some compressed representation in the form of hash codes of verified properties \[[59](#S0065245817300487_3.xhtml#bb0300)\], and function summaries \[[60](#S0065245817300487_3.xhtml#bb0305)\].

In analogy to the idea of extreme programming that advocates the use of regression testing side-by-side with stepwise software development, the idea of extreme model checking is proposed in \[[32](#S0065245817300487_3.xhtml#bb0165)\] to support regression verification. The proposed approach extended the lazy abstraction algorithm implemented in the unbounded model checker BLAST for C programs to support incremental checking of safety properties. This is done by caching and reusing the abstract reachability trees resulting from a previous model checking run. A similar approach is presented in \[[51](#S0065245817300487_3.xhtml#bb0260)\] to perform an incremental state-space exploration for evolving Java programs by recording and reusing the state-space resulting from a previous model checking run to speed up the exploration process of subsequent program versions. The realization of this approach is built in the context of the Java PathFinder (JPF) symbolic execution framework. Inspired by this latter work, a technique of regression model checking is presented in \[[33](#S0065245817300487_3.xhtml#bb0170)\]. Two modes of operations are defined recording mode and pruning mode. Recording mode is used to compute and store the state space and state coverage resulting from exploring a new program location. When a change is made to a program whose state space before the change has previously been computed and recorded, the model checker operates in the pruning mode where a change impact analysis is used to identify the impacted elements in the old state space that need to be updated. Only program locations related to these impacted elements are going to be reexplored during the recording operation mode of the model checker.

The idea of memoizing and reusing the path constraints found in the SET of a Java program to optimize the symbolic execution of the program's next revision is introduced in \[[7](#S0065245817300487_3.xhtml#bb0040)\]. Reusing a previous SET will avoid the reexecution of common paths between the new version of a program and its previous one and hence speed up the symbolic execution of the new version.

The idea of caching and reusing constraint solving proofs in the context of symbolic execution is first used in the implementation of the symbolic execution engine KLEE \[[8](#S0065245817300487_3.xhtml#bb0045)\]. The goal is to reduce the number of calls to the constraint solver while running the symbolic execution and hence mitigating some of the scalability issues related to this technique. The same idea has been further explored and applied in the context of other symbolic execution engines such as JPF \[[54](#S0065245817300487_3.xhtml#bb0275), [55](#S0065245817300487_3.xhtml#bb0280)\], Crest, and JBSE \[[56](#S0065245817300487_3.xhtml#bb0285)\]. In all such work, a repository of constraint proofs is created that is augmented with a number of powerful simplification techniques to facilitate the optimal reuse of constraints including slicing, normalization and canonicalization. This constraint reusing mechanism can be applied to optimize the symbolic execution of similar or different programs.

The idea of reusing previous model checking outcomes including the counter-examples of failed properties (also called verification witnesses) is presented in \[[57](#S0065245817300487_3.xhtml#bb0290)\] to optimize the following reverification runs and in \[[40](#S0065245817300487_3.xhtml#bb0205)\] to perform incremental property checking. A key goal in such approaches is to reduce the number of properties to be rechecked after an update has been made to the set of properties required for a given program.

Different types of analysis can be performed in the context on model checking (e.g., explicit-value analysis and predicate analysis). Each type needs to be explicitly defined and supplied to the model checker to determine the scope of the analysis (e.g., location-scoped, function-scoped, or global-scoped) and to guide the abstraction process followed by the model checker to create a proper and sufficient abstraction of the model state space. The definitions of such analysis-based requirements are called program precisions which can be recorded and reused for speeding up the subsequent analysis of an evolving program as presented in \[[58](#S0065245817300487_3.xhtml#bb0295)\]. Intuitively, the effectiveness of such an approach depends on the class of program changes introduced in a program's next revision which may or may not require refinement of old precisions.

The idea of saving and reusing a compressed representation (hash codes) of the parts of the model parse tree relevant to a given property is presented in \[[59](#S0065245817300487_3.xhtml#bb0300)\] for efficient regression verification. When a change is committed in the system, a new hash code is computed and is compared with the hash code value generated from the previous verification run. If both values are identical then there is no need to reverify the given property, otherwise a reverification is needed.

In \[[60](#S0065245817300487_3.xhtml#bb0305)\], an incremental upgrade checking approach is presented and implemented in the context of bounded model checking (BMC). It reuses the function summaries generated from model checking a previous program version to check the validity of their corresponding modified functions in the new program version. If such validity check fails for a given modified function, an upgrade check is performed to create a new valid summary to replace the invalid one.

A whole program path profiling technique is presented in \[[61](#S0065245817300487_3.xhtml#bb0310)\] that uses execution traces collected from running a system test suite to generate a compact graphical representation in a form of directed acyclic graph (DAG) of the control flow of the entire system including interprocedural paths. The generated DAG can be used to perform more precise program analysis such as dynamic impact analysis \[[62](#S0065245817300487_3.xhtml#bb0315)\]. An incremental version of such dynamic impact analysis is presented in \[[53](#S0065245817300487_3.xhtml#bb0270)\] which reuses the DAG of a previous release of a system to incrementally maintain the DAG of the system as it evolves (i.e., a change is made to its behavior or its test suite).

In \[[52](#S0065245817300487_3.xhtml#bb0265)\], an incremental approach for interprocedural analysis of safety properties is presented. The main idea depends on reusing previous derivation graphs resulting from the synchronous product of program CFGs and a checking automaton describing some safety properties to speed up the reanalysis of the program after a change has been made to its specification or to its safety properties.

Reduction-based (analysis-oriented) incremental approaches: On the other hand, in the second category of approaches incrementality is achieved by reducing the scope of the new analysis to focus mainly on the parts of the system that are impacted by the change given that (1) some analysis has already been conducted on the system before the change and (2) this analysis proved the system's correctness with respect to some properties. Examples of these approaches are built on the assumption that the previous version of the program is verified and is correct and hence the task of reverifying the program after the change is either limited to the impacted parts \[[6](#S0065245817300487_3.xhtml#bb0035), [40](#S0065245817300487_3.xhtml#bb0205), [63](#S0065245817300487_3.xhtml#bb0320)\] or is reduced to an equivalence check between the impacted parts of both program versions \[[34](#S0065245817300487_3.xhtml#bb0175)–[39](#S0065245817300487_3.xhtml#bb0200)\] to conclude the correctness of the modified program version. Program refactoring is an example of an application that can benefit from equivalence checking approaches.

In \[[6](#S0065245817300487_3.xhtml#bb0035)\], an intraprocedural level analysis technique called DiSE (directed incremental symbolic execution) is proposed which uses static analysis and change impact analysis to determine the differences between program versions and the impact of these differences on other locations in the program, and uses this information to direct the symbolic execution to only explore these impacted locations. Analyzing the symbolic paths that characterize the behavior of impacted locations helps in discovering bugs and regression testing (test case selection and augmentation). Another important and practical application of this technique is presented in \[[64](#S0065245817300487_3.xhtml#bb0325)\] for monitoring safety-critical systems. Extending DiSE with interprocedural analysis capabilities is proposed in \[[63](#S0065245817300487_3.xhtml#bb0320)\]. A DiSE-based strategy is used in \[[40](#S0065245817300487_3.xhtml#bb0205)\] in the cases where code changes occur along with the update of properties. In such cases, only the impacted parts of the program are considered when analyzing the set of updated properties.

In order to reduce the overhead of performing a complete semantics equivalence check of two compared programs, the notion of uninterpreted functions is employed in \[[36](#S0065245817300487_3.xhtml#bb0185), [37](#S0065245817300487_3.xhtml#bb0190), [39](#S0065245817300487_3.xhtml#bb0200)\] to abstract the parts of the programs that are syntactically equivalent and have same inputs. In this case a semantics equivalence check is only applied between the corresponding parts that have not been abstracted. An obvious challenge in this technique is to determine which parts correspond to each other.

The notion of uninterpreted functions is also used in \[[38](#S0065245817300487_3.xhtml#bb0195)\] in place of common parts of two program versions which are then analyzed by an extended form of symbolic execution to generate a set of symbolic summaries of behavior that reflects the differences between the two program versions. Analyzing these summaries will reveal equivalency, partial equivalency and deltas in the two versions which can be used for refactoring assurance, change characterization and test suite evolution.

In \[[34](#S0065245817300487_3.xhtml#bb0175)\], a change impact analysis is applied to two related program versions to compute the sets of impacted statements in each version and the set of impacted symbolic summaries (constraints) resulting from the symbolic execution of each program version. Checking the equivalence of program versions depends on whether their impacted symbolic summaries are equivalent or not.

A partition-based regression verification is proposed in \[[65](#S0065245817300487_3.xhtml#bb0330)\] where the input space of two program versions is partitioned, using a form of symbolic execution in conjunction with random testing, into equivalence-revealing partitions (those that generate the same output in both versions) and difference-revealing partitions. Proving the absence of regression errors is carried out by checking the difference-revealing partitions.

The idea of reducing the equivalence checking of similar programs to a comparison of their deduced predicates summaries is presented in \[[35](#S0065245817300487_3.xhtml#bb0180)\]. Proving behavior equivalence of two programs is inferred from the level of coupling found between their predicates.

### 3.4 Incremental Analysis and Verification in Model-Based Development

In his statement paper “Evolution, Adaptation, and the Quest for Incrementality”, Ghezzi \[[66](#S0065245817300487_3.xhtml#bb0335)\] argues that supporting software evolution requires building incremental methods and tools to speed up the maintenance process with the focus on the analysis and the verification activities. An incremental approach in such contexts would try to characterize exactly what has been changed and reuse (as much as possible) the results of previous processing steps in the steps that must be rerun after the change. The motivation for this is twofold: time efficiency and scalability. Given the iterative development approach suggested by MDD, we believe that this vision needs to be employed by modern analysis and verification methods.

Surveying the literature for existing work on model-based incremental analysis and verification methods shows two categories of work: change-based incremental analysis and verification methods and compositional incremental analysis and verification methods.

Change-based incremental analysis or verification methods: We notice that the majority of existing work in this category focuses on incremental model-based test case generation and regression testing \[[67](#S0065245817300487_3.xhtml#bb0340)–[73](#S0065245817300487_3.xhtml#bb0370)\]. In \[[67](#S0065245817300487_3.xhtml#bb0340)\], a global state reduction technique based on dead and live variables has been used to construct and to incrementally update (upon a change), on-the-fly, the global reachable state space of communication protocols modeled as a set of extended communicating finite state machines (ECFSMs). The generated global state space is then used to verify the correctness of such systems. The idea of incremental test case generation is presented in \[[69](#S0065245817300487_3.xhtml#bb0350)\] for testing communication protocols modeled as FSMs. The goal is to test only the modified parts (i.e., transitions) of an evolving FSM specification. The experimental results provided showed significant gains, especially when the percentage of the modifications is not higher than 20% of the original specification. The same idea has also been explored in the context of software product lines \[[71](#S0065245817300487_3.xhtml#bb0360)\] using SAT-based analysis and UML-RT models \[[72](#S0065245817300487_3.xhtml#bb0365)\] using symbolic execution. In \[[71](#S0065245817300487_3.xhtml#bb0360)\], properties of features are defined as first-order logic formulas in Alloy which are then automatically mapped to a transformation that defines an incremental refinement of test suites. In \[[72](#S0065245817300487_3.xhtml#bb0365)\], SETs of the subject models (i.e., a model and its evolved versions) are manipulated to incrementally generate their test suites. Techniques for model-based regression test reduction and regression test generation of extended finite state machines (EFSMs) are presented in \[[68](#S0065245817300487_3.xhtml#bb0345), [70](#S0065245817300487_3.xhtml#bb0355)\] using an incremental manipulation of the control and data dependence graphs of these models.

The idea of incremental dependency graph adaptation and incremental slice computation is proposed in \[[74](#S0065245817300487_3.xhtml#bb0375)\] for software product lines based on the concept of delta modeling \[[75](#S0065245817300487_3.xhtml#bb0380)\] where a family of product variants are defined in terms of a core product and a set of deltas describing the changes to be made to the core product such that a product variant is obtained. In the same context, a framework for incremental regression-based testing is proposed in \[[73](#S0065245817300487_3.xhtml#bb0370)\] to efficiently test the selected product variants.

Incremental techniques for consistency checking of UML models are presented in \[[76](#S0065245817300487_3.xhtml#bb0385)\] using an automatic scope validation of consistency rules instantiation and in \[[77](#S0065245817300487_3.xhtml#bb0390)\] using a change impact analysis on the dependencies between model elements and inconsistency rules. Both approaches automatically detect the model changes that violate user-defined consistency rules during their validation.

Our research shares the same motivation as this category of existing work, however it differs in the analysis technique employed and type of models involved.

Compositional incremental analysis or verification methods: In contrast to the change-based incremental verification methods, compositionality-based incremental analysis or verification methods focus on optimizing the analysis or verification process of large systems using different strategies including assume-guarantee reasoning and compositional minimization (or compositional abstraction) \[[78](#S0065245817300487_3.xhtml#bb0395)\]. A key aspect of these strategies is to alleviate some of the scalability issues (e.g., state explosion problem) encountered when analyzing large systems. The main idea of the assume-guarantee reasoning strategy is to make use of the modular structure of the system by breaking down the verification process into subprocesses, each of which is concerned with the verification of one component. A global conclusion about the verification of the whole system should be incrementally derived from the verification of its components without the need to construct the global state space of the system. On the other hand, the compositional minimization or abstraction strategy depends on building a reduced version of the global state space of the system by composing a minimized or abstracted version of the local state space of the individual system components.

Examples of compositional reasoning approaches are presented in:

*   • \[[79](#S0065245817300487_3.xhtml#bb0400)\] for UML-RT models using domain-specific communication patterns and the RAVEN real-time model checker;
*   • \[[80](#S0065245817300487_3.xhtml#bb0405)\] for software product lines using an automata-based model checking algorithm;
*   • \[[81](#S0065245817300487_3.xhtml#bb0410)\] for component-based software systems based on an assume-guarantee model checker.

Examples of compositional minimization or abstraction approaches are presented in:

*   • \[[82](#S0065245817300487_3.xhtml#bb0415)\] for integration testing of component-based applications whose behavior is modeled as UML Statecharts using some heuristic reduction rules;
*   • \[[83](#S0065245817300487_3.xhtml#bb0420)\] for verifying systems of asynchronously communicating extended finite state machines (CEFSMs) using a partial product algorithm (or a partial composition technique);
*   • \[[84](#S0065245817300487_3.xhtml#bb0425)\] for verifying systems of distributed programs modeled as synchronously communicating FSMs using a hierarchy-based compositional minimization algorithm;
*   • \[[85](#S0065245817300487_3.xhtml#bb0430)\] for communicating state machines with infinite data space by clustering bisimilar states that have different data values into a finite set of equivalent classes and hence reducing the system state space;
*   • \[[86](#S0065245817300487_3.xhtml#bb0435), [87](#S0065245817300487_3.xhtml#bb0440)\] for communication protocols modeled by FSMs communicating through FIFO queues using symbolic reachability analysis and loop-first search analysis, respectively;
*   • \[[88](#S0065245817300487_3.xhtml#bb0445), [89](#S0065245817300487_3.xhtml#bb0450)\] for labeled transition systems (LTS) by leveraging precise information about the context and interface constraints for the different components in the system and hence eliminating the presence of possible unreachable states in the resulting compositional reachability analysis of the whole system;
*   • \[[90](#S0065245817300487_3.xhtml#bb0455)\] for communicating UML-RT state machines by computing the SETs of individual state machines and then composing them to construct a composite symbolic execution tree which can be used to run multiple system-level analyses.

Our research adopts the notion of abstraction presented above to construct an abstracted version of the global state space of the system to be analyzed using symbolic execution. This construction is performed on-the-fly for the whole system and not incrementally as in the work presented in this category.

### 3.5 Summary

In this section we have outlined the categories of research work that are relevant to our research. First, we have shown examples of approaches for the analysis and the verification of Statecharts-like models. Next, we have presented incremental analysis and verification techniques for evolving programs. Finally, we have reviewed some of the techniques that implement incremental analysis and verification of behavioral models.

Our work is inspired by the category of work presented in [Section 3.3](#S0065245817300487_1.xhtml#s0110) that is built specifically to improve the efficiency of symbolic execution when it is reapplied to an evolving version of a program, e.g., the work on incremental state-space exploration (ISSE) \[[51](#S0065245817300487_3.xhtml#bb0260)\], regression model checking \[[33](#S0065245817300487_3.xhtml#bb0170)\], memoized symbolic execution \[[7](#S0065245817300487_3.xhtml#bb0040)\], and directed incremental symbolic execution (DiSE) \[[6](#S0065245817300487_3.xhtml#bb0035)\]. In contrast to the work in \[[7](#S0065245817300487_3.xhtml#bb0040), [33](#S0065245817300487_3.xhtml#bb0170), [51](#S0065245817300487_3.xhtml#bb0260)\] which reuses previous model checking results and constraint solving proofs generated from analyzing a predecessor version of a Java program, we reuse SETs generated from analyzing a predecessor version of a Rhapsody Statechart. Also in contrast to the work in \[[6](#S0065245817300487_3.xhtml#bb0035)\] which performs an intraprocedural regression analysis of an evolved Java code, we perform a regression symbolic analysis of an evolved version of a Rhapsody Statechart.

 

## 4 Standard Symbolic Execution of Rhapsody Statecharts

In this section, we first explain how we build the SET of individual Rhapsody Statecharts. Then, we explain how we extend it to consider a model of communicating Statecharts. [Fig. 5](#S0065245817300487_1.xhtml#f0020) shows the architecture of an implementation of both techniques.

![Fig. 5 Standard symbolic execution (SE) of individual and communicating Rhapsody Statecharts.](images/S0065245817300487/f04-05-9780128151198.jpg)

Fig. 5 Standard symbolic execution (SE) of individual and communicating Rhapsody Statecharts.

### 4.1 Standard Symbolic Execution of Individual Rhapsody Statecharts

In [Section 3](#S0065245817300487_1.xhtml#s0095), we referred to some existing work that adopts the idea of symbolic execution of programs and transfers it to state-based models. We found the approach of Zurowska and Dingel \[[3](#S0065245817300487_3.xhtml#bb0020)\] is the most relevant to our work as it has been applied to a type of models, namely, UML-RT state machines, that shares many features with Rhapsody Statecharts. Therefore, we followed a similar procedure to build ours. The two core components of our standard symbolic execution technique of individual Rhapsody Statecharts are shown in [Fig. 5](#S0065245817300487_1.xhtml#f0020). The first component, “SC2MLM Transformation”, is a transformation that transforms an individual Statechart into our custom MLM representation. The second component, “KLEE-based MLM2SET Generation”, is a symbolic executor that traverses the MLM model and symbolically executes the action code encountered in each transition to build its symbolic state space. In contrast to the work in \[[3](#S0065245817300487_3.xhtml#bb0020)\], our intermediate machine representation of Rhapsody Statecharts takes the form of MLMs instead of their functional finite state machines (FFSMs). Additionally, our symbolic execution module is based on an off-the-shelf symbolic execution engine, KLEE \[[8](#S0065245817300487_3.xhtml#bb0045)\], to symbolically execute action code encountered in the Statecharts, whereas an in-house symbolic execution engine is used in \[[3](#S0065245817300487_3.xhtml#bb0020)\]. The reason for choosing the MLM formalism is to have actions associated only with transitions, and we do this in such a way that it preserves the behavior of Statecharts.

#### 4.1.1 Statecharts-to-Mealy-Like-Machines Transformation: SC2MLM

We first define our custom MLM formalism that is used to represent a semantically equivalent flattened version of a Rhapsody Statechart. The basic structure of an MLM consists of a set of global variables (sometimes called attributes), a set of simple states with one of them marked as an initial state, and a set of transitions between these states. Simple states in MLMs do not have entry or exit actions. Transitions are characterized in the same way as in Rhapsody Statecharts by the event that triggered them, an optional guard and an action that occurs upon firing them. More advanced features that are found in Rhapsody Statecharts such as composite states, concurrent states, states with entry, and exit actions and choice points (also called condition connectors or OR-connectors, which allow a transition to branch depending on the value of a guard) need to be mapped to fit the structure of MLMs. Our current transformation supports the mapping of these specific features. For example:

*   – Composite and concurrent states and their outgoing group transitions (formally called group transitions or high-level transitions) are flattened into simple ones;
*   – Choice points along with their incoming and outgoing branches are replaced by newly created transitions connecting the source state of each choice point with its target states;
*   – Entry actions of each state are added at the end of the action code of all its incoming transitions; and
*   – Exit actions of each state are added at the beginning of the action code of all its outgoing transitions.

We followed the semantics of the Rhapsody Statecharts that is used by the code generator of the IBM Rational Rhapsody tool to develop our transformation. We performed exhaustive manual checking and inspection for the set of models that we used to validate the correctness of our transformation. Conducting a formal testing or verification study for this task is outside the scope of this research and it is subject for future work.

[Fig. 6](#S0065245817300487_1.xhtml#f0025) shows an example of a Rhapsody Statechart with the subset of features that we consider in this work and its MLM representation.

![Fig. 6 An example of a Rhapsody Statechart and its corresponding MLM representation. (A) An example of a Rhapsody Statechart as adapted from \[91\]. (B) The MLM representation of the Rhapsody Statechart in (A).](images/S0065245817300487/f04-06p1-9780128151198.jpg)

Fig. 6 An example of a Rhapsody Statechart and its corresponding MLM representation. (A) An example of a Rhapsody Statechart as adapted from \[[91](#S0065245817300487_3.xhtml#bb0460)\]. (B) The MLM representation of the Rhapsody Statechart in (A).

Definition 5

(Mealy-like machine)

Formally, an MLM is a tuple MLM=(S, V, E, EA, T, s[0], V[0]), where: 

*   • S is a nonempty finite set of states;
*   • V is a set of typed global variables (these are the attributes of the class of objects whose behavior is modeled by the MLM);
*   • E is a nonempty finite set of events (also called triggers or signals) by which the machine communicates with its environment; they are divided into disjoint sets of input events E^(inp), output events E^(out), and internal events E^(int), and can optionally have arguments (also called parameters), EA;
*   • EA is a finite set of event arguments that is disjoint with V;
*   • T is a set of transitions connecting the states in S. A transition is a tuple t=(s, e, eA, G, A, s′, DD), where:  
    *   • s and s’ are the source state and the target state, respectively;
    *   • e is an input or internal event in E^(inp) or E^(int);
    *   • eA is a subset of EA representing the arguments of e;
    *   • G is a Boolean expression (condition) defined over a subset of `V` `∪` `e``A`![si13\_e](images/S0065245817300487/si13_e.png) and is called the guard of t;
    *   • A is a fragment of action code written in C, C++, or Java and is called the action of t; statements in this fragment can be assignment expressions, conditional statements, iterations or a special type of statement used to generate some output events to be sent to the environment; the execution of this fragment may result in updating the values of a subset of V, constraining some of the variables in V, or the parameters in eA, or it may cause a sequence of output events in E^(out) to be sent;
    *   • DD is a subset of the transitions in T that have a data dependency with t with respect to the variables in V (the initialization of this variable occurs as a result of computing the data dependency between the transitions in T);
*   • s[0] ∈ S is the initial state.
*   • V[0] is an initial valuation (or initialization) of the variables in V.

Example 1

For the example of the MLM model presented in [Fig. 6B](#S0065245817300487_1.xhtml#f0025), we can identify the following:

*   – S = {S0, S1\_S0, S1\_S1, S1\_S2, S1\_S3};
*   – V = {a, b, c};
*   – E^(inp) = {setTriangleSides(x, y, z), checkPositiveSides(), checkIsTri- angle(), checkTriangleType(), reset()};
*   – E^(out) = {evStartChecking(), evValidInput(), evInvalidInput(), evIsTri- angle(), evIsNotTriangle(), evEquilateral(), evScalene(), evIsoscel- es()};
*   – E^(int) = ∅;
*   – EA = {x, y, z};
*   – s[0] \= S0;
*   – V[0] \= {a=0, b=0, c=0};
*   – T1 = (S0, setTriangleSides, {x, y, z}, ∅, {itsOutput.gen(new evSta- rtChecking()); a=params.x; b=params.y; c=params.z;}, S1\_S0, ∅);
*   – T2 = (S1\_S0, checkPositiveSides, ∅, {(x>0)&&(b>0)&&(c>0)}, {itsOut- put.gen(new evValidOutput());}, S1\_S1, {T1});
*   – …
*   – T10 = (S1\_S3, reset, ∅, ∅, {a=0;b=0;c=0;}, S0, ∅).

#### 4.1.2 Symbolic Execution of MLM:MLM2SET

The main idea is the same as for the symbolic execution of programs with some variations that reflect the different features of MLMs. For instance, states in MLMs are similar to program locations (i.e., program counters), transitions in MLMs are similar to program statements, and event arguments in MLMs are similar to program arguments (which both represent the input data passed from the environment). Just as symbolic execution of programs replaces the concrete values of all input variables to a program by symbolic values, so too will symbolic execution of MLMs replace the concrete values of all event arguments received by a MLM by a unique set of symbolic values. Consequently, both symbolic execution techniques are able to symbolically trace the given artifact (either a program or an MLM) and compute the constraints and the variable updates associated with each execution path. In this case, both constraints and variable updates are defined over symbolic values. The output from symbolic execution is represented by a symbolic execution tree (SET). The nodes in this tree represent program locations (or MLM states) with the symbolic valuations of program variables (or MLM variables) at these locations and the path constraints collected to reach these locations; therefore, we call them symbolic. The edges in this tree are links between symbolic locations, and they reflect the control flow of the execution. For the symbolic execution of programs, these edges usually have no labels; however, in the symbolic execution of MLMs they are labeled with the event causing the transition (with the symbolic values substituting their arguments if any) and also the sequence of events resulting from the execution of the transition action code (along with their arguments, if any). We call these edges symbolic transitions.^([b](#S0065245817300487_3.xhtml#fn0015)) The root of the tree is the node representing the initial state of the MLM with the MLM variables set to their initial values and the path constraint set to “true” or empty.

Definition 6

(Symbolic Execution Tree)

Formally, a SET of an MLM, MLM=(S, V, E, EA, T, s[0], V[0]), is a tuple SET=(SS, L, ST, ss[0]) where:

*   • SS is a finite set of symbolic states; a symbolic state is a tuple ss = (s, val, pc) where,  
    *   • s is a state in S;
    *   • val is the symbolic valuation of machine variables V;
    *   • pc is the path constraint collected to reach state s.
*   • L is a finite set of labels; a label is a tuple l=(e, V^s, σ, out) where,  
    *   • e is an input or internal event in E^(inp) or E^(int);
    *   • V^s is a set of symbolic variables, different from V and EA;
    *   • σ is a mapping from the original event argument names `e``A` `⊂` `E``A`![si14\_e](images/S0065245817300487/si14_e.png) to the new set of variables names in V^s;
    *   • out is a sequence of some output events `e`[`1`]^(`o``u``t`)`,` `e`[`2`]^(`o``u``t`)`,` `…``,` `e`[`n`]^(`o``u``t`)![si15\_e](images/S0065245817300487/si15_e.png) in E^(out) and the symbolic valuations of their arguments `e`[`1`]^(`o``u``t`)`A``,` `e`[`2`]^(`o``u``t`)`A``,` `…``,` `e`[`n`]^(`o``u``t`)`A`![si16\_e](images/S0065245817300487/si16_e.png) in EA (if any).
*   • ST is a finite set of symbolic transitions defining the transition relation between symbolic states; a symbolic transition is a tuple st = (ss, l, ss’) where,  
    *   • ss is the source symbolic state;
    *   • l is the label of the symbolic transition;
    *   • ss’ is the target symbolic state.
*   • ss[0] is the initial symbolic state.

In the remainder of this section, we provide the details of our algorithm to symbolically execute MLMs as listed in [Algorithm 5](#S0065245817300487_1.xhtml#b0030).

Algorithm 5

Symbolic Execution (SE) of MLMs

Input:

1: An MLM MLM = (S, V, E, EA, T, s[0], V[0])

Output:

1: A SET SET = (SS, L, ST, ss[0])

Steps:

1: ss[0] ← (s[0], v[0], true)

2: SS ← {ss[0]}

3: Create a queue q

4: q ← \[ss[0]\]

5: //Explore the MLM in Breadth-First-Search fashion

6: while q is not empty do

7:     Remove the first element ss = (s, val, pc) from q

8:     for all outgoing transitions t = (s, e, eA, G, A, s’) of s do

9:         Create a unique set V^s of new variables in one-to-one relation with the transition's event arguments eA

10:         Create a map σ between eA and V^s

11:         Substitute every occurrence of a variable x ∈ eA in the guard G and the action code A by σ(x) to obtain G^s ← σ(G) and A^s ← σ(A)

12:         if G^s is satisfiable given val and pc then

13:             feasiblePaths ← SymbolicExecutionOfCode(A^s, val, G^s, pc)

14:             for all feasiblePath = (val’, pc’, out’) ∈ feasiblePaths do

15:                 Create a new symbolic state, ss’ = (s’, val’, pc’)

16:                 if ss’ is not subsumed by any previously generated symbolic state in SS then

17:                     SS ← SS ∪ {ss’}

18:                     Create a new label, l’ = (e, V^s, σ, out’)

19:                     L ← L ∪ {l’}

20:                     Create a new symbolic transition, st’ = (ss, l’, ss’)

21:                     ST ← ST ∪ {st’}

22:                     q ← enqueue(q, ss’)

23:                 end if

24:             end for

25:         end if

26:     end for

27: end while

 

The first task in this algorithm concerns the exploration of the MLM, which is done in a breadth-first-search fashion,^([c](#S0065245817300487_3.xhtml#fn0020)) starting from the initial state and proceeding through each of its outgoing transitions, and so on, until all states have been visited. Since some MLMs may have loops, we need to limit the exploration by some criterion. The criterion that we consider here is to check if a symbolic state is subsumed by some other previously explored symbolic state; if so, we should not explore it again.

Definition 7

(Symbolic states subsumption \[[92](#S0065245817300487_3.xhtml#bb0465)\])

Formally, a symbolic state ss = (s, val, pc) is subsumed by another symbolic state ss’ = (s’, val’, pc’) iff:

1.  (1) s = s’;
2.  (2) val = val’;
3.  (3) pc is included in pc’ (i.e., `p``c``⇒``p``c`^(`′`)![si17\_e](images/S0065245817300487/si17_e.png) or pc is at least as constraining as pc’).

The second task is the symbolic execution of transitions. In this task, we perform the following steps for each transition: (1) we create and assign a unique set of symbolic variables to replace the event arguments of the transition, if any (Lines 9–10); (2) we substitute the occurrences of these event arguments in the guard expression and the action code statements by their assigned symbolic values (Line 11); (3) we check if the guard is satisfiable with respect to the variable updates and the path constraint of the current symbolic state (Line 12); if so, (4) we use symbolic execution of programs to execute the updated action code of the transition; the result from the symbolic execution engine^([d](#S0065245817300487_3.xhtml#fn0025)) is a set of variable valuation and path constraints that trigger different feasible paths in that code (Line 13); (5) We use the results from the previous step to both create a new set of symbolic states representing the target state of this transition and also to label the edges to these new symbolic states (Lines 15–19).

Example 2

The complete SET of the MLM in [Fig. 6B](#S0065245817300487_1.xhtml#f0025) is shown in [Fig. 7](#S0065245817300487_1.xhtml#f0030). As we notice, the SET has depth 6, and it has 14 symbolic execution paths identified by the leaves in the tree. In the following, we show the detailed steps for generating the first three levels of the tree, based on [Algorithm 5](#S0065245817300487_1.xhtml#b0030).

![Fig. 7 SET of the MLM model in Fig. 6B (highlighted Levels: 1, 2, and 3).](images/S0065245817300487/f04-07-9780128151198.jpg)

Fig. 7 SET of the MLM model in [Fig. 6B](#S0065245817300487_1.xhtml#f0025) (highlighted Levels: 1, 2, and 3).

As it is shown, the root of the tree is the symbolic state SS1 = (S0, (a=0, b=0, c=0), \[\]). Exploring state S0 of SS1 will symbolically execute its outgoing transition T1, which creates new symbolic values X, Y, and Z, assigns them to the arguments x, y, and z of the event setTriangleSides, updates the machine variables a, b, and c to have the new symbolic values of the setTriangleSides event arguments, creates a new symbolic state SS2 = (S1\_S0, (a=X, b=Y, c=Z), \[\]), and finally forms the label for the symbolic transition (i.e., the edge) connecting SS1 and SS2 with the transition event e = \[setTriangleSides(X, Y, Z)\] and the output out = \[itsOutput.evStart- Checking()\]. Because there is no guard associated with the transition T1 and there are no conditional statements in its action code, there is no update to be made to the path constraint of the symbolic state SS2. The next step is exploring state S0\_S1 of SS2 which will symbolically execute its outgoing transitions, T2, T3, and T4, in sequence. Symbolically executing T2 creates a new symbolic state SS3 = (S1\_S1, (a=X, b=Y, c=Z), \[!(X<=0)&&!(Y<=0)&&!(Z<=0)\]) and forms the label for the edge between SS2 and SS3with the transition event e = \[checkPositiveSides()\] and the output out = \[itsOutput.evValidInput()\]. As we notice, the value of the path constraint of SS3 reflects the guard condition of transition T2. In contrast with T2, symbolically executing T3 creates three symbolic states representing state S1\_S2, which are SS4, SS5, and SS6. All have the same variable valuations val = (a=X, b=Y, c=Z) but have different path constraints representing all feasible cases for the guard condition of T3. The edges connecting SS3 with SS4, SS5, and SS6 are all labeled with the input event e = \[checkPositiveSide()\] and the output out = \[itsOutput.evInvalidInput()\]. Finally, symbolically executing T4 creates a new symbolic state SS7 = (S0, (a=0, b=0, c=0), \[\]) and forms the label for the edge between symbolic state SS2 and symbolic state SS7 with the transition input event e = \[reset()\] and the output out = \[\]. The difference between the symbolic state SS7 and the other symbolic states SS4, SS5, and SS6 is that we find that there is another symbolic state, SS1, that has already been explored before, and it subsumes SS7, therefore no further exploration is needed for SS7.

We can notice that the symbolic execution of a transition may result in zero, one or many symbolic edges depending on the satisfiability of the guard condition and action code of the transition. Therefore, we refer to transitions with more than one symbolic edge in the resulting SET as multipath transitions (e.g., transitions T3 and T4 are multipath transitions).

The resulting SET can be used to run many intralevel types of analyses (e.g., reachability analysis and guard analysis) to ensure the correctness of the individual objects in isolation of the others.

 

### 4.2 Symbolic Execution of a Model of Communicating Rhapsody Statecharts

In the previous subsection, we showed how to symbolically execute individual Statecharts. In this section we present how we extended our standard symbolic execution technique to consider a model of communicating Statecharts. The goal here is to facilitate the analysis of the overall behavior of the system and the interoperability between its communicating objects. Our approach is based on an on-the-fly exploration of all interleaving Statecharts in a given model to construct the global state space of the system represented by a more general SET called a global symbolic execution tree (GSET).

The two components of our standard symbolic execution technique of a model of communicating Statecharts are shown in [Fig. 5](#S0065245817300487_1.xhtml#f0020), which are the “RhapM2CMLM Transformation” and the “KLEE-based CMLM2GSET Generation”. Each component generalizes the functionality provided by its corresponding one for individual Statecharts. This generalization incorporates the extra features present in the communication setting. For instance, we need to access the OMDs of a Rhapsody model to identify the set of communicating objects in the model and to determine the communication topologies between these objects. This requires the extension of our previous MLM formalism to represent a collection of communicating MLMs and to represent their communication topologies. We also need to extend our previous SET definition to represent, instead, a global SET. In such global SETs, symbolic model states are used in place of simple symbolic states.

#### 4.2.1 Rhapsody Model of Communicating Statecharts-to-Communicating MLMs Transformation: RhapM2CMLM

The input to this component is a Rhapsody model represented by its OMDs and its Statecharts and the output is a Communicating MLMs representation. Our formalism for Communicating MLMs is shown below and it uses the MLM formalism presented in [Section 4.1.1](#S0065245817300487_1.xhtml#s0135) (please see [Definition 5](#S0065245817300487_1.xhtml#enun0030)). For illustration, we refer to the model example shown in [Section 2](#S0065245817300487_1.xhtml#s0030), [Fig. 1](#S0065245817300487_1.xhtml#f0130). For simplicity, we consider only simple states and simple transitions in the Statecharts used in this example, yet our implementation supports Statecharts with more complex features such as hierarchical states, orthogonal regions, choice points, and group transitions.

Definition 8

(Communicating MLMs)

Formally, a global model of n asynchronously communicating MLMs is a tuple M = (MLM^M, Q^M, s[0]^M, V^M, V[0]^M) where: 

*   • MLM^M\=(MLM[1], MLM[2], …, MLM[n]), where MLM[i]\=(S[i], V[i], E[i], EA[i], T[i], s[0i], V[0i]) is the i\-th MLM in M that is defined as follows:  
    *   • S[i] is a nonempty finite set of states and `S`[`1`] `∩` `S`[`2`] `∩` `…` `∩` `S`[`n`] `=` `⌀`![si18\_e](images/S0065245817300487/si18_e.png);
    *   • V[i] is a set of typed global variables (these are the attributes of the class of objects whose behavior is modeled by the MLM);
    *   • E[i] is a nonempty finite set of events (also called triggers or signals) by which the machine communicates with its environment. Events can have arguments EA[i] (also called parameters) and are partitioned into input events, `E`[`i`]^(`i``n``p`)![si19\_e](images/S0065245817300487/si19_e.png), output events, `E`[`i`]^(`o``u``t`)![si20\_e](images/S0065245817300487/si20_e.png), and internal events, `E`[`i`]^(`i``n``t`)![si21\_e](images/S0065245817300487/si21_e.png) and `E`[`1`]^(`i``n``p`) `∩` `E`[`2`]^(`i``n``p`) `∩` `…` `∩` `E`[`n`]^(`i``n``p`)![si22\_e](images/S0065245817300487/si22_e.png)  `=` `E`[`1`]^(`o``u``t`) `∩` `E`[`2`]^(`o``u``t`) `∩` `…` `∩` `E`[`n`]^(`o``u``t`) `=` `E`[`1`]^(`i``n``t`) `∩` `E`[`2`]^(`i``n``t`) `∩` `…` `∩` `E`[`n`]^(`i``n``t`) `=` `⌀`![si23\_e](images/S0065245817300487/si23_e.png);
    *   • EA[i] is a finite set of event arguments that is disjoint with V[i] and `E``A`[`1`] `∩` `E``A`[`2`] `∩` `…` `∩` `E``A`[`n`] `=` `⌀`![si24\_e](images/S0065245817300487/si24_e.png);
    *   • T[i] is a set of transitions connecting the states in S[i]. A transition is a tuple t = (s, e, eA, G, A, s′, DD, COMD), where:  
        *   – s and s’ are the source state and the target state, respectively;
        *   – e is one of the input or internal events in E[i]^(inp) and E[i]^(int);
        *   – eA is a subset of EA[i] representing the arguments of e;
        *   – G is a Boolean expression (condition) defined over a subset of `V`[`i`] `∪` `e``A`![si25\_e](images/S0065245817300487/si25_e.png) and is called the guard of t;
        *   – A is a fragment of action code written in C, C++, or Java and it is called the action of t; statements in this fragment can be assignment expressions, conditional statements, iterations, or a special type of statements used to generate some output events to be sent to the environment; the execution of this fragment may result in updating the values of a subset of V[i], constraining some of the variables in V[i], or the parameters in eA, or it may cause a sequence of output events in E[i]^(out) to be sent;
        *   – DD is a subset of the transitions in T[i] that have a data dependency with t with respect to the variables in V[i];
        *   – COMD is a subset of the transitions in T[j] of MLM[j] ∈ M, where j = 1, …, n and j≠i that have a communication dependency with t.
    *   • s[0i]∈S[i] is the initial state.
    *   • V[0i] is an initial valuation (or initialization) of the variables in V[i].
*   • Q^M\=(q[1], q[2], …, q[n]) is the set of communication queues in M (these queues allow the exchange of messages between MLMs);
*   • `s`[`0`]^(`M`) `=` `(``s`[`01`]`,` `s`[`02`]`,` `…``,` `s`[`0``n`]`)`![si26\_e](images/S0065245817300487/si26_e.png), where s[0i] is the initial state for MLM[i];
*   • `V`^(`M`) `=` `V`[`1`] `∪` `V`[`2`] `∪` `…` `∪` `V`[`n`]![si27\_e](images/S0065245817300487/si27_e.png), where V[i] is the set of variables in MLM[i] and `V`[`1`] `∩` `V`[`2`] `∩` `…` `∩` `V`[`n`]![si28\_e](images/S0065245817300487/si28_e.png)\=∅;
*   • `V`[`0`]^(`M`) `=` `V`[`01`] `∪` `V`[`02`] `∪` `…` `∪` `V`[`0``n`]![si29\_e](images/S0065245817300487/si29_e.png), where V[0i] is the initial valuation of the variables V[i] in MLM[i].

Example 3

Based on this formalism, we can represent the Rhapsody model shown in [Section 2](#S0065245817300487_1.xhtml#s0030), [Fig. 1](#S0065245817300487_1.xhtml#f0130) as the following CMLM:

M^(AB)\=((MLM[itsA], MLM[itsB]), (q[itsA], q[itsB]), (aS1, bS1), (x, y), (0, 5)) where:

*   • MLM[itsA]\=({aS1, aS2, aS3}, {x}, {e1, e2, e3}, {e1Arg1}, {itsA\_T1, itsA\_T2, itsA\_T3}, aS1, {0});  
    *   • itsA\_T1=(aS1, e1, e1Arg1, ∅, (if(params.e1Arg1>7){x=5;}else{x=1;}), aS2, ∅, ∅);
    *   • itsA\_T2=(aS2, e2, ∅, ∅, (itsB.gen(newe5(5));), aS3, ∅, ∅);
    *   • itsA\_T3=(aS3, e3, ∅, ∅, (x=0;), aS1, ∅, {itsB\_T3});
*   • MLM[itsB]\=({bS1, bS2}, {y}, {e4, e5, e6}, {e5Arg1}, {itsB\_T1, itsB\_T2, itsB\_T3}, bS1, {5});  
    *   • itsB\_T1=(bS1, e4, ∅, ∅, (y=y+1;), bS2, ∅, ∅);
    *   • itsB\_T2=(bS2, e5, e5Arg1, (params.e5Arg1==5), (itsA.gen(newe3());), bS1, {itsB\_T1}, ∅);
    *   • itsB\_T3=(bS2, e6, ∅, ∅, (y=y−1;), bS2, ∅, {itsA\_T2}).

Additionally, we can recognize that (1) events e1, e2, e4, and e6 are external events, while events e3 and e5 are internal events and (2) transition itsA\_T1 is a multipath transition due to the if-else conditional statement in the transition's action code.

#### 4.2.2 Symbolic Execution of Communicating MLMs:CMLM2GSET

The input to this component is a set of Communicating MLMs representing a Rhapsody model and the output is a GSET. The formal definition of a GSET extends our previous definition in [Section 1.1](#S0065245817300487_1.xhtml#s0015) for the SET of an individual MLM. It replaces the definition for the symbolic states in the tree to consider instead symbolic model states and it adds an extra element to represent the queues’ contents in a given model.

Definition 9

(Global SET)

Formally, a global SET of a model of n asynchronously communicating MLMs, `M` `=` `(``M``L``M`^(`M`)`,` `Q`^(`M`)`,` `s`[`0`]^(`M`)`,` `V`^(`M`)`,` `V`[`0`]^(`M`)`)`![si30\_e](images/S0065245817300487/si30_e.png) where MLM[i] = (S[i], V[i], E[i], EA[i], T[i], s[0i], V[0i]) is the i^(th) MLM in M, is a tuple GSET^M = (SS^M, L^M, ST, ss[0]^M) where: 

*   • SS^M is a finite set of symbolic model states; a symbolic model state is a tuple ss^M = (s^M, val, pc, q^M) where,  
    *   • s^M is a model state in S^M\=(s[1], s[2], …, s[n]) where s[i]∈S[i] of MLM[i];
    *   • val is the symbolic valuation of the model variables V^M;
    *   • pc is the path constraint collected to reach the model state s^M;
    *   • q^M is the content (or update) of the model queues Q^M;
*   • L is a finite set of labels; a label is a tuple l=(e, V^s, σ, out) where,  
    *   • e is an input or internal event in MLM[i] for some i=1, …, n;
    *   • V^s is a set of symbolic variables, different from V^M and EA[i](MLM[i]) for all i=1, …, n;
    *   • σ is a mapping from the original event argument names `e``A`[`i`] `⊂` `E``A`[`i`]`(``M``L``M`[`i`]`)`![si31\_e](images/S0065245817300487/si31_e.png) for all i=1, …, n to the new set of variables names in V^s;
    *   • out is a sequence of some output events `e`[`1`]^(`o``u``t`)`,` `e`[`2`]^(`o``u``t`)`,` `…``,` `e`[`n`]^(`o``u``t`)![si15\_e](images/S0065245817300487/si15_e.png) in `E`[`i`]^(`o`)![si33\_e](images/S0065245817300487/si33_e.png) and the symbolic valuations of their arguments `e`[`1`]^(`o``u``t`)`A``,` `e`[`2`]^(`o``u``t`)`A``,` `…``,` `e`[`n`]^(`o``u``t`)`A`![si16\_e](images/S0065245817300487/si16_e.png) in EA[i](MLM[i]) (if any).
*   • ST is a finite set of symbolic transitions defining the transition relation between symbolic states; a symbolic transition is a tuple st=(ss^M, l, ss′^M) where:  
    *   • ss^M is the source symbolic model state;
    *   • l is the label of the symbolic transition;
    *   • ss′^M is the target symbolic model state.
*   • `s``s`[`0`]^(`M`)![si35\_e](images/S0065245817300487/si35_e.png) is the initial symbolic model state.

Now we explain the steps to symbolically execute a model of communicating MLMs as listed in [Algorithm 6](#S0065245817300487_1.xhtml#b0035).

Algorithm 6

Symbolic Execution (SE) of CMLMs

Input:

1: A system/model of n communicating MLMs M = (MLM^M,Q^M, *s*[0]^(*M*)![si37\_e](images/S0065245817300487/si37_e.png), V^M,*V*[0]^(*M*)![si38\_e](images/S0065245817300487/si38_e.png))

Output:

1: A Global SET GSET^M = (SS^M, L, ST, *s**s*[0]^(*M*)![si39\_e](images/S0065245817300487/si39_e.png))

Steps:

1: *s**s*[0]^(*M*)←(*s*[0]^(*M*), *V*[0]^(*M*), true, *q*[0]^(*M*))![si40\_e](images/S0065245817300487/si40_e.png)

2: SS^M ← {*s**s*[0]^(*M*)![si39\_e](images/S0065245817300487/si39_e.png)}

3: Create a queue q

4: q ← \[*s**s*[0]^(*M*)![si39\_e](images/S0065245817300487/si39_e.png)\]

5: //Breadth-First-Search fashion exploration for each MLM in M

6: while q is not empty do

7:     Remove the first element ss^M = (s^M, val, pc, q^M) from q

8:     for all MLM[i] in MLM^M do

9:         *s*[*i*]←*s*^(*M*)(*i*)![si43\_e](images/S0065245817300487/si43_e.png) where s[i] ∈ S[i](MLM[i])

10:         for all outgoing transitions t[i] = (s[i], e, eA, G, A, s[i])’ of s[i] do

11:             if `(``(``q`^(`M`) `=` `ϕ``)` `∧` `(``e` `∈` `E`[`i`]^(`i``n``p`)`)``)` `∨` `(``(`head`(``q`[`i`]^(`M`)`)` `=` `e``)` `∧` `(``e` `∈` `E`[`i`]^(`i``n``t`)`)``)`![si44\_e](images/S0065245817300487/si44_e.png) then

12:                 Create a unique set V^s of new variables in one-to-one relation with the transition's event arguments eA

13:                 Create a map σ between eA and V^s

14:                 Substitute every occurrence of a variable x ∈ eA in the guard G and the action code A by σ(x) to obtain G^s ← σ(G) and A^s ← σ(A)

15:                 if G^s is satisfiable given val and pc then

16:                     feasiblePaths ← SymbolicExecutionOfCode(A^s, val, G^s, pc)

17:                     for all feasiblePath = (val’, pc’, out’) ∈ feasiblePaths do

18:                         q’^M ← out’

19:                         Create a new symbolic state, ss’^M = (s’^M, val’, pc’, q’^M) where s’^M = s^M.replace(s[i], s[i]’)

20:                         if ss’^M is not subsumed by any previously generated symbolic model state in SS^M then

21:                             SS^M ← SS^M ∪ {ss’^M}

22:                             Create a new label, l’ = (e, V^s, σ, out’)

23:                             L ← L ∪ {l’}

24:                             Create a new symbolic transition, st’ = (ss^M, l’, ss’^M)

25:                             ST ← ST ∪ {st’}

26:                             q ← enqueue(q, ss’^M)

27:                         end if

28:                     end for

29:                 end if

30:             end if

31:         end for

32:     end for

33: end while

The first step in this algorithm is an on-the-fly breadth-first-search exploration for each MLM in the model M concurrently, starting from the initial model state and proceeding through the outgoing transitions of the initial state in each MLM, and so on, until all model states have been visited or until we reach a certain depth limit in case of unbounded loops. Checking if a symbolic model state has been visited is done using the subsumption criterion definition listed below that extends [Definition 7](#S0065245817300487_1.xhtml#enun0045) to consider the queues’ contents of symbolic model states.

Definition 10

(Symbolic Model States Subsumption \[[92](#S0065245817300487_3.xhtml#bb0465)\])

Formally, a symbolic model state ss^M \= (s^M, val, pc, q^M) is subsumed by another symbolic mode state ss′^M \= (s′^M, val′, pc′, q′^M) iff:

1.  (1) s^M \= s′^M;
2.  (2) val = val′;
3.  (3) q^M \= q′^M;
4.  (4) pc is included in pc’ (i.e., `p``c``⇒``p``c`^(`′`)![si17\_e](images/S0065245817300487/si17_e.png) or pc is more constrained than pc’).

Symbolic model states that are marked “visited” do not require further exploration and therefore they form the leaves in a GSET. In [Fig. 8](#S0065245817300487_1.xhtml#f0035), we identified the subsumed nodes for all the leaves of the GSET(AB^(V0)). For example, symbolic model state SS21, which is a leaf node in the GSET(AB^(V0)), is subsumed by symbolic model state SS11, which is a nonleaf node in the GSET(AB^(V0)).

![Fig. 8 GSET(ABV0)—global symbolic execution tree for the example model ABV0 in Fig. 1.](images/S0065245817300487/f04-08-9780128151198.jpg)

Fig. 8 GSET(AB^(V0))—global symbolic execution tree for the example model AB^(V0) in [Fig. 1](#S0065245817300487_1.xhtml#f0130).

A common problem when building the global state space of asynchronous systems are unbounded queues which are continuously filled with messages (sent either from the environment or from the peers in the system) that cannot be consumed at the same rate. In this case the exploration will exhibit an infinite state behavior and will not end. Possible solutions for this problem are addressed in \[[93](#S0065245817300487_3.xhtml#bb0470)\] using bounded queues or assuming a “slow” environment in which external events (i.e., events that are sent by the environment to the system) are offered only when the system reaches a stable state (i.e., when the execution of all internal events are completed and all system queues have become empty). In such an environment, a higher priority is given to internal events over external ones.

In our approach, we adopt the “slow” environment assumption used in \[[93](#S0065245817300487_3.xhtml#bb0470)\] by allowing the execution of transitions with external events only if the system is in a stable state.

The second step is the symbolic execution of transitions which is done using the open-source symbolic execution engine KLEE \[[8](#S0065245817300487_3.xhtml#bb0045)\]. For each such transition that has an external event or an available internal event (i.e., the event exists in the head of the queue of the MLM to which the transition belongs to) (Line 11) we do the following:

1.  (1) we create and assign a unique set of symbolic variables to replace the event arguments of the transition, if any (Lines 12–13);
2.  (2) we substitute the occurrences of these event arguments in the guard expression and the action code statements, by their assigned symbolic values (Line 14);
3.  (3) we check if the guard is satisfiable with respect to the variable updates and the path constraint of the current symbolic state (Line 15); if so,
4.  (4) we use the symbolic execution engine KLEE \[[8](#S0065245817300487_3.xhtml#bb0045)\] to execute the updated action code of the transition; the results are a set of variable assignments and path constraints that trigger different feasible paths in that code (Line 13);
5.  (5) we use the results from the previous step to both create a new set of symbolic model states representing the target state of this transition and also to label the edges to these new symbolic model states (Lines 17–28).

Example 4

Applying this algorithm on the example model in [Fig. 1](#S0065245817300487_1.xhtml#f0130) results in the GSET shown in [Fig. 8](#S0065245817300487_1.xhtml#f0035) which consists of 25 symbolic model states and 9 symbolic execution paths given by the number of leaves in the tree.

### 4.3 Summary

In this section, we have shown examples of individual and communicating Rhapsody Statecharts. We have presented the formalisms we use to represent a semantically equivalent flattened version of Rhapsody Statecharts and a model of communicating Rhapsody Statecharts such that we can symbolically execute them. The proposed formalisms are called MLMs and Communicating MLMs (CMLMs). We also have provided the formal definitions for the structures of the SET and the GSET resulting from each symbolic execution technique.

## 5 Optimizing Symbolic Execution of Evolving Rhapsody Statecharts

In this section, we first illustrate with a running example the optimization ideas employed in this research for the symbolic execution of evolving Statecharts. Next, we provide the details of our two proposed techniques, namely, memoization-based symbolic execution (MSE) and dependency-based symbolic execution (DSE), for both individual and communicating Statecharts.

### 5.1 Motivating Example

In this section we explain using a running example the optimization ideas employed in the next section. For illustration, we use the models in [Fig. 9](#S0065245817300487_1.xhtml#f0040) and their symbolic execution trees (SETs) as shown in [Figs. 10](#S0065245817300487_1.xhtml#f0045) and [11](#S0065245817300487_1.xhtml#f0050) to show how our optimization techniques work for evolving individual Statecharts.

![Fig. 9 Two versions of an example Statechart. (A) V0—the base version of an example Statechart. (B) V1—a modified version of the Statechart in (A).](images/S0065245817300487/f04-09-9780128151198.jpg)

Fig. 9 Two versions of an example Statechart. (A) V0—the base version of an example Statechart. (B) V1—a modified version of the Statechart in (A).

![Fig. 10 SET(V0)—symbolic execution tree for the Statechart in Fig. 9A.](images/S0065245817300487/f04-10-9780128151198.jpg)

Fig. 10 SET(V0)—symbolic execution tree for the Statechart in [Fig. 9A](#S0065245817300487_1.xhtml#f0040).

![Fig. 11 SET(V1)—symbolic execution tree for the Statechart in Fig. 9B. (A) The parts that are different from SET(V0) are highlighted (in red). (B) The pruned parts resulting from the partial exploration of transitions: T1, T3, and T4 are grayed out.](images/S0065245817300487/f04-11p1-9780128151198.jpg)

Fig. 11 SET(V1)—symbolic execution tree for the Statechart in [Fig. 9B](#S0065245817300487_1.xhtml#f0040). (A) The parts that are different from SET(V0) are highlighted (in red). (B) The pruned parts resulting from the partial exploration of transitions: T1, T3, and T4 are grayed out.

In [Fig. 9](#S0065245817300487_1.xhtml#f0040), we have two versions of an example of individual Rhapsody Statechart: V0 (in [Fig. 9A](#S0065245817300487_1.xhtml#f0040)) is the base version and V1 (in [Fig. 9B](#S0065245817300487_1.xhtml#f0040)) is a modified version of the base version where we modified the conditional statement in the action code of transition T2. In [Fig. 10](#S0065245817300487_1.xhtml#f0045), we show the SET of V0, SET(V0), however, in [Fig. 11A and B](#S0065245817300487_1.xhtml#f0050), we show two different illustrations for the symbolic execution tree of V1, SET(V1).

Alternatively, we can use the model version AB^(V1) shown in [Fig. 12](#S0065245817300487_1.xhtml#f0055) and the GSETs in [Figs. 13](#S0065245817300487_1.xhtml#f0060) and [14](#S0065245817300487_1.xhtml#f0065) to illustrate how the same concepts are applied for evolving communicating Statecharts. The model version AB^(V1) is the successive version of the model example AB^(V0) shown in [Fig. 1](#S0065245817300487_1.xhtml#f0130) with a change in transition itsA\_T2 of the Statechart of object itsA.

![Fig. 12 A modified model version ABV1 and its dependency graph. (A) ABV1—a successive version of the example model ABV0 in Fig. 1. (B) Dependency graph of the model version ABV1.](images/S0065245817300487/f04-12-9780128151198.jpg)

Fig. 12 A modified model version AB^(V1) and its dependency graph. (A) AB^(V1)—a successive version of the example model AB^(V0) in [Fig. 1](#S0065245817300487_1.xhtml#f0130). (B) Dependency graph of the model version AB^(V1).

![Fig. 13 MGSET(ABV1)—the parts that are different from GSET(ABV0) in Fig. 8 are highlighted (in red).](images/S0065245817300487/f04-13-9780128151198.jpg)

Fig. 13 MGSET(AB^(V1))—the parts that are different from GSET(AB^(V0)) in [Fig. 8](#S0065245817300487_1.xhtml#f0035) are highlighted (in red).

![Fig. 14 DGSET(ABV1)—the pruned parts resulting from the partial exploration of transition itsA\_T1 are grayed out.](images/S0065245817300487/f04-14-9780128151198.jpg)

Fig. 14 DGSET(AB^(V1))—the pruned parts resulting from the partial exploration of transition itsA\_T1 are grayed out.

#### 5.1.1 Optimization Via Reuse—An Artifact-Oriented Evolution Support Approach

By comparing the unhighlighted parts (colored black) of the symbolic execution tree of V1, SET(V1), in [Fig. 11A](#S0065245817300487_1.xhtml#f0050) with the SET of V0, SET(V0), in [Fig. 10](#S0065245817300487_1.xhtml#f0045), we notice that these parts are identical. However, by looking at the highlighted parts (colored red) of the SET(V1), we find that:

1.  (1) they are slightly different from their corresponding parts in the SET(V0);
2.  (2) they represent the symbolic execution of transition T2 (the changed transition in V1) and subsequent transitions; and
3.  (3) they reflect the parts of the SET(V0) that are impacted by the changes made on V1.

Therefore, if we already have the SET(V0) and we manage to identify the parts of it that need to be updated in order to account for the changes made on V1, then we can direct the symbolic execution of V1 to generate only the new updated parts to replace the old ones. The applicability and utility of running this process depends, first, on the existence of the SET(V0) and, second, on the amount of savings gained from reusing it which can be very large for big complex models that undergo some minor changes (i.e., changes with limited impact). Possible measures for quantifying the amount of savings are (1) the time gained from not generating the SET(V1) from scratch; (2) the percentage of nodes (or symbolic states) in the SET(V0) that can be safely reused; or (3) the percentage of execution paths in the SET(V0) that can be safely reused. A very important benefit from this latter measure is that it provides us with a good estimate of how many of the test cases generated from the SET(V0), to test V0, can be reused for testing V1. We notice that the location of the change in the model may suggest the effectiveness of reusing the SET(V0). We believe that, in general, the closer the change is to the initial state of the model, the smaller the number of nodes in the SET(S0) that can be reused. Additionally, the more model paths go through a changed state or transition, the more updates of the SET(V0) are needed and the smaller the effectiveness of reusing SET(V0). For example, having a change in state S1 or transition T1 in V1 will require an update to all the descendants of the symbolic state SS2 in the SET(V0), leaving only two symbolic states to be reused.

#### 5.1.2 Optimization Via Reduction—An Analysis-Oriented Evolution Support Approach

First, we assume that the base version of a model (i.e., the version before the change) has already been analyzed successfully to, e.g., determine reachability of states or generate test cases. This assumption enables the optimization described below.

Second, as we discussed in [Section 4.1](#S0065245817300487_1.xhtml#s0130), the symbolic execution of a transition, t[i], in an MLM model may result in zero, one or many symbolic transitions of t[i] in the SET of that model, depending on: (1) the path constraints and the variable valuation of the symbolic state representing the source state of t[i]; (2) the satisfiability of the guard condition of t[i]; and (3) the number of execution paths of the action code of t[i]. For example, the symbolic execution of transition T1 in the two versions of the model in [Fig. 9](#S0065245817300487_1.xhtml#f0040) results in two symbolic transitions connecting the symbolic state SS2 of state S1 (the source state of T1), with the two symbolic states SS3 and SS4 of state S2 (the target state of T1). The first symbolic transition is taken if a=7, while the second takes place if a=1 (these are the two cases that satisfy the guard condition of T1). Similarly, the symbolic execution of T2 results in having two symbolic transitions originating from each of the symbolic states SS3 and SS4 and ending at the symbolic states SS5 and SS6 (resp., SS8 and SS9) as a result of having a conditional statement in the action code of T2. On the other hand, the symbolic execution of transition T3, which does not have a guard or any conditional statements in its action code, results in having only one symbolic transition originating from each of the symbolic states SS3 and SS4 and ending at the symbolic states SS7 and SS10, respectively. In the same way, the symbolic execution of transition T4 results in having one symbolic transition originating from each of the symbolic states SS5, SS6, SS8, and SS9 and ending at the symbolic states SS11, SS12, SS13, and SS14, respectively.

Third, as discussed in [Section 2.3](#S0065245817300487_1.xhtml#s0060), applying a dependency analysis on a modified version of a model given the list of the changes made on its previous version allows us to identify all the parts of the model that have an impact on or are impacted by the changes.

Now, with all that said, our question is can we direct the symbolic exploration of a modified version of a model to exhaustively explore all changed transitions and all other transitions that either impact or are impacted by one or more changed transitions and to reduce the exploration of the remaining transitions (i.e., the transitions that neither impact nor are impacted by the change) to a minimum (i.e., to consider only one symbolic transition per such transition)? Our goal is twofold: (1) to explore the minimal set of symbolic transitions to perform the analysis on the evolved state machine model (to, e.g., reveal states that have become unreachable by the change or to generate test cases for the new executions introduced by the change); and (2) to reduce the time of exploration as well as the size of the resulting SETs.

For example, applying a dependency analysis on V1 given that transition T2 has been changed with respect to its base version V0 shows that there is no dependency between T2 and any other transitions as none of them defines a variable that transition T2 uses (and vice versa). Now, with this information in mind, we can direct the symbolic execution of V1 to “fully” explore the changed transition T2 (i.e., to explore all its symbolic transitions) and to only “partially” explore the rest of the transitions in the model (i.e., to explore only one of its symbolic transitions). Following this process to symbolically execute V1 results in the SET shown in [Fig. 11B](#S0065245817300487_1.xhtml#f0050), which has six symbolic states less than the complete SET(V1). Although the new SET is not complete, it is sufficient to run regression types of analysis. For instance, the SET in [Fig. 11B](#S0065245817300487_1.xhtml#f0050) can be used to determine if the change introduced any unreachable states or which test cases must be run to test the execution paths introduced by the change.

As the amount of savings to be gained here depends on the number of symbolic transitions to be pruned from the partial exploration of unimpacted transitions, this technique is most beneficial if applied to Statecharts that have transitions with disjunct guards (i.e., “||”) or with action code that has conditional statements, which both result in more than one symbolic transition in the SET. The more symbolic transitions we have for an unimpacted transition, the more savings we gain if it is partially explored.

### 5.2 Proposed Symbolic Execution Optimizations for Evolving Rhapsody Statecharts

Symbolic execution is an expensive approach especially when applied to big and complex artifacts (programs or models) where the size of the generated SETs can be very large. Software artifacts can undergo several iterations and refinements and repeating the symbolic execution of these artifacts from scratch after every iteration or refinement step can be very tedious and time consuming. The new version of an artifact can be very similar to the previous one, so excluding the unchanged parts from successive runs of the symbolic execution technique reduces the time required for any symbolic execution-based types of analyses. Alternatively, directing the successive runs of the symbolic execution technique away from execution paths that are not impacted and toward execution paths that are impacted also reduces the time required for any symbolic execution-based types of analyses. Inspired by the work in \[[7](#S0065245817300487_3.xhtml#bb0040)\] and \[[6](#S0065245817300487_3.xhtml#bb0035)\] for optimizing the symbolic execution of evolving programs, we propose two techniques for optimizing the symbolic execution of evolving Rhapsody Statecharts. The two techniques are applied for both individual Statecharts and communicating Statecharts.

#### 5.2.1 Memoization-Based Symbolic Execution

In this section we present our MSE technique for both individual and communicating Statecharts. The architectures of implementations of the proposed approaches are shown in [Fig. 15A and B](#S0065245817300487_2.xhtml#f0070), respectively.

![Fig. 15 Memoization-based symbolic execution (MSE) proposed architecture. (A) MSE architecture for evolving individual Statecharts. (B) MSE architecture for evolving communicating Statecharts.](images/S0065245817300487/f04-15-9780128151198.jpg)

Fig. 15 Memoization-based symbolic execution (MSE) proposed architecture. (A) MSE architecture for evolving individual Statecharts. (B) MSE architecture for evolving communicating Statecharts.

##### 5.2.1.1 Technique Description

The basic idea of this technique is to reuse the results from a previous run of the symbolic execution technique on the model version before the change to optimize the next run of the technique on the model version after the change such that only the parts of the SET (resp., GSET) that are affected by the change will be regenerated. It is obvious that a key requirement for this technique is to have a stored version of the SET (resp., GSET) of the model before the change. Another requirement is to have a list of the changes made to the previous version of the model which will be used to remove the parts of the previous SET (resp., GSET) that are affected by the changes and to mark their corresponding source nodes (i.e., symbolic states or symbolic model states) as “needing an update”. Rerunning the SE technique on the modified model version will be directed to generate the required updates for these marked nodes.

To cope with the requirements of this technique, we needed to add to the definition of the symbolic state (resp., symbolic model state) presented earlier in [Section 4](#S0065245817300487_1.xhtml#s0125) as part of the definition of the symbolic execution tree (resp., GSET) the following two features: (1) a Boolean attribute needsUpdate that indicates whether a given symbolic state needs to be updated or not and (2) a hashmap `b``r``a``n``c``h``e``s``T``o``U``p``d``a``t``e``:``S``→`𝒫`(``T``)`![si45\_e](images/S0065245817300487/si45_e.png) of states with their corresponding outgoing transitions that need to be updated.

To be able to identify the nodes and the branches that need to be updated, we need to provide the technique with a list of all the differences between the modified mode version and its previous version. Our technique only considers a subset of model changes that can be mapped to changes to transitions in the MLM (resp., CMLMs) representation. This includes (1) adding states or transitions, (2) removing states or transitions, (3) modifying entry or exit actions of states, and (4) modifying events, guards, or actions of transitions. For example, adding or removing states can be represented by an addition or a deletion of transitions connecting these states with other states in the model; also, updating the entry actions (resp., exit actions) of states can be represented by an update of their incoming transitions (resp., outgoing transitions). Therefore, we manage to represent these differences in terms of a set of updated transitions T^(updated) including all transitions that have been added to, deleted from or updated in the modified version of the model. Other types of model changes such as the addition, deletion, or modification of variables (i.e., class attributes) are not supported since these changes impacts the variable valuation of every state in the model and hence requires a complete regeneration of the entire SET of the model after the change.

To find the differences between two Rhapsody models, we use the Rhapsody DiffMerge tool that we mentioned in [Section 2.4](#S0065245817300487_1.xhtml#s0080). These differences are mapped to their MLM (resp., CMLMs) correspondences using our “SC2MLM DiffMap” (resp., “RhapM2CMLM DiffMap”) component, which outputs the set of all transitions T^(updated) that are found to have been updated in the modified MLM (resp., CMLMs) version. Each element in the set T^(updated) indicates the name of a transition that has been affected by the change, the name of the source state of this transition, and the change type applied to this transition (i.e., “Addition”, “Deletion”, “Modification”).

The main component of our MSE technique for individual Statecharts is the “KLEE-based MLM2MSET Generation” component shown in [Fig. 15A](#S0065245817300487_2.xhtml#f0070). Similarly, the main component for communicating Statecharts is the “KLEE-based CMLM2MGSET Generation” component shown in [Fig. 15B](#S0065245817300487_2.xhtml#f0070). The detailed steps of implementing each component are listed in [Algorithms 7](#S0065245817300487_2.xhtml#b0040) and [8](#S0065245817300487_2.xhtml#b0045), respectively. In the sequel, we describe the details of both components.

Algorithm 7

Memoized-Based Symbolic Execution (MSE) of an Evolving MLM

Inputs:

1: A modified MLM model version: MLM^(modVer) = (S, V, E, EA, T, s[0], V[0])

2: A SET of the previous MLM model version MLM^(baseVer): SET^(baseVer) = (SS, L, ST, ss[0])

3: A set of all changed transitions between MLM^(modVer) and MLM^(baseVer): T^(updated)

Output:

1: A Memoized-based SET of MLM^(modVer): MSET^(modVer)

Steps:

1: //Task 1: Explore SET^(baseVer) in breadth-first-search fashion to remove the parts (i.e., the subtrees) that need to be updated and to mark the nodes in SET^(baseVer) to be reexplored when we rerun the standard SE on MLM^(modVer)

2: ss[0] ← (s[0], V[0], true)

3: Create a queue q

4: q ← \[ss[0]\]

5: while q is not empty do

6:     Remove the first element ss = (s, val, pc) from q

7:     if there is t in T^(updated) such that s = sourceState(t) and t is marked as “Added” then

8:         //Mark ss as “needsUpdate”

9:         ss.needsUpdate ← true

10:         //Add state s and its outgoing transition t to the hashmap branchesToUpdate of ss

11:         ss.branchesToUpdate ← ss.branchesToUpdate ∪ {s→![si46\_e](images/S0065245817300487/si46_e.png) {{t}}}

12:     end if

13:     for all outgoing symbolic transitions st = (ss, l, ss’) of ss do

14:         if there is t ∈ T^(updated) such that sourceState(t) = ss.s and targetState(t) = ss’.s then

15:             Assert t is marked as “Modified” or “Deleted”

16:             Remove l and ss’ with all its children from SET^(baseVer)

17:             if t is marked as “Modified” then

18:                 //Mark ss as “needsUpdate”

19:                 ss.needsUpdate ← true

20:                 //Add state s and its outgoing transition t to the hashmap branchesToUpdate of ss

21:                 ss.branchesToUpdate ← ss.branchesToUpdate ∪ {s→![si46\_e](images/S0065245817300487/si46_e.png) {{t}}}

22:             end if

23:         else

24:             q ← enqueue(q, ss’)

25:         end if

26:     end for

27: end while

28: //Task 2: Iterate over SET^(baseVer) and set the attributes needsUpdate and branchesToUpdate of all leaf symbolic states that are no longer subsumed by any of previsited nodes to “true” and “All”, respectively

29: SET^(baseVer) = Task2\_helperMethod(SET^(baseVer))

30: //Task 3: Reexplore SET^(baseVer) to merge the results from the standard symbolic execution of MLM^(modVer) for the parts that need to be updated

31: q ← \[ss[0]\]

32: //Create a set of previsited symbolic states for the purpose of subsumption checking

33: SS^(preVisited) ← {}

34: while q is not empty do

35:     Remove the first element ss = (s, val, pc) from q

36:     if ss has one or more outgoing symbolic transitions then

37:         //Record ss in the set of previsited symbolic states

38:         SS^(preVisited) ← SS^(preVisited) ∪ {ss}

39:         //Add all the target symbolic states of the outgoing symbolic transitions of ss to the queue

40:         for all outgoing symbolic transitions st = (ss, l, ss’) of ss do

41:             q ← enqueue(q, ss’)

42:         end for

43:     end if

44:     if ss.needsUpdate then

45:         //Rerun the SE on the model version MLM^(modVer) taking into consideration only transitions in ss.branchesToUpdate

46:         for all outgoing transitions t = (s, e, eA, G, A, s’) of s ∧ t ∈ ss.branchesToUpdate do

47:             Create a unique set V^s of new variables in one-to-one relation with the transition's event arguments eA

48:             Create a map σ between eA and V^s

49:             Substitute every occurrence of a variable x∈ eA in the guard G and the action code A by σ(x) to obtain G^s ← σ(G) and A^s ← σ(A)

50:             if G^s is satisfiable given val and pc then

51:                 feasiblePaths ← SymbolicExecutionOfCode(A^s, val, G^s, pc)

52:                 for all feasiblePath = (val’, pc’, out’)∈ feasiblePaths do

53:                     Create a new symbolic state, ss’ = (s’, val’, pc’)

54:                     if ss’ is not subsumed by any previously generated symbolic state in SS^(preVisited) then

55:                         ss′.needsUpdate ← true

56:                         ss′.branchesToUpdate ← “All”

57:                         SS ← SS ∪ {ss’}

58:                         Create a new label, l’ = (e, V^s, σ, out’)

59:                         L ← L ∪ {l’}

60:                         Create a new symbolic transition, st’ = (ss, l’, ss’)

61:                         ST ← ST ∪ {st’}

62:                         q ← enqueue(q, ss’)

63:                     end if

64:                 end for

65:             end if

66:         end for

67:     end if

68: end while

69: //Task 4 (Optional): Iterate over SET^(baseVer) and remove any node that can be subsumed by any other nodes (either at the same hierarchical level or higher)

70: SET^(modVer) = Task4\_helperMethod(SET^(baseVer))

71: *M**S**E**T*^(*m**o**d**V**e**r*)←*S**E**T*^(*b**a**s**e**V**e**r*)![si48\_e](images/S0065245817300487/si48_e.png)

Algorithm 8

Memoization-based Symbolic Execution (MSE) of an Evolving CMLM

Inputs:

1: A modified CMLM model version of n communicating MLMs: M2 = (*M**L**M*^(*M*2), *Q*^(*M*2), *s*[0]^(*M*2), *V*^(*M*2), *V*[0]^(*M*2)![si49\_e](images/S0065245817300487/si49_e.png))

2: A GSET of the previous CMLM model version M1: GSET^(M1)\=(SS^(M1), L, ST, *s**s*[0]^(*M*1)![si50\_e](images/S0065245817300487/si50_e.png))

3: A set of all changed transitions between M2 and M1: T^(updated)

Output:

1: A memoization-based GSET of M2: MGSET^(M2)

Steps:

1: //Task 1: Explore GSET^(M1) in breadth-first-search fashion to remove the parts (i.e., the subtrees) that need to be updated and to mark the nodes in GSET^(M1) to be reexplored when we rerun the standard SE on M2

2: *s**s*[0]^(*M*1)←(*s*[0]^(*M*1),*V*[0]^(*M*1),*t**r**u**e*,*q*[0]^(*M*1))![si51\_e](images/S0065245817300487/si51_e.png)

3: Create a queue q

4: *q*←\[*s**s*[0]^(*M*1)\]![si52\_e](images/S0065245817300487/si52_e.png)

5: while q is not empty do

6:     Remove the first element ss^(M1)\=(s^(M1), val, pc, q^(M1)) from q

7:     if there is s1 in s^(M1) and there t in T^(updated) such that s1 = sourceState(t) and t is marked as “Added” then

8:         //Mark ss^(M1) as “needsUpdate”

9:         *s**s*^(*M*1).*n**e**e**d**s**U**p**d**a**t**e*←*t**r**u**e*![si53\_e](images/S0065245817300487/si53_e.png)

10:         //Add state s1 and its outgoing transition t to the hashmap branchesToUpdate of ss^(M1)

11:         *s**s*^(*M*1).*b**r**a**n**c**h**e**s**T**o**U**p**d**a**t**e*←*s**s*^(*M*1).*b**r**a**n**c**h**e**s**T**o**U**p**d**a**t**e*![si54\_e](images/S0065245817300487/si54_e.png) ∪ {*s*→![si55\_e](images/S0065245817300487/si55_e.png) {t}}

12:     end if

13:     for all outgoing symbolic transitions st = (ss^(M1), l, ss′^(M1))of ss^(M1) do

14:         if there is t ∈ T^(updated) such that sourceState(t) ∈ ss^(M1).s^(M1) and targetState(t) ∈ ss′^(M1).s^(M1) then

15:             Assert t is marked as “Modified” or “Deleted”

16:             Remove l and ss′^(M1)with all its children from SET^(M1)

17:             if t is marked as “Modified” then

18:                 //Mark ss^(M1) as “needsUpdate”

19:                 *s**s*^(*M*1).*n**e**e**d**s**U**p**d**a**t**e*←*t**r**u**e*![si53\_e](images/S0065245817300487/si53_e.png)

20:                 //Add state s1 and its outgoing transition t to the hashmap branchesToUpdate of ss^(M1)

21:                 *s**s*^(*M*1).*b**r**a**n**c**h**e**s**T**o**U**p**d**a**t**e*←*s**s*^(*M*1).*b**r**a**n**c**h**e**s**T**o**U**p**d**a**t**e*![si57\_e](images/S0065245817300487/si57_e.png) ∪ {*s*→![si55\_e](images/S0065245817300487/si55_e.png) {t}}

22:             end if

23:         else

24:             q ← enqueue(q, ss′^(M1))

25:         end if

26:     end for

27: end while

28: //Task 2: Iterate over GSET^(M1) and set the attributes needsUpdate and branchesToUpdate of all leaf symbolic states that are no longer subsumed by any of previsited nodes to “true” and “All”, respectively

29: GSET^(M1) = Task2\_helperMethod(GSET^(M1))

30: //Task 3: Reexplore GSET^(M1) to merge the results from the symbolic execution of M2 for the parts that need to be updated

31: *q*←\[*s**s*[0]^(*M*1)\]![si59\_e](images/S0065245817300487/si59_e.png)

32: //Create a set of previsited symbolic states for the purpose of subsumption checking

33: SS^(preVisited) ← {}

34: while q is not empty do

35:     Remove the first element ss^(M1) = (s^(M1), val, pc, q^(M1)) from q

36:     if ss^(M1) has one or more outgoing symbolic transitions then

37:         //Record ss^(M1) in the set of previsited symbolic model states

38:         SS^(preVisited) ← SS^(preVisited) ∪ {ss^(M1)}

39:         //Add all the target symbolic states of the outgoing symbolic transitions of ss^(M1) to the queue

40:         for all outgoing symbolic transitions st = (ss^(M1), l, ss′^(M1))of ss^(M1) do

41:             q ← enqueue(q, ss′^(M1))

42:         end for

43:     end if

44:     if ss^(M1).needsUpdate then

45:         //Rerun the SE on the model version M2 taking into consideration only the states and the transitions in the hashmap branchesToUpdate of ss^(M1)

46:         for all MLM[i] in MLM^(M2) do

47:             *s*[*i*]←*s*^(*M*2)(*i*)![si60\_e](images/S0065245817300487/si60_e.png) where s[i] ∈ S[i](MLM[i])

48:             if s[i] is found in the branchesToUpdate map of ss^(M1) then

49:                 for all outgoing transitions t[i] = (s[i], e, eA, G, A, s[i]′) of s[i] do

50:                     if t[i] is found in the branchesToUpdate map of ss^(M1) then

51:                         if `(``(``q`^(`M`) `=` `ϕ``)` `∧` `(``e` `∈` `E`[`i`]^(`i``n``p`)`)``)` `∨` `(``(`head`(``q`[`i`]^(`M`)`)` `=` `e``)` `∧` `(`*e* `∈` `E`[*i*]^(*i**n**t*)`)``)`![si61\_e](images/S0065245817300487/si61_e.png) then

52:                             Create a unique set V^s of new variables in one-to-one relation with the transition's event arguments eA

53:                             Create a map σ between eA and V^s

54:                             Substitute every occurrence of a variable x ∈ eA in the guard G and the action code A by σ(x) to obtain *G*^(*s*)←*σ*(*G*)![si62\_e](images/S0065245817300487/si62_e.png) and *A*^(*s*)←*σ*(*A*)![si63\_e](images/S0065245817300487/si63_e.png)

55:                             if G^s is satisfiable given val and pc then

56:                                 feasiblePaths ← SymbolicExecutionOfCode(A^s, val, G^s, pc)

57:                                 for all feasiblePath = (val’, pc’, out’) ∈ feasiblePaths do

58:                                     *q*^′^(*M*2)←*o**u**t*^′![si64\_e](images/S0065245817300487/si64_e.png)

59:                                     Create a new symbolic model state ss′^(M2) = (s′^(M2), val′, pc′, q′^(M2)) where s′^(M2) = s^(M1).replace(s[i], *s*[*i*]^(^′)![si65\_e](images/S0065245817300487/si65_e.png))

60:                                     if ss′^(M2) is not subsumed by any previously generated symbolic model state in SS^(preVisited) then

61:                                         Mark ss′^(M2) as “needsUpdate” with respect to “All” states in s′^(M2) and “All” their outgoing transitions

62:                                         SS^(M1) ← SS^(M1) ∪ {ss′^(M2)}

63:                                         Create a new label l’ = (e, V^s, σ, out’)

64:                                         L ← L ∪ {l’}

65:                                         Create a new symbolic transition st’ = (ss^(M1), l’, ss′^(M2))

66:                                         ST ← ST ∪ {st’}

67:                                         //Recored ss′^(M2) in the set of previsited symbolic model states

68:                                         SS^(preVisited) ← SS^(preVisited) ∪ {ss′^(M2)}

69:                                         q ← enqueue(q, ss′^(M2))

70:                                     end if

71:                                 end for

72:                             end if

73:                         end if

74:                     end if

75:                 end for

76:             end if

77:         end for

78:     end if

79: end while

80:  //Task 4 (Optional): Iterate over GSET^(M1) and remove any node that can be subsumed by any other nodes (either at the same hierarchical level or higher)

81:  GSET^(M1) = Task4\_helperMethod(GSET^(M1))

82:  *M**G**S**E**T*^(*M*2)←*G**S**E**T*^(*M*1)![si66\_e](images/S0065245817300487/si66_e.png)

The three inputs to both components are (1) the MLM (resp., CMLMs) representation of the modified model version MLM^(modVer) (resp., CMLM^(modVer)), (2) the set of transitions that have been updated in the modified version of the model T^(updated), and (3) the SET^(baseVer) (resp., GSET^(baseVer)) to be reused.

Four successive tasks are performed by both components.

Task 1: The first task is to load and explore the input SET^(baseVer) (resp., GSE– T^(baseVer)) in order to: (1) remove all the edges representing any transition belonging to the set of updated transitions T^(updated) (note that removing an edge leads to removing the entire subtree rooted at the target node of the edge) and (2) mark all symbolic states (resp., symbolic model states) representing states with outgoing transitions belonging to T^(updated) as “needing an update” with respect to these outgoing transitions. This is done by updating the attributes needsUpdate and branchesToUpdate of each such symbolic state (resp., symbolic model state).

Task 2: As a result of the previous task, we may find some leaves in the resulting SET^(baseVer) (resp., GSET^(baseVer)) that lost their subsuming nodes. In this case, we need also to mark these leaves as “needing an update” with respect to all outgoing transitions of their corresponding model states. Therefore, the second task of both components is to iterate over the nodes in the SET^(baseVer) (resp., GSET^(baseVer)) resulting from the previous task and to set the attributes needsUpdate and branchesToUpdate of all leaf symbolic states (resp., symbolic model states) that are no longer subsumed to “true” and “All”, respectively. A detailed description of this task is omitted for brevity.

Task 3: The third task of both components is to reexplore the SET^(baseVer) (resp., GSET^(baseVer)) resulting from the previous task to find all symbolic states (resp., symbolic model states) that need an update. For each such symbolic state (resp., symbolic model state), we rerun the SE technique on the modified model version MLM^(modVer) (resp., CMLMs^(modVer)) targeting only the parts of the model identified by the hashmap branchesToUpdate of the symbolic state (resp., symbolic model state) and taking into consideration the set of symbolic states (resp., symbolic model states) that have been previously explored to be used for the subsumption checking. Our strategy to implement this task differs from the one that we initially used to implement the “KLEE-based MLM2MSET Generation” component in an earlier version of this work \[[94](#S0065245817300487_3.xhtml#bb0475)\]. This modification is done based on the intuition that we got from applying the MSE technique for individual Statecharts where we found that our Initial Nodes Update Strategy may generate, in some cases, extra symbolic states. The process of detecting and removing these extra symbolic states may reduce the efficiency of the technique especially for large SETs. Additionally, when we followed the same strategy in the implementation of the “KLEE-based CMLM2MGSET Generation” component, we found, based on an initial evaluation of the technique, that it generates larger MGSETs with many extra symbolic model states. Therefore, we have adapted this initial nodes update strategy in the implementation of the two components: “KLEE-based MLM2MSET Generation” and “KLEE-based CMLM2MGSET Generation” presented here such that we overcome, to some extent, this problem. The difference between both strategies lies in the way we generate the subtrees required to update the symbolic states (resp., symbolic model states) that need an update. In the following, we explain this in details.

1.  (1) Initial Nodes Update Strategy (INUS): Our initial nodes update strategy depends on generating the subtrees required to update symbolic states (resp., symbolic model states) that are marked as “needing an update” independently (i.e., one at a time and in a breadth-first manner) by running an adapted version of the SE on the modified model version based on some additional parameters. These additional parameters determine where the exploration starts (i.e., the symbolic state to begin the exploration at), which updated transitions to consider when exploring the state representing the start symbolic state for the first time, and the set of symbolic states that have been previously explored to be used for the subsumption checking. The resulting sub-SETs for running this adapted version of the SE are to be merged with their corresponding symbolic states in the SET^(baseVer). One limitation of this strategy is that it prevents the detection of existing subsumption relationships between symbolic states in the sub-SETs that were generated first and symbolic states in the sub-SETs that are generated later.
2.  (2) Adapted Nodes Update Strategy (ANUS): One possible solution to overcome the limitation presented in the initial nodes update strategy is to run the SE on the modified model version for symbolic states (resp., symbolic model states) that need an update on-the-fly as they are identified. In this case, the construction of the sub-SETs for the nodes that need an update is carried out jointly (concurrently) at the same time rather than successively as in the initial strategy. This procedure is implemented in [Algorithm 7](#S0065245817300487_2.xhtml#b0040), Lines 30–68 and in [Algorithm 8](#S0065245817300487_2.xhtml#b0045), Lines 30–79. This strategy can overcome part (but not all) of the limitation raised by the initial strategy (i.e., we may also find some extra symbolic model states in the generated SETs following this strategy as well).

A step-by-step illustration of both update strategies is shown in [Figs. 16](#S0065245817300487_2.xhtml#f0075) and [17](#S0065245817300487_2.xhtml#f0080), respectively, for updating nodes 2 and 5 in the example SET shown in [Fig. 18](#S0065245817300487_2.xhtml#f0085). Please note that: (1) nodes are labeled based on their creation order and (2) leading zeros in a node label indicate the number of reruns of the SE technique that created the node. A comparison between the SETs generated after applying each update strategy is shown in [Fig. 19](#S0065245817300487_2.xhtml#f0090). A demonstration of a scenario of an undetected subsumption relation between existing and newly created nodes following any of the two presented nodes update strategies is shown in [Fig. 20](#S0065245817300487_2.xhtml#f0095). In this scenario, the root node “0” is marked as “needing an update” with respect to a newly added branch which is colored red. Following either update strategies will generate the subtree consisting of nodes “001”, “002”, and “003”. Assume the case where a subsumption relation now exists between the already existing node “5” and the newly created node “001”. In this case, nodes “02”, “03”, “06”, and “07” are considered extra nodes. This is because the newly detected subsumption relation between nodes “5” and “001” does not exist before the creation of node “001” and also when the generation of nodes “02”, “03”, “06”, and “07” took place.

![Fig. 16 A demonstration of the Initial Nodes Update Strategy used in the implementation of an earlier version of MSE \[94, 95\]. Nodes are labeled based on their creation order and leading zeros in a node label indicate the number of reruns of the SE technique that created the node. (A) Step 1: Reexploring node 2 given previsited nodes = {0, 1, 2, 3, 4, 5, 6}. (B) Step 2: Merging the subtree updating node 2 with the original SET. (C) Step 3: Reexploring node 5 given previsited nodes = {0, 1, 2, 3, 4, 5, 6, 01, 02, 03, 04, 05}. (D) Step 4: Merging the subtree updating node 5 with the original SET.](images/S0065245817300487/f04-16-9780128151198.jpg)

Fig. 16 A demonstration of the Initial Nodes Update Strategy used in the implementation of an earlier version of MSE \[[94](#S0065245817300487_3.xhtml#bb0475), [95](#S0065245817300487_3.xhtml#bb0480)\]. Nodes are labeled based on their creation order and leading zeros in a node label indicate the number of reruns of the SE technique that created the node. (A) Step 1: Reexploring node 2 given previsited nodes = {0, 1, 2, 3, 4, 5, 6}. (B) Step 2: Merging the subtree updating node 2 with the original SET. (C) Step 3: Reexploring node 5 given previsited nodes = {0, 1, 2, 3, 4, 5, 6, 01, 02, 03, 04, 05}. (D) Step 4: Merging the subtree updating node 5 with the original SET.

![Fig. 17 A demonstration of the Adapted Nodes Update Strategy used in the implementation of the current version of MSE as presented in Algorithms 7 and 8—one-level depth exploration with marking generated nodes (if not subsumed by a previsited node) as “needing an update”. Nodes are labeled based on their creation order and leading zeros in a node label indicate the number of reruns of the SE technique that created the node. (A) Step 1: One-level depth exploration of node 2 given previsited nodes = {0, 1, 2, 3, 4, 5, 6}. The resulting node 01 is marked (with double circles) as “needing an update”. (B) Step 2: One-level depth exploration of node 5 given previsited nodes = {0, 1, 2, 3, 4, 5, 6, 01}. The resulting node 02 is marked (with double circles) as “needing an update”, while the resulting node 03 is found to be subsumed by one of the given previsited nodes. (C) Step 3: One-level depth exploration of node 01 given previsited nodes = {0, 1, 2, 3, 4, 5, 6, 01, 02, 03}. The resulting nodes 04 and 05 are both found to be subsumed by one of the given previsited nodes. Note that subsumption relation between nodes 04 and 02 is detected. (D) Step 4: One-level depth exploration of node 02 given previsited nodes = {0, 1, 2, 3, 4, 5, 6, 01, 02, 03, 04, 05}. The resulting nodes 06 and 07 are both found to be subsumed by one of the given previsited nodes.](images/S0065245817300487/f04-17-9780128151198.jpg)

Fig. 17 A demonstration of the Adapted Nodes Update Strategy used in the implementation of the current version of MSE as presented in Algorithms [7](#S0065245817300487_2.xhtml#b0040) and [8](#S0065245817300487_2.xhtml#b0045)—one-level depth exploration with marking generated nodes (if not subsumed by a previsited node) as “needing an update”. Nodes are labeled based on their creation order and leading zeros in a node label indicate the number of reruns of the SE technique that created the node. (A) Step 1: One-level depth exploration of node 2 given previsited nodes = {0, 1, 2, 3, 4, 5, 6}. The resulting node 01 is marked (with double circles) as “needing an update”. (B) Step 2: One-level depth exploration of node 5 given previsited nodes = {0, 1, 2, 3, 4, 5, 6, 01}. The resulting node 02 is marked (with double circles) as “needing an update”, while the resulting node 03 is found to be subsumed by one of the given previsited nodes. (C) Step 3: One-level depth exploration of node 01 given previsited nodes = {0, 1, 2, 3, 4, 5, 6, 01, 02, 03}. The resulting nodes 04 and 05 are both found to be subsumed by one of the given previsited nodes. Note that subsumption relation between nodes 04 and 02 is detected. (D) Step 4: One-level depth exploration of node 02 given previsited nodes = {0, 1, 2, 3, 4, 5, 6, 01, 02, 03, 04, 05}. The resulting nodes 06 and 07 are both found to be subsumed by one of the given previsited nodes.

![Fig. 18 An example SET with nodes 2 and 5 are marked as “needing an update” with respect to some of their outgoing branches. Nodes are labeled based on their creation order.](images/S0065245817300487/f04-18-9780128151198.jpg)

Fig. 18 An example SET with nodes 2 and 5 are marked as “needing an update” with respect to some of their outgoing branches. Nodes are labeled based on their creation order.

![Fig. 19 Comparison between our two nodes update strategies showing (in A) a demonstration of undetected subsumption relation (SR) between nodes 02 and 001 resulting in having extra nodes 04 and 05. (A) Less optimized MSET resulting from our Initial Nodes Update Strategy. (B) A more optimized MSET resulting from our Adapted Nodes Update Strategy.](images/S0065245817300487/f04-19-9780128151198.jpg)

Fig. 19 Comparison between our two nodes update strategies showing (in A) a demonstration of undetected subsumption relation (SR) between nodes 02 and 001 resulting in having extra nodes 04 and 05. (A) Less optimized MSET resulting from our Initial Nodes Update Strategy. (B) A more optimized MSET resulting from our Adapted Nodes Update Strategy.

![Fig. 20 A demonstration of a possible case of undetected subsumption relation (SR) between nodes 5 and 001 resulting in having extra nodes 02, 03, 06, and 07.](images/S0065245817300487/f04-20-9780128151198.jpg)

Fig. 20 A demonstration of a possible case of undetected subsumption relation (SR) between nodes 5 and 001 resulting in having extra nodes 02, 03, 06, and 07.

Task 4: Since the resulting SETs (resp., GSETs) of the previous task may contain some extra symbolic states (resp., symbolic model states), the last task to be performed in both components is to detect and remove such extra symbolic states (resp., symbolic model states). A detailed description of this task is straightforward and omitted for brevity.

In [Table 1](#S0065245817300487_2.xhtml#t0010), we highlight the steps of the algorithms implementing each one of the aforementioned four tasks of both components.

 

Table 1

 Components’ Tasks and Their Corresponding Algorithms’ Steps 

 
| Task  || Component |
| --- | --- |
| KLEE-Based CMLM2MSET Generation || KLEE-Based CMLM2MGSET Generation |
| Task 1 || [Algorithm 7](#S0065245817300487_2.xhtml#b0040), Lines 1–27 || [Algorithm 8](#S0065245817300487_2.xhtml#b0045), Lines 1–27 |
| --- | --- | --- |
| Task 2 || [Algorithm 7](#S0065245817300487_2.xhtml#b0040), Lines 28–29 || [Algorithm 8](#S0065245817300487_2.xhtml#b0045), Lines 28–29 |
| Task 3 || [Algorithm 7](#S0065245817300487_2.xhtml#b0040), Lines 30–68 || [Algorithm 8](#S0065245817300487_2.xhtml#b0045), Lines 30–79 |
| Task 4 (Optional) || [Algorithm 7](#S0065245817300487_2.xhtml#b0040), Lines 69–70 || [Algorithm 8](#S0065245817300487_2.xhtml#b0045), Lines 80–81 |

![t0010](images/S0065245817300487/t0010.png)

The output from both components is a memoization-based SET (resp., GSET) of the modified model version, MSET^(modVer) (resp., MGSET^(modVer)), that shares all what can be reused from the old tree SET^(baseVer) (resp., GSET^(baseVer)) but also contains the modifications resulting from the SE of the parts of the new version of the model that are found changed. We use a tree-based data structure for representing, storing, retrieving, and manipulating these SETs.

Example 5

Applying MSE on the modified model of individual Statechart V1 shown in [Fig. 9B](#S0065245817300487_1.xhtml#f0040) and on the modified model of communicating Statecharts AB^(V1) shown in [Fig. 12](#S0065245817300487_1.xhtml#f0055) generates the memoization-based SET (resp., GSET) that are shown in [Figs. 11A](#S0065245817300487_1.xhtml#f0050) and [13](#S0065245817300487_1.xhtml#f0060), respectively. The amount of savings gained from applying MSE on the modified model V1 (or AB^(V1)) compared to applying standard SE on the same models is measured by the percentage of reused nodes (which are colored black) to the total number of nodes in the resulting MSET (or MGSET). We can see that the savings obtained in the MSET(V1) in [Fig. 11A](#S0065245817300487_1.xhtml#f0050) is equal to 6/14 (i.e., approximately 43%), while the savings gained in the MGSET(AB^(V1)) in [Fig. 13](#S0065245817300487_1.xhtml#f0060) is equal to 11/21 (i.e., approximately 52%).

It is quite clear that in some cases the savings gained from MSE can be very minimal depending on how many tree nodes are reused and the location of tree nodes that need to be updated. In this case, it is the analyst decision to choose between using MSE or standard SE.

##### 5.2.1.2 Discussion

We consider MSE an example of an artifact-oriented optimization technique because it can be used to optimize the generation of one type of intermediate artifact (in our case they are in the form of SETs) as the system evolves. At any point in time, these intermediate artifacts are maintained (i.e., up-to-date) and complete (i.e., they represent all execution paths of their corresponding models) and thus they can be used to run any SET-based analyses.

Nevertheless, by marking the new parts of the generated MSETs (resp., MGSETs) resulting from MSE from the reused parts, we can use the new parts to run regression-based analyses. In that sense, MSE can also be considered as an example of an analysis-oriented optimization technique meaning that if a given analysis has been performed on a given model before the change, then using only the new parts of the generated MSETs (resp., MGSETs) of the model after the change will allow us to rerun the same analysis and to conclude the overall correctness of the changed model.

#### 5.2.2 Dependency-Based Symbolic Execution

In this section we present our DSE technique ^([e](#S0065245817300487_3.xhtml#fn0030)) for both individual and communicating Statecharts. The architectures of the implementation of the proposed approach are shown in [Fig. 21A and B](#S0065245817300487_2.xhtml#f0100), respectively.

![Fig. 21 Dependency-based symbolic execution (DSE) proposed architecture. (A) DSE architecture for evolving individual Statecharts. (B) DSE architecture for evolving communicating Statecharts.](images/S0065245817300487/f04-21-9780128151198.jpg)

Fig. 21 Dependency-based symbolic execution (DSE) proposed architecture. (A) DSE architecture for evolving individual Statecharts. (B) DSE architecture for evolving communicating Statecharts.

##### 5.2.2.1 Technique Description

The main idea of this technique is to generate a subset (or a partial view) of the complete SET of a modified model version that characterizes all model paths that are impacted by the change which is sufficient to perform regression-based analyses. To achieve this, we integrate a dependency-based change impact analysis with our standard SE technique such that we can direct the successive runs of the SE technique to fully explore model transitions that are impacted by the change and to partially explore model transitions that are not impacted by the change. A full exploration of a model transition means to consider all the symbolic execution paths resulting from symbolically executing the transition guard and action code, while a partial exploration means to consider only one of these symbolic paths, namely the first one. Note that only models with multipath transitions (i.e., transitions with disjoint guard conditions and/or conditional statements in their action code) can benefit from this technique. We found that this model feature is extensively used in many of existing Simulink/Stateflow models. In our model examples in [Section 5.1](#S0065245817300487_1.xhtml#s0170), transitions T1 and T2 in [Fig. 9](#S0065245817300487_1.xhtml#f0040) (resp., transition itsA-T1 in [Fig. 12A](#S0065245817300487_1.xhtml#f0055)) are all examples of multipath transitions. The SE of each one of these transitions results in two symbolic paths originating at the same symbolic state (resp., symbolic model state) representing the source state of the transition and ending at two different symbolic states (resp., symbolic model states) representing the target state of the transition, each of which is characterized by the valuations of variables, the path constraints and the updates of queues resulting from the symbolic evaluation of each branch in the guard condition and in the conditional and iterative statements found in the action code of the transition.

Based on this idea we can conclude that the key requirements of this technique are first to identify the differences between two model versions and second to perform a dependency analysis on the modified model version to compute the impact of these differences. These two requirements are achieved by the two components “Model Differencing” and “Dependency-based Change Impact Analysis” shown in [Fig. 21A and B](#S0065245817300487_2.xhtml#f0100).

To implement the “Model Differencing” component, we follow the same procedure as in the previous section. First we use the Rhapsody DiffMerge to find the differences between two Rhapsody models, then we use our “SC2MLM DiffMap” (resp., “RhapM2CMLM DiffMap”) component to map these differences to their MLMs (resp. CMLMs) correspondences. The output in this case, as we explained earlier, represents the set T^(updated) of all transitions that are found to have been updated in the modified MLM (resp., CMLMs) version. Each element in the set T^(updated) indicates the name of a transition that has been affected by the change, the name of the source state of this transition, and the change type applied to this transition (i.e., “Addition”, “Deletion”, “Modification”).

To implement the “Dependency-based Change Impact Analysis” component, we considered the two types of dependences discussed in [Section 2.3](#S0065245817300487_1.xhtml#s0060): data dependence (DD) and communication dependence (COMD). The formal definitions of both types of dependences and the algorithms to compute them are provided in [Section 2.3](#S0065245817300487_1.xhtml#s0060). The two inputs to this component are (1) the MLM (resp., CMLMs) representation of the modified model version MLM^(modVer) (resp., CMLM^(modVer)), and (2) the set of transitions T^(updated) that have been updated in the modified model version. The first task to be performed by this component is to compute the data dependences and the communication dependences between the transitions of the input model version. The second task to be performed is to identify the set of transitions T^(impacted) that have a dependency relation (DD or COMD) with any of the transitions in T^(updated). The output of this component is the union set of T^(updated) and T^(impacted); these transitions are the ones that we need to fully explore when we run our DSE technique on the modified model version MLM^(modVer) (resp., CMLM^(modVer)).

The last task to be performed is to run the symbolic execution of the modified version of the model guided by the list of updated/impacted transitions resulting from the “Dependency-based Change Impact Analysis” component. Two modes of exploration are defined: “full” and “partial”. The “full” exploration mode requires a complete exploration of all execution paths (i.e., symbolic transitions) of a given transition and is applied to all transitions that are found to have been updated or impacted. However, the “partial” exploration mode requires the execution of only one path (i.e., symbolic transition) of an explored transition and is applied to transitions that are found neither updated nor impacted. The components performing this task are the “KLEE-based MLM2DSET Generation” component shown in [Fig. 21A](#S0065245817300487_2.xhtml#f0100) for individual Statecharts and the “KLEE-based CMLM2DGSET Generation” component shown in [Fig. 21B](#S0065245817300487_2.xhtml#f0100) for communicating Statecharts. The algorithms implementing this task for each component are listed in [Algorithm 9](#S0065245817300487_2.xhtml#b0050) and [Algorithm 10](#S0065245817300487_2.xhtml#b0055), respectively.

Algorithm 9

Dependency-Based Symbolic Execution (DSE) of an Evolving MLM

Input:

1: A modified MLM model version: MLM^(modVer) = (S, V, E, EA, T, s[0], V[0])

2: A set of all changed transitions and their imapcted ones: T^(ofInterest) = T^(updated) ∪ T^(impacted)

Output:

1: A Dependency-based SET of MLM^(modVer): DSET^(modVer) = (SS, L, ST, ss[0])

Steps:

1: *s**s*[0]←(*s*[0],*V*[0],true)![si67\_e](images/S0065245817300487/si67_e.png)

2: *S**S*←{*s**s*[0]}![si68\_e](images/S0065245817300487/si68_e.png)

3: *L*←{}![si69\_e](images/S0065245817300487/si69_e.png)

4: *S**T*←{}![si70\_e](images/S0065245817300487/si70_e.png)

5: Create a queue q

6: *q*←\[*s**s*[0]\]![si71\_e](images/S0065245817300487/si71_e.png)

7: //Explore the MLM in Breadth-First-Search fashion

8: while q is not empty do

9:     Remove the first element ss = (s, val, pc) from q

10:     for all outgoing transitions t = (s, e, eA, G, A, s’) of s do

11:         Create a unique set V^s of new variables in one-to-one relation with the transition event's arguments eA

12:         Create a map σ between eA and V^s

13:         Substitute every occurrence of a variable x ∈ eA in the guard G and the action code A by σ(x) to obtain *G*^(*s*)←*σ*(*G*)![si72\_e](images/S0065245817300487/si72_e.png) and *A*^(*s*)←*σ*(*A*)![si63\_e](images/S0065245817300487/si63_e.png)

14:         if G^s is satisfiable given val and pc then

15:             feasiblePaths ← SymbolicExecutionOfCode(A^s, val, G^s, pc)

16:             if t ∈ T^(ofInterest) then

17:                 //Full-exploration mode

18:                 for all feasiblePath = (val’, pc’, out’) ∈ feasiblePaths do

19:                     Create a new symbolic state, ss’ = (s’, val’, pc’)

20:                     if ss’ is not subsumed by any previously generated state then

21:                         SS ← SS ∪ {ss’}

22:                         Create a new label, l’ = (e, V^s, σ, out’)

23:                         L ← L ∪ {l’}

24:                         Create a new symbolic transition, st’ = (ss, l’, ss’)

25:                         ST ← ST ∪ {st’}

26:                         q ← enqueue(q, ss’)

27:                     end if

28:                 end for

29:             else

30:                 //Partial-exploration mode

31:                 Select only one feasiblePath = (val’, pc’, out’) ∈ feasiblePaths

32:                 Create a new symbolic state, ss’ = (s’, val’, pc’)

33:                 if ss’ is not subsumed by any previously generated state then

34:                     SS ← SS ∪ {ss’}

35:                     Create a new label, l’ = (e, V^s, σ, out’)

36:                     L ← L ∪ {l’}

37:                     Create a new symbolic transition, st’ = (ss, l’, ss’)

38:                     ST ← ST ∪ {st’}

39:                     q ← enqueue(q, ss’)

40:                 end if

41:             end if

42:         end if

43:     end for

44: end while

Algorithm 10

Dependency-based Symbolic Execution (DSE) of an Evolving CMLM

Input:

1: A modified CMLM model version of n communicating MLMs: M = (*M**L**M*^(*M*), *Q*^(*M*), *s*[0]^(*M*), *V*^(*M*), *V*[0]^(*M*)![si74\_e](images/S0065245817300487/si74_e.png))

2: A set of all changed transitions and their imapcted ones: T^(ofInterest) = T^(updated) ∪ T^(impacted)

Output:

1: A Dependency-based GSET of M: DGSET^M = (SS^M, L, ST, *s**s*[0]^(*M*)![si39\_e](images/S0065245817300487/si39_e.png))

Steps:

1: *s**s*[0]^(*M*)←(*s*[0]^(*M*), *V*[0]^(*M*), true, *q*[0]^(*M*))![si40\_e](images/S0065245817300487/si40_e.png)

2: SS^M ← {*s**s*[0]^(*M*)![si39\_e](images/S0065245817300487/si39_e.png)}

3: L ← {}

4: ST ← {}

5: Create a queue q

6: q ← \[*s**s*[0]^(*M*)![si39\_e](images/S0065245817300487/si39_e.png)\]

7: //Breadth-First-Search fashion exploration for each MLM in M

8: while q is not empty do

9:     Remove the first element ss^M = (s^M, val, pc, q^M) from q

10:     for all MLM[i] in MLM^M do

11:         *s*[*i*]←*s*^(*M*)(*i*)![si43\_e](images/S0065245817300487/si43_e.png) where s[i] ∈ S[i](MLM[i])

12:         for all outgoing transitions t[i] = (s[i], e, eA, G, A, s[i]′) of s[i] do

13:             if `(``(``q`^(`M`) `=` `ϕ``)` `∧` `(``e` `∈` `E`[`i`]^(`i``n``p`)`)``)` `∨` `(``(`head`(``q`[`i`]^(`M`)`)` `=` `e``)` `∧` `(``e` `∈` `E`[`i`]^(`i``n``t`)`)``)`![si44\_e](images/S0065245817300487/si44_e.png) then

14:                 Create a unique set V^s of new variables in one-to-one relation with the transition's event arguments eA

15:                 Create a map σ between eA and V^s

16:                 Substitute every occurrence of a variable x∈ eA in the guard G and the action code A by σ(x) to obtain G^s ← σ(G) and A^s ← σ(A)

17:                 if G^s is satisfiable given val and pc then

18:                     feasiblePaths ← SymbolicExecutionOfCode(A^s, val, G^s, pc)

19:                     if t ∈ T^(ofInterest) then

20:                         //Full-exploration mode

21:                         for all feasiblePath = (val’, pc’, out’) ∈ feasiblePaths do

22:                             *q*^′^(*M*)←*o**u**t*^′![si81\_e](images/S0065245817300487/si81_e.png)

23:                             Create a new symbolic state, ss′^M = (s′^M, val′, pc′, q′^M) where s′^M = s^M.replace(s[i], *s*[*i*]^′![si82\_e](images/S0065245817300487/si82_e.png))

24:                             if ss′^M is not subsumed by any previously generated symbolic model state in SS^M then

25:                                 SS^M ← SS^M ∪ {ss′^M}

26:                                 Create a new label, l’ = (e, V^s, σ, out’)

27:                                 L ← L ∪ {l’}

28:                                 Create a new symbolic transition, st’ = (ss^M, l’, ss′^M)

29:                                 ST ← ST ∪ {st’}

30:                                 q ← enqueue(q, ss′^M)

31:                             end if

32:                         end for

33:                     else

34:                         //Partial-exploration mode

35:                         Select only one feasiblePath = (val’, pc’, out’) ∈ feasiblePaths

36:                         *q*^′^(*M*)←*o**u**t*^′![si81\_e](images/S0065245817300487/si81_e.png)

37:                         Create a new symbolic state, ss^M′ = (s′^M, val′, pc′, q′^M) where s′^M = s^M.replace(s[i], *s*[*i*]^′![si82\_e](images/S0065245817300487/si82_e.png))

38:                         if ss′^M is not subsumed by any previously generated symbolic model state in SS^M then

39:                             SS^M ← SS^M ∪ {ss′^M}

40:                             Create a new label, l’ = (e, V^s, σ, out’)

41:                             L ← L ∪ {l’}

42:                             Create a new symbolic transition, st’\=(ss^M, l’, ss′^M)

43:                             ST ← ST ∪ {st’}

44:                             q ← enqueue(q, ss′^M)

45:                         end if

46:                     end if

47:                 end if

48:             end if

49:         end for

50:     end for

51: end while

 

Example 6

Applying our dependency-based change impact analysis on the model version V1 will not report transition T1 among the list of transitions that are data dependent on the modified transition T2. As a result, only a partial exploration of transition T1 is performed and since it is a multipath transition, only one feasible path (i.e., one symbolic transition) is considered and the rest are pruned. Similarly, applying our dependency-based change impact analysis on the model version AB^(V1) will not report transition itsA-T1 among the list of transitions that are data or communication dependent on the modified transitionitsA-T2. As a result, only a partial exploration of transition itsA-T1 is performed and since it is a multipath transition, only one feasible path (i.e., one symbolic transition) is considered and the rest are pruned. The amount of savings gained from applying DSE is measured by the percentage of nodes that are pruned during the partial exploration mode. We can see that the savings gained in the DSET(V1) in [Fig. 11B](#S0065245817300487_1.xhtml#f0050) is approximately equal to 43% which is the percentage of the 6 pruned nodes (these which are colored gray) to the total number of nodes of the complete SET which is 14 nodes. Similarly, the savings gained in the DGSET(AB^(V1)) in [Fig. 14](#S0065245817300487_1.xhtml#f0065) is approximately equal to 43% which is the percentage of the 9 pruned nodes (these which are colored gray) to the total number of nodes of the complete GSET which is 21 nodes.

##### 5.2.2.2 Discussion

Assume that the SET-based type of analysis required here is to check that the system has no dead ends.^([f](#S0065245817300487_3.xhtml#fn0035)) In a given SET, a tree leaf that is not subsumed by any other node in the tree may indicate (1) reaching a previsited symbolic state, (2) reaching a depth bound of some loop, or (3) reaching a dead end symbolic state. In our example, we neither have termination states nor loops in any of the action code of transitions. Therefore, in this case, a SET leaf node that is not subsumed by any other node will indicate a dead end symbolic state. Also, assume that an analyst has performed this type of analysis on the GSET(AB^(V0)) and has concluded that AB^(V0) has no dead ends. In this case, applying the same type of analysis on the DGSET(AB^(V1)), which is a partial view of the GSET(AB^(V1)), will be sufficient to check whether AB^(V1) has a dead end or not. By checking the leaves of the DGSET(AB^(V1)), we can see that the symbolic model state SS15 is not subsumed by any other node in the tree and thus we can conclude that AB^(V1) has a dead end. By inspecting (1) the valuations of the variables and the contents of the queues of this symbolic model state (i.e., SS15) and (2) the outgoing transition itsB-T3 of state bS2 that is fired by the event e5, we can see that the guard of this transition is unsatisfiable with respect to the given value of the event parameter. Since the DGSET(AB^(V1)) represents only a subset of the complete GSET(AB^(V1)), we cannot use it to perform a different type of analysis. In that sense, DSE is considered as an example of an analysis-oriented optimization approach.

### 5.3 MSE or DSE?

Based on our discussion of the idea behind each technique, we conclude

*   – For MSE, we need to have access to the SET (resp., GSET) of the original model (i.e., the model before the change) to be reused and we need to identify the differences between the new version of the model and the original one. We speculate that the effectiveness of this technique may be highly dependent on the change location. The resulting MSET (resp., MGSET) represents all execution paths of the modified model (i.e., the model after the change) and can thus be used to perform all SET-based analyses. However, if reestablishing a previous analysis result as the goal, a regression analysis can also be run on just the changed parts of the SET.
*   – For DSE, we need to identify the differences between the new version of the model and the original one as well as to integrate a dependence analysis to identify the impact of the change. We speculate that models with complex guards and action code may benefit most from this technique. As the resulting DSET (resp., DGSET) may not be complete and omit executions that are guaranteed to not have been impacted by the change, it can be used only to run regression-types of analysis.

Having said that, we think that both optimization techniques complement each other, in the sense that they both can serve the same purpose but are most useful under different circumstances, and it is the role of the analyst to choose among them. For instance, the availability of the SET from a previous analysis is a basic requirement for applying MSE, while the complexity of the guards or action code of the transitions in the model under study is a key factor for the effectiveness of DSE.

### 5.4 Summary

In this section we have presented two symbolic execution optimization techniques, MSE and DSE, for both evolving individual and communicating Statecharts. We first explained with examples the idea behind each technique. Second, we introduced our proposed architectures for both techniques and provided the required description of the different components in each architecture.

## 6 Implementation

In this section we provide a high-level description of the implementation decisions that we have made to build the architectures presented in [Section 4](#S0065245817300487_1.xhtml#s0125) for Standard SE and in [Section 5](#S0065245817300487_1.xhtml#s0165) for MSE and DSE. [Fig. 22](#S0065245817300487_2.xhtml#f0105) shows the operating system required and the technology used to implement each of the components presented in these architectures. We first highlight the implementation decisions that we made based on the initial requirements of this research work. Second, we provide the details of three core tasks. These are (1) the interaction with the symbolic execution engine KLEE, (2) building the model transformation and text generation in the context of IBM Rational Rhapsody RulesComposer, and (3) the interaction with the IBM Rational Rhapsody DiffMerge tool.

![Fig. 22 Implementation illustration of our developed components.](images/S0065245817300487/f04-22-9780128151198.jpg)

Fig. 22 Implementation illustration of our developed components.

### 6.1 Implementation Decisions

Most of the implementation decisions that we made are based on the following two main requirements.

1.  (1) The context and the type of state-based models that we are going to use to develop our research. The decision of this aspect was made based on an interest from our industrial partner to provide such analysis capability for the state-based models developed in the context of the IBM Rational Rhapsody MDE tool, which are known as Rhapsody Statecharts. We found that although working with proprietary and commercial tools has its advantage in terms of quality and documentation, they limit the choices one may have to develop some external functionality or process and manipulate the artifacts they create to some extent. Therefore, we decided to implement our required components using IBM related tools (e.g., IBM Rational Rhapsody Developer RulesComposer Add-On for model transformation and custom code generation, and IBM Rational Rhapsody DiffMerge for model differencing).
2.  (2) The symbolic execution engine to be reused for the action code encountered in the state-based models to be analyzed. Our decision was to use the KLEE symbolic execution engine—an open-source symbolic execution engine for C code. We made this decision after we examined the feasibility of building an API that enables the interaction with KLEE. In [Section 6.2](#S0065245817300487_2.xhtml#s0240), we provide a more detailed description of this process. To be able to use KLEE for the symbolic execution of the fragments of action code encountered in Rhapsody Statecharts, we only consider a subset of Java and C++ code that has the same syntax as C code, including the basic assignment statements, conditional statements, and iterative statements. The data types supported are the basic types including characters, Booleans, and integer numbers. We also consider the type of statements that are used in the action code for sending events to other objects.

Unfortunately, KLEE does not run under Windows. It runs only on certain types of Linux distributions including Ubuntu but not Red Hat. On the other hand, the IBM Rational Rhapsody tools can be installed on Windows and only on the Red Hat Linux distribution. Therefore, we decided to add the Ubuntu VM to our Windows machine. The IBM Rational Rhapsody tools are to be installed on the Windows machine and the KLEE symbolic execution engine is to be installed on the Ubuntu VM. The decision of which component is to be implemented on which VM was made based on the functionality of each component and the development environment it requires. [Fig. 22](#S0065245817300487_2.xhtml#f0105) highlights this categorization. For example, components that require the IBM infrastructure to operate are developed and run on Windows. Examples of these components are the “SC2MLM Transformation” and “RhapM2CMLM Transformation”, which are implemented in the context of the Rhapsody RulesComposer Add-On to perform the following two tasks: (1) to translate from Rhapsody Statecharts to MLM and (2) to compute the data and communication dependencies in and between the generated MLMs. Similarly, components “SC2MLM DiffMap”, “RhapM2CMLM DiffMap”, and “Dependency-based Change Impact Analysis” require the manipulation of the files representing the MLMs generated from the transformation components and this requires access to the MLM meta-model and its related schema definitions which are tool-dependent generated artifacts. Thus, we have implemented these components as a Java project in the context of the Rhapsody RulesComposer Add-On. All other components which are the KLEE-based ones require the interaction with the KLEE symbolic execution engine and therefore they are developed and run on the Ubuntu VM.

In order to facilitate the communication between the part of the implementation that runs on the Ubuntu VM (where KLEE works) and the part that runs on the Windows VM (where the IBM Rational Rhapsody tool works), we use the Java Remote Method Invocation (RMI) system. We developed the part of the implementation that runs on the Ubuntu VM side as an RMI server API and the part of the implementation that runs on Window VM as an RMI client API which has been integrated with the IBM Rational Rhapsody tool as an external helper.

### 6.2 Interaction With KLEE

We referred to this task in the algorithms provided in [Sections 4](#S0065245817300487_1.xhtml#s0125) and [5](#S0065245817300487_1.xhtml#s0165) using the pseudo-code function: SymbolicExecutionOfCode(A^s, val, G^s, pc). It identifies the information necessary to symbolically execute the action code and the guard of a transition given the variables’ valuation and the path constraints collected to reach a symbolic state corresponding to the source state of a transition. The output from executing this statement is a set of all feasible paths resulting from parsing the output from the KLEE symbolic execution engine which we use to create a set of symbolic transitions and their target symbolic states. In the sequel we explain in details how we implement this task using the illustrations in [Fig. 23](#S0065245817300487_2.xhtml#f0110).

![Fig. 23 An example illustrating an execution of the pseudo-code function SymbolicExecutionOfCode(As, val, Gs, pc). (A) On the left is part of a Statechart showing a transition T2 and its source and target States S2 and S3. On the right is a symbolic state SS4 of the source state S2. (B) Illustration of our interface components with KLEE. (C) Highlighted (in red) are the generated symbolic transitions ST7 and ST8 and their target symbolic states SS8 and SS9 resulting from the SE of transition T2 given a symbolic state SS4 of its source state S2.](images/S0065245817300487/f04-23-9780128151198.jpg)

Fig. 23 An example illustrating an execution of the pseudo-code function SymbolicExecutionOfCode(A^s, val, G^s, pc). (A) On the left is part of a Statechart showing a transition T2 and its source and target States S2 and S3. On the right is a symbolic state SS4 of the source state S2. (B) Illustration of our interface components with KLEE. (C) Highlighted (in red) are the generated symbolic transitions ST7 and ST8 and their target symbolic states SS8 and SS9 resulting from the SE of transition T2 given a symbolic state SS4 of its source state S2.

In [Fig. 23A](#S0065245817300487_2.xhtml#f0110), we show (1) on the left, part of an example Statechart model that consists of two states: S2 and S3 which are connected by a transition T2 and (2) on the right, an example symbolic state representation SS4 of the transition's source state S2. We also highlight the necessary information about the attribute(s) defined for the given model, the event e2 of transition T2 and its arguments (if any) and the symbolic variable(s) used in the given symbolic state representation SS4. In [Fig. 23B](#S0065245817300487_2.xhtml#f0110), we show the flow diagram of how we interact with the KLEE symbolic execution engine to symbolically execute the action code of transition T2 given the symbolic state SS4. In this flow diagram, we identify two components: “KLEE Input File Preparation” and “Feasible Paths Data Extraction”.

The “KLEE Input File Preparation” component takes as inputs a transition to be symbolically explored and a symbolic state representing the source state of the transition and generates as an output C file named “TAC.c” which has at the beginning the declarations of all required variables, including those which are symbolic, and the action code statements of the input transition as well as the path constraints definition of the input symbolic state. Following this, we add, for every declared variable, a conditional statement to check whether its last assigned value is concrete or symbolic and to record in a user-defined output file named “TAC-output.txt” the variable name and its value if it is concrete or the keyword “SYMBOLIC” if it is symbolic. In order to get the symbolic expression corresponding to a symbolic variable, we use KLEE's special function klee\_print\_expr which prints its output to the STDOUT stream of the running process. In order to manipulate this output, we redirect the STDOUT stream into a file named “klee-stdout.log”. The output C file “TAC.c” is to be compiled and executed by the KLEE symbolic execution engine. The output from the execution is recorded in an output directory named “klee-out-0” which is created by KLEE. We also use this directory to record the aforementioned user-created files: “TAC-output.txt” and “klee-stdout.log”.

Having the output files generated from KLEE ready, the next step is to parse these files to extract the required information about each feasible path reported by KLEE. This step is performed by the “Feasible Paths Data Extraction” component which consists of a series of shell script calls and a parser generated by JavaCC. Among the list of global files that KLEE generates for each execution, there is a set of per-path files to record information about the test case generated by KLEE for each path and the constraints associated with each path. The extensions for these files are .ktest and .pc, respectively. The test case files are binary files which require a specific tool called ktest-tool to read their contents, however the path constraint files are textual files written in the KQuery language—the input language of the Kleaver constraint solver used by KLEE. In order to convert these constraints into Java Boolean expressions, we have developed a JavaCC parser for a relevant subset of the KQuery language (the token definition of the lexical analyzer of our JavaCC parser is shown in [Listing 1](#S0065245817300487_2.xhtml#b0060)). We use this parser to parse the path constraints files as well as the symbolic expressions found in the user-created file “klee-stdout.log”.

Listing 1

The Token Definition of the Lexical Analyzer of Our JavaCC Parser for a Subset of the KQuery Language

*   TOKEN :
*   {
*             < LBR : "(" >
*           | < RBR : ")" >
*           | < QUERY : "query" >
*           | < LSBR : "\[" >
*           | < RSBR : "\]" >
*           | < FALSE : " false" >
*           | < TRUE : " true " >
*           | < VarDeclStart : ("ReadLSB") >
*           | < AEK : ("Add" | "Sub" | "Mul" | "UDiv" | "URem" | "SDiv" | "SRem") >
*           | < CEK : ("Eq" | "Ne" | "Ult" | "Ule" | "Ugt" | "Uge" | " Slt " | " Sle " | "Sgt" | "Sge") >
*           | < type : \["w"\] (\["0"−"9"\])+ >
*           | < identifier : \["a"−"z", "A"−"Z","\_"\] (\["a"−"z","A"−"Z","0"−"9", "\_"\])\*>
*           | < colon : " : " >
*           | < number : (<decConstant> | <signedDecConstant>) >
*           | < signedDecConstant : ("+") | ("−")<decConstant>>
*           | < decConstant : (<digit>)+ >
*           | < digit : \["0"−"9"\] >
*   }

Example 7

In [Listing 2](#S0065245817300487_2.xhtml#b0065) we show an excerpt of the file “TAC.c” that is generated by the component “KLEE Input File Preparation” for transition T2 and its symbolic source state SS4 in [Fig. 23A](#S0065245817300487_2.xhtml#f0110). In [Listings 3](#S0065245817300487_2.xhtml#b0070) and [4](#S0065245817300487_2.xhtml#b0075), we show the two path constraints files generated by KLEE as a result of executing the input file “TAC.c” shown in [Listing 2](#S0065245817300487_2.xhtml#b0065). The Java Boolean expression representation corresponding to each path constraint is shown in [Listings 5](#S0065245817300487_2.xhtml#b0080) and [6](#S0065245817300487_2.xhtml#b0085), respectively. Similarly, the files “TAC-output.txt” and “klee-stdout.log” resulting from executing KLEE on the input file “TAC.c” are shown in [Listings 7](#S0065245817300487_2.xhtml#b0090) and [8](#S0065245817300487_2.xhtml#b0095). The Java expression representation corresponding to the symbolic variables found in the file “klee-stdout.log” in [Listing 8](#S0065245817300487_2.xhtml#b0095) is shown in [Listing 9](#S0065245817300487_2.xhtml#b0100). In [Fig. 23C](#S0065245817300487_2.xhtml#f0110) we show the symbolic transitions ST7 and ST8 and their symbolic target states SS8 and SS9 resulting from the parsing and the extraction step implemented by the component “Feasible Paths Data Extraction” for the files in [Listings 3](#S0065245817300487_2.xhtml#b0070), [4](#S0065245817300487_2.xhtml#b0075), [7](#S0065245817300487_2.xhtml#b0090), and [8](#S0065245817300487_2.xhtml#b0095).

 

Listing 2

Excerpt From TAC.c

*   \# include <stdio . h >
*   \# include <klee / klee . h >
*   int main ()
*   {
*           FILE \* file;
*           // variable declaration and initialization
*           int T1\_1\_a;
*           klee\_make\_symbolic(&T1\_1\_a, sizeof (T1\_1\_a), "T1\_1\_a");
*           int T2\_2\_b;
*           klee\_make\_symbolic(&T2\_2\_b, sizeof (T2\_2\_b), "T2\_2\_b");
*           int x = T1\_1\_a;
*           int y = 0;
*           //user−defined variables to represent output events to be generated
*           char\* output1\_eventName = "";
*           char\* output1\_eventArg\_1 = "";
*           char\* output1\_eventArg\_2 = "";
*           //pre−defined path constraint (PC) declaraion
*           klee\_assume(1==T1\_1\_a);
*           // action code symbolic representation
*           if (T2\_2\_b==x+1) {
*                                y=T2\_2\_b+1;
*           }
*           else {
*                                y=T2\_2\_b+2;
*           }
*           output1\_eventName = "itsEnv . evReportVarsVal";
*           output1\_eventArg\_1 = x;
*           output1\_eventArg\_2 = y;
*           // logging all variables ’ valuation
*           file = fopen (" ./ klee−out−0/TAC−output.txt","a+");
*           fprintf (file, "%s∖n", "Output = ");
*           printf ("%s∖n", "Output = ");
*           if (klee\_is\_symbolic (T1\_1\_a)) {
*                                fprintf (file, "%s∖n", "T1\_1\_a = SYMBOLIC");
*                                klee\_print\_expr ("T1\_1\_a = ", T1\_1\_a);
*           }
*           else {
*                                 fprintf (file, "%s%d∖n", "T1\_1\_a = ", T1\_1\_a);
*           }
*           ∖ ldots
*           if (! (output1\_eventName== "")) {
*                                 fprintf (file, "%s%s∖n", "output1\_eventName = " , output1\_eventName);
*                                 if (klee\_is\_symbolic (output1\_eventArg\_1)) {
*                                                     fprintf (file, "%s∖n", "output1\_eventArg\_1 = SYMBOLIC");
*                                                     klee\_print\_expr ("output1\_eventArg\_1 = ", output1\_eventArg\_1);
*                                }
*                                else if (output1\_eventArg\_1== "")
*                                                    fprintf (file, "%s∖n", "output1\_eventArg\_1 = ");
*                                else
*                                                     fprintf (file, "%s%d∖n", "output1\_eventArg\_1 = ", output1\_eventArg\_1);
*                                 if (klee\_is\_symbolic (output1\_eventArg\_2)) {
*                                                     fprintf (file, "%s∖n", "output1\_eventArg\_2 = SYMBOLIC");
*                                                     klee\_print\_expr ("output1\_eventArg\_2 = ", output1\_eventArg\_2);
*                                }
*                                else if (output1\_eventArg\_2== "")
*                                                     fprintf (file, "%s∖n", "output1\_eventArg\_2 = ");
*                                else
*                                                     fprintf (file, "%s%d∖n", "output1\_eventArg\_2 = ", output1\_eventArg\_2);
*           }
*           fclose (file);
*   }

Listing 3

KLEE Generated KQuery Constraint File Associated With the First Feasible Path of the Code in [Listing 2](#S0065245817300487_2.xhtml#b0065): test000001.pc

*   array T1\_1\_a \[4\] : w32 −> w8 = symbolic
*   array T2\_2\_b \[4\] : w32 −> w8 = symbolic
*   (query \[(Eq 1
*                                (ReadLSB w32 0 T1\_1\_a))
*                       (Eq false
*                                (Eq 2
*                                         (ReadLSB w32 0 T2\_2\_b)))\]
*                     false)

Listing 4

KLEE Generated KQuery Constraint File Associated With the Second Feasible Path of the Code in [Listing 2](#S0065245817300487_2.xhtml#b0065): test000002.pc

*   array T1\_1\_a \[4\] : w32 −> w8 = symbolic
*   array T2\_2\_b \[4\] : w32 −> w8 = symbolic
*   (query \[(Eq 1
*                             (ReadLSB w32 0 T1\_1\_a))
*                     (Eq 2
*                             (ReadLSB w32 0 T2\_2\_b))\]
*                    false)

Listing 5

The Boolean Expressions of the KQuery Path Constraint in [Listing 3](#S0065245817300487_2.xhtml#b0070)

*   (1==T1\_1\_a) && !(2==T2\_2\_b)

Listing 6

The Boolean Expressions of the KQuery Path Constraint in [Listing 4](#S0065245817300487_2.xhtml#b0075)

*   (1==T1\_1\_a) && (2==T2\_2\_b)

Listing 7

User-Created File From Running KLEE on the LLVM Bitcode Representation of File TAC.c: TAC-output.txt

*   Output =
*   T1\_1\_a = SYMBOLIC
*   T2\_2\_b = SYMBOLIC
*   x = SYMBOLIC
*   y = SYMBOLIC
*   output1\_eventName = itsEnv . evReportVarsVal
*   output1\_eventArg\_1 = SYMBOLIC
*   output1\_eventArg\_2 = SYMBOLIC
*   Output =
*   T1\_1\_a = SYMBOLIC
*   T2\_2\_b = SYMBOLIC
*   x = SYMBOLIC
*   y = SYMBOLIC
*   output1\_eventName = itsEnv . evReportVarsVal
*   output1\_eventArg\_1 = SYMBOLIC
*   output1\_eventArg\_2 = SYMBOLIC

Listing 8

User-Created File of the Resulting stdout From Running KLEE on the LLVM Bitcode Representation of File TAC.c: klee-stdout.log

*   KLEE: output directory = " klee−out−0"
*   Output =
*   T1\_1\_a = : (ReadLSB w32 0 T1\_1\_a)
*   T2\_2\_b = : (ReadLSB w32 0 T2\_2\_b)
*   x = : (ReadLSB w32 0 T1\_1\_a)
*   y = : (Add w32 2
*                        (ReadLSB w32 0 T2\_2\_b))
*   output1\_eventArg\_1 = : (ReadLSB w32 0 T1\_1\_a)
*   output1\_eventArg\_2 = : (Add w32 2
*                        (ReadLSB w32 0 T2\_2\_b))
*   Output =
*   T1\_1\_a = : (ReadLSB w32 0 T1\_1\_a)
*   T2\_2\_b = : (ReadLSB w32 0 T2\_2\_b)
*   x = : (ReadLSB w32 0 T1\_1\_a)
*   y = : (Add w32 1
*                        (ReadLSB w32 0 T2\_2\_b))
*   output1\_eventArg\_1 = : (ReadLSB w32 0 T1\_1\_a)
*   output1\_eventArg\_2 = : (Add w32 1
*                        (ReadLSB w32 0 T2\_2\_b))
*   KLEE: done : total instructions = 194
*   KLEE: done : completed paths = 2
*   KLEE: done : generated tests = 2

Listing 9

The Boolean Expressions of the KQuery Path Constraint in [Listing 8](#S0065245817300487_2.xhtml#b0095)

*   T1\_1\_a = T1\_1\_a
*   T2\_2\_b = T2\_2\_b
*   x = T1\_1\_a
*   y = 2 + T2\_2\_b
*   output1\_eventArg\_1 = T1\_1\_a
*   output1\_eventArg\_2 = 2 + T2\_2\_b
*   T1\_1\_a = T1\_1\_a
*   T2\_2\_b = T2\_2\_b
*   x = T1\_1\_a
*   y = 1 + T2\_2\_b
*   output1\_eventArg\_1 = T1\_1\_a
*   output1\_eventArg\_2 = 1 + T2\_2\_b

 

### 6.3 Implementation of the MQL and TGL-Based Transformation Components

Our transformation components are implemented in the context of the IBM Rational Rhapsody Developer RulesComposer Add-On which is an Eclipse-based development environment for model transformation and text generation. In such an environment, a model transformation is defined using an imperative transformation language called MQL. The basic element of a model transformation is a ruleset which is a group of logically interdependent rules, each of which specifies a set of procedural expressions that query source and target model elements to create new elements, update the attributes and the references of existing elements, or launch text generation templates. A model transformation may be implemented using one or more rulesets. Text generation is defined using templates written in a language called the TGL which uses MQL expressions (i.e., placeholders) for dynamic text generation. Scripts are methods written in MQL, TGL, or Java to extend and customize a meta-type of a source or a target meta-model for a particular model transformation or text generation. They are called from MQL and TGL code on model elements in the same way as regular Java methods.

To implement our transformation components, we first defined the meta-model of the CMLMs representation defined in [Section 4](#S0065245817300487_1.xhtml#s0125) as an Ecore model which we show in [Appendix](#S0065245817300487_3.xhtml#s0320). We also imported this Ecore model as a meta-model project that is added to the default set of meta-models defined within the RulesComposer Add-On. Then, we created a RulesComposer project with references to the Rhapsody meta-model which is already defined and integrated within the tool and the CMLMs meta-model that we have defined and imported into the tool. Our implementation of this model transformation and text generation RulesComposer project consists of:

*   • 19 rules grouped into 2 rulesets. The first ruleset groups a set of 17 rules that specify how to flatten and map a Rhapsody source model into a CMLMs target model. The second ruleset groups a set of 2 rules that computes the data and the communication dependencies in a given CMLMs model.
*   • 48 MQL scripts distributed among the following meta-types:  
    *   • 9 scripts for “rhapsody\_Statechart”,
    *   • 21 scripts for “rhapsody\_State”,
    *   • 1 script for “rhapsody\_Transition”,
    *   • 5 scripts for “cmlms\_CMLM”,
    *   • 5 scripts for “cmlms\_MLM”, and
    *   • 7 scripts for “cmlms\_Transition”.
*   • 6 Java scripts equally distributed between the “cmlms\_CMLM” and “cmlms\_MLM” meta-types. We defined these scripts to be able to create specialized ArrayList, HashMap, and HashSet objects to be used within our rules.
*   • 2 TGL templates. These templates are used to generate a Java representation for our CMLMs representations; one for the individual MLMs and one for the communicating MLMs.
*   • 4948 lines of code (LOC) distributed as follows:  
    *   • 2761 LOC for the rulesets,
    *   • 1516 LOC for the MQL scripts,
    *   • 102 LOC for the Java scripts, and
    *   • 568 LOC for the TGL templates.

### 6.4 Interaction With the IBM Rational Rhapsody DiffMerge and Its Related Components

As we decided to use the IBM Rational Rhapsody DiffMerge tool to find the differences between evolving versions of Rhapsody models, we needed to find a way to process and parse the output generated by the tool. Two types of reports can be exported from the tool that summarize the differences found between compared models. The first report is a Rich Text Format (RTF) report and it is designed to contain a greater level of detail but it is not suitable for further processing to extract difference data. On the other hand, the second report is a Comma Separated Values (CSV) format report which is easier to process but it is designed to contain a lower level of detail. In order to extend the information included in the CSV format reports about the difference data, we had to extend the underlying CSV report template of the tool. The default template file we found is called “DiffReport\_csv.dpl” and it is written in a language that is embedded in the IBM Rational Rhapsody ReporterPLUS for generating CSV format reports about the difference data found by the Rhapsody DiffMerge tool.

The original version of this template file contains 156 LOC and it reports only on six specified attributes for a given difference. This includes information about the meta-class of the difference elements, their names, their locations, the difference type indicating whether the difference element is an added element, a deleted element or a modified element, the differences count (i.e., the number of attributes in the difference elements with different values) and whether a difference is a trivial (i.e., nonconflicting) difference or not. This latter feature is mainly used when the three-way comparison with the base unit option is performed. In this case if a difference is found in the two compared units with respect to their base unit, then this difference is a nontrivial (i.e., conflicting) difference which needs manual resolution; the automatic merging operation of the tool cannot resolve nontrivial differences. The merging operation is outside the scope of our work and we do not need the three-way comparison option. Therefore, all the differences reported were trivial differences.

Our adapted version of the same template file contains 205 LOC and it adds three extra attributes to be reported to the original list. These are the names of the attributes in the difference elements with different values and their values in both compared models, namely, the “left value” and the “right value”. Recording the values of these attributes enabled us to uniquely identify specific Rhapsody model elements which may have the same value assigned to their “name” attribute. Transitions are an example of such elements where two or more transitions can have the same name. Users are not allowed to set the value of the “name” attribute of a transition in the IBM Rhapsody tool. Instead, the tool uses the values assigned to the “trigger”, the “guard”, and the “action” attributes of a transition to generate and assign a compound value to its “name” attribute. For the unique identification of transitions in a model, the tool uses an internal global unique identifier number to be assigned to each newly created transition. The attribute that is used for this purpose is a private variable which cannot be accessed by users. We also noticed that the value of the “name” attribute of a difference transition recorded by the Rhapsody DiffMerge tool does not exactly match the value recorded for the attribute “name” of the same transition in the corresponding Rhapsody Statechart model. Only the “trigger” and the “guard” parts of the name of a transition are used by the Rhapsody DiffMerge tool to report the name of a difference transition. This information alone is not enough to uniquely identify a transition in a model especially in the case of poorly designed Statecharts that may have nondeterministic transitions. Therefore, we believe that the addition we have made to the default CSV report template of the Rhapsody DiffMerge tool was mandatory and it enabled us to uniquely identify the difference elements reported including states and transitions.

Given our adapted CSV format difference reports, the next step for us was to develop a parser such that all the difference information recorded in a given CSV difference report are mapped to our user-defined data structure objects. We use this parsed information and the MLM or CMLMs representations of compared Rhapsody models as the inputs to components “SC2MLM DiffMap” and “RhapM2CMLMs” in order to map the identified difference elements in the compared Rhapsody models into their MLM or CMLMs correspondences. The generated difference report from either of the two aforementioned components is used as an input to component “Dependency-based Change Impact Analysis” to identify the parts of an input MLM or CMLMs representation that have a data or communication dependence with a difference element in the input difference report. The implementation of the CSV parser, the two DiffMap components and the “Depend-ency-based Change Impact Analysis” component are all built as a Java project in the context of the IBM Rational Rhapsody RulesComposer Add-On. The project consists of 10 Java classes and approximately 1581 lines of code (LOC).

### 6.5 Summary

In this section we have provided an overview of the implementation of the architectures presented in the previous sections, showing the operating systems required and the technologies used and how we realized the interaction between the different components to fulfill the required tasks.

## 7 Evaluation

In this section we present the evaluation of the effectiveness of the two proposed optimization techniques: MSE and DSE, on both individual Statecharts and communicating Statecharts. We first state the research questions considered in our evaluation. Second, we list the set of artifacts used as case studies for individual and communicating Statecharts. Third, we describe the evaluation setup. Finally we discuss the results and draw conclusions.

It is worth mentioning that we performed our evaluation in two stages. The first stage considered the evaluation of individual Statecharts, while the second stage considered the evaluation of communicating Statecharts. In the first stage we consider only modification changes, while in the second stage we consider also addition and deletion changes.

### 7.1 Research Questions and Variables of Interest

We consider the following three research questions:

*   – RQ1. How effective are our optimizations (i.e., how much do they reduce the resource requirements of the symbolic execution of a changed state machine model) compared to standard SE of a changed Statechart model?  
    For RQ1, we consider the following three correlated variables: (1) the time taken to run each technique, (2) the number of symbolic states, and (3) the number of execution paths in the resulting SETs.
*   – RQ2. Does the SET generated from MSE match the one generated from standard SE?  
    For RQ2, we compare the total number of symbolic states in the SETs resulting from standard SE and MSE. We also perform manual inspection of a subset of the two SETs to ensure their equivalence.
*   – RQ3. Which aspects influence the effectiveness of each technique?  
    For RQ3, we consider the following two aspects: (1) change impact and (2) model characteristics.  
    To measure the impact of the change, we consider the following two criteria:  
     
    
    1.  (1) we define a change impact metric (CIM) as the percentage of the maximal paths of the MLM model involving the change. The lower the value of this metric is, the lower the impact of the change on the model and the higher the opportunity to benefit from a previous analysis results, and vice versa. This metric is used only for individual Statecharts (i.e., it is applied only on the AQS, LGS, and ACCS models) where the notion of maximal path is defined and, thus, can be computed.
    2.  (2) we identify the type of the change applied to create each modified version of the subject models. The change types we consider are modification (M), addition (A), and deletion (D).
    
      
    For model characteristics, we identify the following two metrics that appear likely to have an impact on the effectiveness of DSE:  
    
    1.  (1) the number of transitions in the subject model with multipath guards or action code.
    2.  (2) the number of transitions that have a dependency with other transitions in the model.
    
      
    We speculate that the change impact is a better predictor for the effectiveness of MSE, whereas the model characteristics are more suitable as indicators of the effectiveness of DSE.

### 7.2 Case Study Artifacts

To evaluate the effectiveness of our optimization techniques on both individual and communicating Statecharts, the following artifacts are selected:

1.  (1) For individual Statecharts: We chose three industrial-sized models from the automotive domain. The first model, the Air Quality System (AQS), is a proprietary model that we obtained from our industrial partner that is responsible for air purification in the vehicle's cabin. The second and the third models, the Lane Guide System (LGS) and the Adaptive Cruise Control System (ACCS), are nonproprietary models designed at the University of Waterloo \[[96](#S0065245817300487_3.xhtml#bb0485)\]. The LGS is an automotive feature used to avoid unintentional lane departure by providing alerts when certain events occur. The ACCS is an automotive feature used to automatically maintain the speed of a vehicle set by the driver through the automatic operation of the vehicle. The three models were developed as Simulink/Stateflow models and we manually converted them to behaviorally equivalent Rhapsody Statecharts. [Table 2a](#S0065245817300487_2.xhtml#t0015) summarizes the characteristics of the three models and their MLM representations, including the two model characteristics metrics used to answer RQ3. The models contain 4, 7, and 3 variables of type integer, respectively.
2.  (2) For communicating Statecharts: We used an adapted version of a system model implementing a well-known communication protocol called full-duplex alternating protocol (FABP) found in \[[97](#S0065245817300487_3.xhtml#bb0490)\]. The model consists of three communicating objects: Transmitter, Receiver, and Buffer. The behavior of each object is modeled as a Statechart. A summary of the number of states and transitions in each state machine is shown in [Table 2b](#S0065245817300487_2.xhtml#t0015). We also listed the values of the model characteristics metrics, namely, the number of transitions with multipath action in each Statechart and the number of transition with data or communication dependencies. There are four integer variables in this model.

 

Table 2

 Characteristics of the Artifacts Used in Our Evaluation 

 
| (a) Three individual Statecharts models  |
| --- |
| Numbers of || Air Quality System (AQS) || Lane Guide System (LGS) || Adaptive Cruise Control System (ACCS) |
| Rhapsody Statechart (Before Flattening) || MLM (After Flattening) || Rhapsody Statechart (before flattening) || MLM (after flattening) || Rhapsody Statechart (Before Flattening) || MLM (after flattening) |
| Concurrent regions || 1 || 1 || 1 || 1 || 2 || 1 |
| --- | --- | --- | --- | --- | --- | --- |
| Hierarchical levels || 3 || 1 || 3 || 1 || 3 || 1 || 1 |
| States || 3 CS+14 SS || 14 SS || 2 CS+10 SS || 10 SS || 2 CS+6 SS || 3 SS || 19 SS |
| Transitions || 8 GT+22 ST || 55 ST || 6 GT+16 ST || 40 ST || 9 GT+5 ST || 9 ST || 73 ST |
| Transitions with multipath guards or action code || 5 ST || 5 ST || 2 GT || 10 ST || 1 ST || 0 || 1 ST |
| Transitions with data dependencies || 3 ST || 3 ST || 0 || 0 || 2 GT+2 ST || 4 ST || 16 ST |
| CS, composite state; GT, group transition; SS, simple state; ST, simple transition. |
| (b) One Communicating Statecharts Model |
| Full-Duplex Alternating Bit Protocol (FABP) |
| Numbers of || Transmitter (Trans) || Receiver (Rcv) || Buffer (Buff) |
| Rhapsody Statechart (before flattening) || MLM (after flattening) || Rhapsody Statechart (before flattening) || MLM (after flattening) || Rhapsody Statechart (Before Flattening) || MLM (after flattening) |
| Concurrent regions || 1 || 1 || 1 || 1 || 1 || 1 |
| Hierarchical levels || 1 || 1 || 1 || 1 || 1 || 1 |
| States || 4 SS || 4 SS || 4 SS || 4 SS || 2 SS || 2 SS |
| Transitions || 14 ST || 14 ST || 14 ST || 14 ST || 4 ST || 4 ST |
| Transitions with multipath guards or action code || 0 || 0 || 6 ST || 6 ST || 0 || 0 |
| Transitions with data dependencies || 8 ST || 8 ST || 0 || 0 || 0 || 0 |
| Transitions with communication dependencies || 10 ST || 10 ST || 4 ST || 4 ST || 4 ST || 4 ST |
| SS, simple State; ST, simple transition. |

![t0015](images/S0065245817300487/t0015.png)

### 7.3 Evaluation Setup

To perform our study, we followed the following procedures:

1.  (1) For individual Statecharts: We first prepared a set of different versions for each artifact: the base version and a number of modified versions. Each modified version introduces a single change to one simple or group transition in the base version. Each change is made in the form of an alteration to the event name or the addition of a send event statement to the action code of the subject transition. The main reason for selecting these specific types of changes is to keep the number of modified models manageable and to facilitate the manual correctness check of the results. Another important reason is that some of the tools used in the implementation (e.g., the IBM Rhapsody DiffMerge) do not have command line access which made it impossible to fully automate the collection of the performance data and evaluate the techniques more comprehensively using, e.g., a large number of automatically modified models. The total numbers of the modified versions created for each model are 26 for the AQS model, 19 of the LGS, and 19 for the ACCS model.  
    For each modified version, we first recorded the following information: (1) the change ID ^([⁷](#fn7))
2.  (2) For communicating Statecharts: We followed the same procedure described above for individual Statecharts; however, here we prepared three sets of different versions of the base version of the FABP model. Each set has 32 modified versions with an added transition, a deleted transition, or a modified transition. All changes in the modified versions are atomic. However, they cover all the transitions in the FABP model. For each model version, we recorded the same information listed earlier except the information about the CIM metric which is not applicable for communicating Statecharts. We ran our standard SE and the MSE on all versions, while we ran the DSE only on the versions where the change is found to not impact all of the multipath transitions in the model. Performing the DSE on a model version with a change that has an impact on all multipath transitions will result in no savings compared to performing the standard SE on the same model. For each run, we recorded the same information listed earlier about the characteristics of the generated GSETs.

The characteristics of the SETs generated from running the standard SE on the base versions of the AQS, LGS, ACCS, and FABP models are shown in [Table 3](#S0065245817300487_3.xhtml#t0020). They include the time taken to run the standard SE technique and the number of symbolic states and execution paths in the resulting SETs.

 

Table 3

Performance of Standard SE on the Base Version of the Four Models: AQS, LGS, ACCS, and FABP

 
| SET/GSET Characteristics || Air Quality System (AQS) || Lane Guide System (LGS) || Adaptive Cruise Control System (ACCS) || Full-Duplex Alternating Bit Protocol (FABP) |
| --- | --- | --- | --- | --- |
| Time (min) || ≈ 10 || ≈ 5 || ≈ 9 || ≈ 14 |
| --- | --- | --- | --- | --- |
| No. symbolic states || 6039 || 1769 || 3492 || 2805 |
| No. execution paths || 5019 || 1325 || 2855 || 1342 |

![t0020](images/S0065245817300487/t0020.png)

[Tables 4](#S0065245817300487_3.xhtml#t0025), [5](#S0065245817300487_3.xhtml#t0030), and [6](#S0065245817300487_3.xhtml#t0035) summarize the results of running the three symbolic execution techniques on the modified versions of the AQS, the LGS, and the ACCS models, respectively. Additionally, a summary of the results for the versions of each change type of the FABP model is depicted in [Tables 7](#S0065245817300487_3.xhtml#t0040), [8](#S0065245817300487_3.xhtml#t0045), and [9](#S0065245817300487_3.xhtml#t0050), respectively.

 

Table 4

 Results of MSE and DSE on the AQS Example 

 
|  || Change Information ||  ||  |
| --- | --- | --- | --- |
|  || MLM || SE:MSE || SE:DSE |
| Ver. || Change ID/No. of Changed Transitions || No. of Multipath Impacted Transitions || CIM \[0, 100\] || Time || No. of New Symbolic States || No. of Total Symbolic States || No. of New Execution Paths || No. of Total Execution Paths || Time || No. of Total Symbolic States || No. of Total Execution Paths |
| V1 || M\[AQS-06\]/7 || 0 || 30 || 1:0.3 || 1:0.08 || 1:1 || 1:0.08 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| V2 || M\[AQS-27\]/1 || 0 || 4 || 1:0.3 || 1:0.36 || 1:1 || 1:0.36 || 1:1 || 1:0.01 || 1:0.03 || 1:0.02 |
| V3 || M\[AQS-07\]/1 || 0 || 100 || 1:0.51 || 1:1 || 1:1 || 1:1 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V4 || M\[AQS-09\]/1 || 0 || 20 || 1:0.26 || 1:0.23 || 1:1 || 1:0.23 || 1:1 || 1:0.02 || 1:0.04 || 1:0.03 |
| V5 || M\[AQS-10\]/1 || 1 || 30 || 1:0.21 || 1:0.01 || 1:1 || 1:0.01 || 1:1 || 1:0.02 || 1:0.14 || 1:0.13 |
| V6 || M\[AQS-08\]/1 || 1 || 90 || 1:0.44 || 1:0.64 || 1:1 || 1:0.66 || 1:1 || 1:0.02 || 1:0.14 || 1:0.13 |
| V7 || M\[AQS-28\]/1 || 1 || 0 || 1:0.23 || 1:0.06 || 1:1 || 1:0.06 || 1:1 || 1:0.02 || 1:0.14 || 1:0.13 |
| V8 || M\[AQS-29\]/1 || 0 || 30 || 1:0.27 || 1:0.23 || 1:1 || 1:0.23 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V9 || M\[AQS-11\]/1 || 0 || 0 || 1:0.19 || 1:0 || 1:1 || 1:0 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V10 || M\[AQS-12\]/1 || 0 || 40 || 1:0.24 || 1:0.23 || 1:1 || 1:0.23 || 1:1 || 1:0.02 || 1:0.04 || 1:0.03 |
| V11 || M\[AQS-13\]/1 || 0 || 30 || 1:0.2 || 1:0.06 || 1:1 || 1:0.06 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V12 || M\[AQS-14\]/1 || 0 || 1 || 1:0.22 || 1:0.02 || 1:1 || 1:0.02 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V13 || M\[AQS-04\]/5 || 0 || 97 || 1:0.64 || 1:0.87 || 1:1 || 1:0.91 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V14 || M\[AQS-05\]/7 || 0 || 30 || 1:0.38 || 1:0.39 || 1:1 || 1:0.43 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V15 || M\[AQS-15\]/1 || 0 || 94 || 1:0.41 || 1:0.61 || 1:1 || 1:0.64 || 1:1 || 1:0.02 || 1:0.17 || 1:0.16 |
| V16 || M\[AQS-16\]/1 || 0 || 14 || 1:0.22 || 1:0.01 || 1:1 || 1:0.02 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V17 || M\[AQS-17\]/5 || 0 || 14 || 1:0.29 || 1:0.15 || 1:1 || 1:0.17 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V18 || M\[AQS-18\]/5 || 0 || 42 || 1:0.22 || 1:0.06 || 1:1 || 1:0.06 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V19 || M\[AQS-20\]/1 || 0 || 35 || 1:0.21 || 1:0.01 || 1:1 || 1:0.01 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| V20 || M\[AQS-21\]/1 || 0 || 48 || 1:0.32 || 1:0.41 || 1:1 || 1:0.42 || 1:1 || 1:0.01 || 1:0.03 || 1:0.02 |
| V21 || M\[AQS-22\]/1 || 0 || 27 || 1:0.22 || 1:0.01 || 1:1 || 1:0.01 || 1:1 || 1:0.01 || 1:0.03 || 1:0.02 |
| V22 || M\[AQS-23\]/1 || 0 || 2 || 1:0.21 || 1:0 || 1:1 || 1:0 || 1:1 || 1:0.01 || 1:0.03 || 1:0.02 |
| V23 || M\[AQS-24\]/1 || 0 || 35 || 1:0.29 || 1:0.41 || 1:1 || 1:0.41 || 1:1 || 1:0.01 || 1:0.03 || 1:0.02 |
| V24 || M\[AQS-25\]/1 || 0 || 14 || 1:0.2 || 1:0.03 || 1:1 || 1:0.03 || 1:1 || 1:0.01 || 1:0.03 || 1:0.02 |
| V25 || M\[AQS-26\]/1 || 0 || 25 || 1:0.3 || 1:0.4 || 1:1 || 1:0.4 || 1:1 || 1:0.01 || 1:0.03 || 1:0.02 |
| V26 || M\[AQS-03\]/5 || 0 || 2 || 1:0.28 || 1:0.09 || 1:1 || 1:0.08 || 1:1 || 1:0.02 || 1:0.03 || 1:0.02 |
| Average savings || 71.0% || 75.5% ||  || 74.9% ||  || 98.4% || 95.6% || 96.1% |
| Standard deviation || 10.9% || 28.0% ||  || 28.8% ||  || 0.2% || 4.4% || 4.2% |
| CORREL(CIM) || −0.81 || −0.83 ||  || −0.84 ||  || −0.21 || −0.33 || −0.33 |

![t0025](images/S0065245817300487/t0025.png)

 

Table 5

 Results of MSE and DSE on the LGS Example 

 
| Ver.  || Change Information ||  ||  |
| --- | --- | --- | --- |
|  || MLM || SE:MSE || SE:DSE |
|  || Change ID/No. of Changed Transitions || No. of Multipath Impacted Transitions || CIM \[0, 100\] || Time || No. of New Symbolic States || No. of Total Symbolic States || No. of New Execution Paths || No. of Total Execution Paths || Time || No. of Total Symbolic States || No. of Total Execution Paths |
| V1 || M\[LGS-01\]/1 || 0 || 100 || 1:0.81 || 1:1 || 1:1 || 1:1 || 1:1 || 1:0.28 || 1:0.3 || 1:0.3 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| V2 || M\[LGS-02\]/7 || 0 || 28 || 1:0.19 || 1:0.25 || 1:1 || 1:0.33 || 1:1 || 1:0.25 || 1:0.3 || 1:0.3 |
| V3 || M\[LGS-05\]/7 || 0 || 28 || 1:0.19 || 1:0.25 || 1:1 || 1:0.33 || 1:1 || 1:0.3 || 1:0.3 || 1:0.3 |
| V4 || M\[LGS-09\]/1 || 0 || 97 || 1:0.74 || 1:1 || 1:1 || 1:1 || 1:1 || 1:0.23 || 1:0.3 || 1:0.3 |
| V5 || M\[LGS-08\]/4 || 0 || 13 || 1:0.38 || 1:0.5 || 1:1 || 1:0.5 || 1:1 || 1:0.22 || 1:0.47 || 1:0.47 |
| V6 || M\[LGS-06\]/1 || 0 || 13 || 1:0.47 || 1:0.58 || 1:1 || 1:0.59 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V7 || M\[LGS-07\]/5 || 0 || 40 || 1:0.55 || 1:0.74 || 1:1 || 1:0.74 || 1:1 || 1:0.22 || 1:0.73 || 1:0.73 |
| V8 || M\[LGS-11\]/1 || 0 || 22 || 1:0.24 || 1:0.27 || 1:1 || 1:0.27 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V9 || M\[LGS-13\]/1 || 0 || 22 || 1:0.25 || 1:0.27 || 1:1 || 1:0.27 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V10 || M\[LGS-19\]/1 || 0 || 22 || 1:0.3 || 1:0.27 || 1:1 || 1:0.27 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V11 || M\[LGS-20\]/1 || 0 || 22 || 1:0.28 || 1:0.27 || 1:1 || 1:0.27 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V12 || M\[LGS-12\]/1 || 0 || 3 || 1:0.09 || 1:0.04 || 1:1 || 1:0.04 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V13 || M\[LGS-15\]/1 || 0 || 13 || 1:0.14 || 1:0.12 || 1:1 || 1:0.12 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V14 || M\[LGS-10\]/1 || 0 || 3 || 1:0.09 || 1:0.04 || 1:1 || 1:0.04 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V15 || M\[LGS-14\]/1 || 0 || 13 || 1:0.15 || 1:0.12 || 1:1 || 1:0.12 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V16 || M\[LGS-16\]/1 || 0 || 13 || 1:0.18 || 1:0.12 || 1:1 || 1:0.12 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V17 || M\[LGS-21\]/1 || 0 || 3 || 1:0.09 || 1:0.04 || 1:1 || 1:0.04 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V18 || M\[LGS-17\]/1 || 0 || 13 || 1:0.16 || 1:0.12 || 1:1 || 1:0.12 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| V19 || M\[LGS-18\]/1 || 0 || 3 || 1:0.09 || 1:0.04 || 1:1 || 1:0.04 || 1:1 || 1:0.22 || 1:0.3 || 1:0.3 |
| Average savings || 71.7% || 68.2% ||  || 67.2% ||  || 76.7% || 67.0% || 66.6% |
| Standard deviation || 21.6% || 30.6% ||  || 30.5% ||  || 2.2% || 10.5% || 10.4% |
| CORREL(M) || −0.89 || −0.88 ||  || −0.89 ||  || −0.48 || −0.09 || −0.08 |

![t0030](images/S0065245817300487/t0030.png)

 

Table 6

 Results of MSE and DSE on the ACCS Example 

 
| Ver.  || Change Information ||  ||  |
| --- | --- | --- | --- |
|  || MLM || SE:MSE || SE:DSE |
|  || Change ID/No. of Changed Transitions || No. of Multipath Impacted Transitions || CIM \[0, 100\] || Time || No. of New Symbolic States || No. of Total Symbolic States || No. of New Execution Paths || No. of Total Execution Paths || Time || No. of Total Symbolic States || No. of Total Execution Paths |
| V1 || M\[ACCS-04\]/1 || 0 || 100 || 1:0.82 || 1:1 || 1:1 || 1:1 || 1:1 || 1:1.05 || 1:0.92 || 1:0.9 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| V2 || M\[ACCS-05\]/12 || 0 || 30 || 1:0.21 || 1:0.17 || 1:1 || 1:0.17 || 1:1 || 1:0.79 || 1:0.92 || 1:0.9 |
| V3 || M\[ACCS-06\]/12 || 0 || 30 || 1:0.19 || 1:0.15 || 1:1 || 1:0.17 || 1:1 || 1:0.78 || 1:0.92 || 1:0.9 |
| V4 || M\[ACCS-19\]/2 || 0 || 2 || 1:0.61 || 1:0.79 || 1:1 || 1:0.8 || 1:1 || 1:1.02 || 1:0.92 || 1:0.9 |
| V5 || M\[ACCS-20\]/2 || 0 || 2 || 1:0.43 || 1:0.44 || 1:1 || 1:0.46 || 1:1 || 1:1 || 1:0.92 || 1:0.9 |
| V6 || M\[ACCS-13\]/2 || 0 || 60 || 1:0.73 || 1:0.87 || 1:1 || 1:0.87 || 1:1 || 1:1.02 || 1:0.92 || 1:0.9 |
| V7 || M\[ACCS-14\]/2 || 0 || 60 || 1:0.45 || 1:0.55 || 1:1 || 1:0.55 || 1:1 || 1:1.02 || 1:0.92 || 1:0.9 |
| V8 || M\[ACCS-15\]/2 || 0 || 20 || 1:0.56 || 1:0.76 || 1:1 || 1:0.77 || 1:1 || 1:1.03 || 1:0.92 || 1:0.9 |
| V9 || M\[ACCS-16\]/2 || 0 || 20 || 1:0.24 || 1:0.18 || 1:1 || 1:0.2 || 1:1 || 1:1.03 || 1:0.92 || 1:0.9 |
| V10 || M\[ACCS-17\]/4 || 0 || 36 || 1:0.14 || 1:0.05 || 1:1 || 1:0.04 || 1:1 || 1:1.04 || 1:0.92 || 1:0.9 |
| V11 || M\[ACCS-18\]/4 || 0 || 36 || 1:0.26 || 1:0.2 || 1:1 || 1:0.18 || 1:1 || 1:1.04 || 1:0.92 || 1:0.9 |
| V12 || M\[ACCS-07\]/1 || 1 || 99 || 1:0.81 || 1:1 || 1:1 || 1:1 || 1:1 || 1:1.02 || 1:1 || 1:1 |
| V13 || M\[ACCS-08\]/6 || 0 || 14 || 1:0.27 || 1:0.22 || 1:1 || 1:0.19 || 1:1 || 1:1.02 || 1:0.92 || 1:0.9 |
| V14 || M\[ACCS-09\]/1 || 1 || 11 || 1:0.59 || 1:0.67 || 1:1 || 1:0.68 || 1:1 || 1:0.87 || 1:1 || 1:1 |
| V15 || M\[ACCS-21\]/1 || 0 || 11 || 1:0.11 || 1:0.01 || 1:1 || 1:0.01 || 1:1 || 1:0.99 || 1:0.92 || 1:0.9 |
| V16 || M\[ACCS-11\]/3 || 0 || 83 || 1:0.73 || 1:0.87 || 1:1 || 1:0.88 || 1:1 || 1:1 || 1:0.92 || 1:0.9 |
| V17 || M\[ACCS-12\]/3 || 1 || 30 || 1:0.23 || 1:0.17 || 1:1 || 1:0.2 || 1:1 || 1:0.99 || 1:1 || 1:1 |
| V18 || M\[ACCS-10\]/6 || 0 || 31 || 1:0.63 || 1:0.72 || 1:1 || 1:0.73 || 1:1 || 1:1.02 || 1:0.92 || 1:0.9 |
| V19 || M\[ACCS-22\]/6 || 0 || 31 || 1:0.17 || 1:0.09 || 1:1 || 1:0.12 || 1:1 || 1:1.02 || 1:0.92 || 1:0.9 |
| Average savings || 56.9% || 53.2% ||  || 52.6% ||  || 1.4% || 7.0% || 8.6% |
| Standard deviation || 24.6% || 35.0% ||  || 35.1% ||  || 8.0% || 3.1% || 3.8% |
| CORREL(CIM) || −0.59 || −0.56 ||  || −0.56 ||  || −0.22 || −0.14 || −0.14 |

![t0035](images/S0065245817300487/t0035.png)

 

Table 7

 Results of MSE and DSE on the Versions of the FABP Example With Modification Changes 

 
| Ver.  || Change Information ||  ||  |
| --- | --- | --- | --- |
|  || CMLM || SE:MSE || SE:DSE |
|  || Change ID/No. of Changed Transitions || No. of Multipath Impacted Transitions || Time || No. of New Symbolic States || No. of Total Symbolic States || No. of New Execution Paths || No. of Total Execution Paths || Time || No. of Total Symbolic States || No. of Total Execution Paths |
| V1 || M\[Buff-01\]/1 || 0 || 1:0.71 || 1:0.77 || 1:1 || 1:0.78 || 1:1 || 1:0.03 || 1:0.03 || 1:0.04 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| V2 || M\[Buff-02\]/1 || 6 || 1:0.69 || 1:0.76 || 1:0.98 || 1:0.77 || 1:0.99 || 1:1 || 1:1 || 1:1 |
| V3 || M\[Buff-03\]/1 || 0 || 1:0.13 || 1:0.05 || 1:1 || 1:0.05 || 1:1 || 1:0.03 || 1:0.03 || 1:0.04 |
| V4 || M\[Buff-04\]/1 || 6 || 1:0.57 || 1:0.56 || 1:1 || 1:0.62 || 1:1 || 1:1 || 1:1 || 1:1 |
| V5 || M\[Rcv-01\]/1 || 6 || 1:0.19 || 1:0.17 || 1:1 || 1:0.18 || 1:1 || 1:1 || 1:1 || 1:1 |
| V6 || M\[Rcv-02\]/1 || 6 || 1:0.44 || 1:0.5 || 1:1 || 1:0.49 || 1:1 || 1:1 || 1:1 || 1:1 |
| V7 || M\[Rcv-03\]/1 || 6 || 1:0.37 || 1:0.38 || 1:1 || 1:0.39 || 1:1 || 1:1 || 1:1 || 1:1 |
| V8 || M\[Rcv-04\]/1 || 6 || 1:0.27 || 1:0.3 || 1:1 || 1:0.31 || 1:1 || 1:1 || 1:1 || 1:1 |
| V9 || M\[Rcv-05\]/1 || 6 || 1:0.2 || 1:0.17 || 1:1 || 1:0.18 || 1:1 || 1:1 || 1:1 || 1:1 |
| V10 || M\[Rcv-06\]/1 || 6 || 1:0.41 || 1:0.38 || 1:1 || 1:0.38 || 1:1 || 1:1 || 1:1 || 1:1 |
| V11 || M\[Rcv-07\]/1 || 6 || 1:0.42 || 1:0.45 || 1:1 || 1:0.44 || 1:1 || 1:1 || 1:1 || 1:1 |
| V12 || M\[Rcv-08\]/1 || 6 || 1:0.68 || 1:0.73 || 1:1 || 1:0.72 || 1:1 || 1:1 || 1:1 || 1:1 |
| V13 || M\[Rcv-09\]/1 || 6 || 1:0.64 || 1:0.76 || 1:1 || 1:0.75 || 1:1 || 1:1 || 1:1 || 1:1 |
| V14 || M\[Rcv-10\]/1 || 0 || 1:0.16 || 1:0.08 || 1:1 || 1:0.11 || 1:1 || 1:0.03 || 1:0.03 || 1:0.04 |
| V15 || M\[Rcv-11\]/1 || 0 || 1:0.34 || 1:0.28 || 1:0.98 || 1:0.27 || 1:0.98 || 1:0.03 || 1:0.03 || 1:0.04 |
| V16 || M\[Rcv-12\]/1 || 0 || 1:0.29 || 1:0.23 || 1:0.99 || 1:0.23 || 1:0.99 || 1:0.03 || 1:0.03 || 1:0.04 |
| V17 || M\[Rcv-13\]/1 || 0 || 1:0.47 || 1:0.5 || 1:0.7 || 1:0.51 || 1:0.71 || 1:0.03 || 1:0.03 || 1:0.04 |
| V18 || M\[Rcv-14\]/1 || 6 || 1:0.63 || 1:0.7 || 1:1 || 1:0.7 || 1:1 || 1:1 || 1:1 || 1:1 |
| V19 || M\[Trans-01\]/1 || 6 || 1:0.55 || 1:0.7 || 1:0.7 || 1:0.71 || 1:0.71 || 1:1 || 1:1 || 1:1 |
| V20 || M\[Trans-02\]/1 || 6 || 1:0.74 || 1:0.88 || 1:0.98 || 1:0.89 || 1:0.99 || 1:1 || 1:1 || 1:1 |
| V21 || M\[Trans-03\]/1 || 6 || 1:0.12 || 1:0.01 || 1:1 || 1:0.02 || 1:1 || 1:1 || 1:1 || 1:1 |
| V22 || M\[Trans-04\]/1 || 6 || 1:0.43 || 1:0.44 || 1:1 || 1:0.41 || 1:1 || 1:1 || 1:1 || 1:1 |
| V23 || M\[Trans-05\]/1 || 6 || 1:0.58 || 1:0.64 || 1:1 || 1:0.63 || 1:1 || 1:1 || 1:1 || 1:1 |
| V24 || M\[Trans-06\]/1 || 6 || 1:0.12 || 1:0.01 || 1:1 || 1:0.01 || 1:1 || 1:1 || 1:1 || 1:1 |
| V25 || M\[Trans-07\]/1 || 6 || 1:0.88 || 1:0.99 || 1:1 || 1:0.99 || 1:1 || 1:1 || 1:1 || 1:1 |
| V26 || M\[Trans-08\]/1 || 6 || 1:0.77 || 1:0.83 || 1:1 || 1:0.85 || 1:1 || 1:1 || 1:1 || 1:1 |
| V27 || M\[Trans-09\]/1 || 6 || 1:0.29 || 1:0.27 || 1:1 || 1:0.27 || 1:1 || 1:1 || 1:1 || 1:1 |
| V28 || M\[Trans-10\]/1 || 6 || 1:0.34 || 1:0.32 || 1:1 || 1:0.33 || 1:1 || 1:1 || 1:1 || 1:1 |
| V29 || M\[Trans-11\]/1 || 6 || 1:0.14 || 1:0.04 || 1:1 || 1:0.04 || 1:1 || 1:1 || 1:1 || 1:1 |
| V30 || M\[Trans-12\]/1 || 6 || 1:0.25 || 1:0.19 || 1:1 || 1:0.16 || 1:1 || 1:1 || 1:1 || 1:1 |
| V31 || M\[Trans-13\]/1 || 6 || 1:0.14 || 1:0.01 || 1:1 || 1:0.01 || 1:1 || 1:1 || 1:1 || 1:1 |
| V32 || M\[Trans-14\]/1 || 6 || 1:0.13 || 1:0.02 || 1:1 || 1:0.04 || 1:1 || 1:1 || 1:1 || 1:1 |
| Average savings || 59.2% || 58.9% ||  || 58.6% ||  || 18.2% || 18.1% || 18.0% |
| Standard deviation || 22.7% || 29.8% ||  || 29.8% ||  || 38.5% || 38.3% || 38.2% |

![t0040](images/S0065245817300487/t0040.png)

 

Table 8

 Results of MSE and DSE on the Versions of the FABP Example With Addition Changes 

 
| Ver.  || Change Information ||  ||  |
| --- | --- | --- | --- |
|  || CMLM || SE:MSE || SE:DSE |
|  || Change ID/No. of Changed Transitions || No. of Multipath Impacted Transitions || Time || No. of New Symbolic States || No. of Total Symbolic States || No. of New Execution Paths || No. of Total Execution Paths || Time || No. of Total Symbolic States || No. of Total Execution Paths |
| V1 || A\[Buff-01\]/1 || 0 || 1:0.72 || 1:0.78 || 1:1 || 1:0.78 || 1:1 || 1:0.03 || 1:0.03 || 1:0.04 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| V2 || A\[Buff-02\]/1 || 6 || 1:0.72 || 1:0.8 || 1:0.98 || 1:0.86 || 1:0.99 || 1:1 || 1:1 || 1:1 |
| V3 || A\[Buff-03\]/1 || 0 || 1:0.13 || 1:0.05 || 1:1 || 1:0.05 || 1:1 || 1:0.03 || 1:0.03 || 1:0.04 |
| V4 || A\[Buff-04\]/1 || 6 || 1:0.53 || 1:0.57 || 1:1 || 1:0.62 || 1:1 || 1:1 || 1:1 || 1:1 |
| V5 || A\[Rcv-01\]/1 || 6 || 1:0.21 || 1:0.17 || 1:1 || 1:0.18 || 1:1 || 1:1 || 1:1 || 1:1 |
| V6 || A\[Rcv-02\]/1 || 6 || 1:0.5 || 1:0.5 || 1:1 || 1:0.49 || 1:1 || 1:1 || 1:1 || 1:1 |
| V7 || A\[Rcv-03\]/1 || 6 || 1:0.41 || 1:0.38 || 1:1 || 1:0.39 || 1:1 || 1:1 || 1:1 || 1:1 |
| V8 || A\[Rcv-04\]/1 || 6 || 1:0.35 || 1:0.3 || 1:1 || 1:0.31 || 1:1 || 1:1 || 1:1 || 1:1 |
| V9 || A\[Rcv-05\]/1 || 6 || 1:0.23 || 1:0.17 || 1:1 || 1:0.18 || 1:1 || 1:1 || 1:1 || 1:1 |
| V10 || A\[Rcv-06\]/1 || 6 || 1:0.4 || 1:0.38 || 1:1 || 1:0.38 || 1:1 || 1:1 || 1:1 || 1:1 |
| V11 || A\[Rcv-07\]/1 || 6 || 1:0.44 || 1:0.45 || 1:1 || 1:0.45 || 1:1 || 1:1 || 1:1 || 1:1 |
| V12 || A\[Rcv-08\]/1 || 6 || 1:0.72 || 1:0.74 || 1:1 || 1:0.73 || 1:1 || 1:1 || 1:1 || 1:1 |
| V13 || A\[Rcv-09\]/1 || 6 || 1:0.71 || 1:0.76 || 1:1 || 1:0.75 || 1:1 || 1:1 || 1:1 || 1:1 |
| V14 || A\[Rcv-10\]/1 || 0 || 1:0.17 || 1:0.09 || 1:1 || 1:0.11 || 1:1 || 1:0.03 || 1:0.03 || 1:0.04 |
| V15 || A\[Rcv-11\]/1 || 0 || 1:0.4 || 1:0.28 || 1:0.98 || 1:0.27 || 1:0.98 || 1:0.03 || 1:0.03 || 1:0.04 |
| V16 || A\[Rcv-12\]/1 || 0 || 1:0.26 || 1:0.18 || 1:0.99 || 1:0.21 || 1:0.99 || 1:0.03 || 1:0.03 || 1:0.04 |
| V17 || A\[Rcv-13\]/1 || 0 || 1:0.48 || 1:0.5 || 1:0.7 || 1:0.51 || 1:0.71 || 1:0.03 || 1:0.03 || 1:0.04 |
| V18 || A\[Rcv-14\]/1 || 6 || 1:0.71 || 1:0.7 || 1:1 || 1:0.7 || 1:1 || 1:1 || 1:1 || 1:1 |
| V19 || A\[Trans-01\]/1 || 6 || 1:0.58 || 1:0.7 || 1:0.7 || 1:0.71 || 1:0.71 || 1:1 || 1:1 || 1:1 |
| V20 || A\[Trans-02\]/1 || 6 || 1:0.83 || 1:0.88 || 1:0.98 || 1:0.89 || 1:0.99 || 1:1 || 1:1 || 1:1 |
| V21 || A\[Trans-03\]/1 || 6 || 1:0.13 || 1:0.01 || 1:1 || 1:0.02 || 1:1 || 1:1 || 1:1 || 1:1 |
| V22 || A\[Trans-04\]/1 || 6 || 1:0.47 || 1:0.44 || 1:1 || 1:0.41 || 1:1 || 1:1 || 1:1 || 1:1 |
| V23 || A\[Trans-05\]/1 || 6 || 1:0.62 || 1:0.64 || 1:1 || 1:0.64 || 1:1 || 1:1 || 1:1 || 1:1 |
| V24 || A\[Trans-06\]/1 || 6 || 1:0.12 || 1:0.01 || 1:1 || 1:0.01 || 1:1 || 1:1 || 1:1 || 1:1 |
| V25 || A\[Trans-07\]/1 || 6 || 1:0.9 || 1:0.99 || 1:1 || 1:0.99 || 1:1 || 1:1 || 1:1 || 1:1 |
| V26 || A\[Trans-08\]/1 || 6 || 1:0.78 || 1:0.83 || 1:1 || 1:0.85 || 1:1 || 1:1 || 1:1 || 1:1 |
| V27 || A\[Trans-09\]/1 || 6 || 1:0.32 || 1:0.27 || 1:1 || 1:0.27 || 1:1 || 1:1 || 1:1 || 1:1 |
| V28 || A\[Trans-10\]/1 || 6 || 1:0.33 || 1:0.33 || 1:1 || 1:0.33 || 1:1 || 1:1 || 1:1 || 1:1 |
| V29 || A\[Trans-11\]/1 || 6 || 1:0.15 || 1:0.04 || 1:1 || 1:0.04 || 1:1 || 1:1 || 1:1 || 1:1 |
| V30 || A\[Trans-12\]/1 || 6 || 1:0.3 || 1:0.19 || 1:1 || 1:0.16 || 1:1 || 1:1 || 1:1 || 1:1 |
| V31 || A\[Trans-13\]/1 || 6 || 1:0.14 || 1:0.01 || 1:1 || 1:0.01 || 1:1 || 1:1 || 1:1 || 1:1 |
| V32 || A\[Trans-14\]/1 || 6 || 1:0.13 || 1:0.02 || 1:1 || 1:0.04 || 1:1 || 1:1 || 1:1 || 1:1 |
| Average Savings || 56.6% || 59.0% ||  || 60.1% ||  || 18.2% || 18.1% || 18.0% |
| Standard Deviation || 23.9% || 30.1% ||  || 29.1% ||  || 38.5% || 38.3% || 38.2% |

![t0045](images/S0065245817300487/t0045.png)

 

Table 9

 Results of MSE and DSE on the Versions of the FABP Example With Deletion Changes 

 
| Ver.  || Change Information ||  ||  |
| --- | --- | --- | --- |
|  || CMLM || SE:MSE || SE:DSE |
|  || Change ID/No. of Changed Transitions || No. of Multipath Impacted Transitions || Time || No. of New Symbolic States || No. of Total Symbolic States || No. of New Execution Paths || No. of Total Execution Paths || Time || No. of Total Symbolic States || No. of Total Execution Paths |
| V1 || D\[Buff-01\]/1 || 0 || 1:0.19 || 1:0.07 || 1:1 || 1:0.06 || 1:1 || 1:0.08 || 1:0.07 || 1:0.08 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| V2 || D\[Buff-02\]/1 || 6 || 1:0.64 || 1:0.61 || 1:1 || 1:0.6 || 1:1 || 1:1 || 1:1 || 1:1 |
| V3 || D\[Buff-03\]/1 || 0 || 1:0.09 || 1:0 || 1:1 || 1:0 || 1:1 || 1:0.03 || 1:0.04 || 1:0.04 |
| V4 || D\[Buff-04\]/1 || 6 || 1:0.18 || 1:0.06 || 1:1 || 1:0.06 || 1:1 || 1:1 || 1:1 || 1:1 |
| V5 || D\[Rcv-01\]/1 || 6 || 1:0.06 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V6 || D\[Rcv-02\]/1 || 6 || 1:0.05 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V7 || D\[Rcv-03\]/1 || 6 || 1:0.06 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V8 || D\[Rcv-04\]/1 || 6 || 1:0.06 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V9 || D\[Rcv-05\]/1 || 6 || 1:0.07 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V10 || D\[Rcv-06\]/1 || 6 || 1:0.05 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V11 || D\[Rcv-07\]/1 || 6 || 1:0.2 || 1:0.14 || 1:1 || 1:0.14 || 1:1 || 1:1 || 1:1 || 1:1 |
| V12 || D\[Rcv-08\]/1 || 6 || 1:0.24 || 1:0.19 || 1:1 || 1:0.19 || 1:1 || 1:1 || 1:1 || 1:1 |
| V13 || D\[Rcv-09\]/1 || 6 || 1:0.57 || 1:0.65 || 1:1 || 1:0.67 || 1:1 || 1:1 || 1:1 || 1:1 |
| V14 || D\[Rcv-10\]/1 || 0 || 1:0.12 || 1:0.12 || 1:1 || 1:0.13 || 1:1 || 1:0.03 || 1:0.04 || 1:0.04 |
| V15 || D\[Rcv-11\]/1 || 0 || 1:0.08 || 1:0.02 || 1:1 || 1:0.02 || 1:1 || 1:0.04 || 1:0.05 || 1:0.05 |
| V16 || D\[Rcv-12\]/1 || 0 || 1:0.2 || 1:0.2 || 1:1 || 1:0.18 || 1:1 || 1:0.03 || 1:0.04 || 1:0.04 |
| V17 || D\[Rcv-13\]/1 || 0 || 1:0.14 || 1:0.1 || 1:1 || 1:0.1 || 1:1 || 1:0.05 || 1:0.05 || 1:0.06 |
| V18 || D\[Rcv-14\]/1 || 6 || 1:0.37 || 1:0.32 || 1:1 || 1:0.32 || 1:1 || 1:1 || 1:1 || 1:1 |
| V19 || D\[Trans-01\]/1 || 6 || 1:0.33 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V20 || D\[Trans-02\]/1 || 6 || 1:0.14 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V21 || D\[Trans-03\]/1 || 6 || 1:0.11 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V22 || D\[Trans-04\]/1 || 6 || 1:0.18 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V23 || D\[Trans-05\]/1 || 6 || 1:0.16 || 1:0.04 || 1:1 || 1:0.03 || 1:1 || 1:1 || 1:1 || 1:1 |
| V24 || D\[Trans-06\]/1 || 6 || 1:0.09 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V25 || D\[Trans-07\]/1 || 6 || 1:0.29 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V26 || D\[Trans-08\]/1 || 6 || 1:0.17 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V27 || D\[Trans-09\]/1 || 6 || 1:0.14 || 1:0.07 || 1:1 || 1:0.09 || 1:1 || 1:1 || 1:1 || 1:1 |
| V28 || D\[Trans-10\]/1 || 6 || 1:0.26 || 1:0.24 || 1:1 || 1:0.24 || 1:1 || 1:1 || 1:1 || 1:1 |
| V29 || D\[Trans-11\]/1 || 6 || 1:0.1 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V30 || D\[Trans-12\]/1 || 6 || 1:0.13 || 1:03 || 1:1 || 1:02 || 1:1 || 1:1 || 1:1 || 1:1 |
| V31 || D\[Trans-13\]/1 || 6 || 1:0.09 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| V32 || D\[Trans-14\]/1 || 6 || 1:0.09 || 1:0 || 1:1 || 1:0 || 1:1 || 1:1 || 1:1 || 1:1 |
| Average savings || 82.3% || 91.0% ||  || 91.1% ||  || 18.0% || 17.9% || 17.8% |
| Standard deviation || 13.9% || 16.5% ||  || 16.6% ||  || 38.0% || 37.9% || 37.7% |

![t0050](images/S0065245817300487/t0050.png)

In columns 5–6, 8 (resp., 10–12) of [Tables 4](#S0065245817300487_3.xhtml#t0025)–[6](#S0065245817300487_3.xhtml#t0035) and columns 4–5, 7 (resp., 9–11) of [Tables 7](#S0065245817300487_3.xhtml#t0040)–[9](#S0065245817300487_3.xhtml#t0050), we show the savings ratios in time, in the number of symbolic states, and in the number of execution paths gained from applying MSE (resp., DSE) on the modified versions of the four given models compared to standard SE. We also show, for each such column, the overall average and the standard deviation. Additionally, we show the correlation coefficient with the CIM metric data in column 4 of [Tables 4](#S0065245817300487_3.xhtml#t0025)–[6](#S0065245817300487_3.xhtml#t0035) for the individual Statecharts models.

The ratios between the total number of symbolic states (resp., execution paths) found in the resulting SETs generated from standard SE and MSE for the four given models are shown in column 7 (resp., 9) of [Tables 4](#S0065245817300487_3.xhtml#t0025)–[6](#S0065245817300487_3.xhtml#t0035) and column 6 (resp., 8) of [Tables 7](#S0065245817300487_3.xhtml#t0040)–[9](#S0065245817300487_3.xhtml#t0050). The values recorded in these four columns are computed with “Task 4” of the MSE [Algorithms 7](#S0065245817300487_2.xhtml#b0040) and [8](#S0065245817300487_2.xhtml#b0045) being enabled and they are used for answering RQ2 with respect to MSE.

Our evaluation is performed on a standard PC with Intel Core i7 CPU 3.4 GHz and 8 GB of RAM and running Windows 7 as a host and Ubuntu 12.04 as VM.

### 7.4 Results and Analysis

In this section, we discuss the results presented in [Tables 4](#S0065245817300487_3.xhtml#t0025)–[9](#S0065245817300487_3.xhtml#t0050) according to our three research questions.

RQ1. How effective are our optimizations compared to standard SE?

In [Table 10](#S0065245817300487_3.xhtml#t0055), we show a summary of the average and the standard deviation values of the data shown in columns 5–6, 8 (resp., 10–12) of [Tables 4](#S0065245817300487_3.xhtml#t0025)–[6](#S0065245817300487_3.xhtml#t0035) and columns 4–5, 7 (resp., 9–11) of [Tables 7](#S0065245817300487_3.xhtml#t0040)–[9](#S0065245817300487_3.xhtml#t0050) corresponding to the amount of savings in the execution times and in the number of symbolic states and execution paths gained from applying our current implementation of MSE (resp., DSE) on all the versions of the four given models. Based on the values presented in this table, we notice the following:

 

Table 10

 Summary of Statistical Measures of the Effectiveness of MSE and DSE for the Four Models: AQS, LGS, ACCS, and FABP With Respect to the Savings in Execution Time and in the Number of Symbolic States and Execution Paths 

 
| (a) Average and Standard Deviation of Savings in Time  |
| --- |
|  || AVG || STDEV |
|  || AQS || LGS || ACCS || FABP || AQS || LGS || ACCS || FABP |
| MSE || 71.0% || 71.7% || 56.9% || 66.0% || 10.9% || 21.6% || 24.6% || 23.5% |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| DSE || 98.4% || 76.7% || 1.4% || 18.1% || 0.2% || 2.2% || 8.0% || 37.9% |
| (b) Average and Standard Deviation of Savings in Number of Symbolic States |
|  || AVG || STDEV |
|  || AQS || LGS || ACCS || FABP || AQS || LGS || ACCS || FABP |
| MSE || 75.5% || 68.2% || 53.2% || 69.6% || 28.0% || 30.6% || 35.0% || 30.1% |
| DSE || 95.6% || 67.0% || 7.0% || 18.0% || 4.4% || 10.5% || 3.1% || 37.7% |
| (c) Average and Standard Deviation of Savings in Number of Execution Paths |
|  || AVG || STDEV |
|  || AQS || LGS || ACCS || FABP || AQS || LGS || ACCS || FABP |
| MSE || 74.9% || 67.2% || 52.6% || 69.3% || 28.8% || 30.5% || 35.1% || 30.3% |
| DSE || 96.1% || 66.6% || 8.6% || 18.0% || 4.2% || 10.4% || 3.8% || 37.6% |

![t0055](images/S0065245817300487/t0055.png)

1.  (1) MSE achieved an average of savings in execution time that ranges from 56.9% (of 9 min) for the ACCS model to 71.7% (of 5 min) for the LGS model, while DSE achieved an average of savings in execution time that approximately ranges from 1.4% (of 9 min) for the ACCS model to 98.4% (of 10 min) for the AQS model. Similarly, MSE achieved an average of savings in the number of symbolic states (resp., execution paths) that ranges from 53.2% (resp., 52.6%) for the ACCS model to 75.5% (resp., 74.9%) for the AQS model, while DSE achieved an average of savings in the number of symbolic states (resp., execution paths) that ranges from 7.0% (resp., 8.6%) for the ACCS model to 95.6% (resp., 96.1%) for the AQS model.
2.  (2) The range of the average values of the achieved savings ratios for DSE is larger than it is for MSE which means that DSE can achieve much higher savings for some models than the others. This shows a higher sensitivity of DSE to the subject models than it is for MSE.
3.  (3) The standard deviation values of the achieved savings ratios for the AQS, LGS, and ACCS models are much higher for MSE than they are for DSE, which means that the effectiveness of MSE for these three models is more influenced by the changes made in each modified model version than it is for the DSE. Interestingly, this observation is reversed for the FABP model.

RQ2. Does the SET generated from MSE match the one generated from standard SE?

The main purpose of this research question is twofold: (1) to ensure the correctness of our MSE algorithms and their implementation and (2) to draw a precise conclusion about the relationship between the SET generated from MSE and the one generated from standard SE. Our initial expectation was that both SETs should be identical; however, the results show that, in some cases, this assumption does not hold.

1.  (1) For individual Statecharts: By looking at the ratios recorded in columns 7 and 9 of [Table 4](#S0065245817300487_3.xhtml#t0025)–[6](#S0065245817300487_3.xhtml#t0035) and our manual inspection, we notice that MSE generated the exact same SETs as standard SE for all versions of the three models: AQS, LGS, and ACCS.
2.  (2) For communicating Statecharts: By looking at the ratios recorded in columns 6 and 8 of [Tables 7](#S0065245817300487_3.xhtml#t0040)–[9](#S0065245817300487_3.xhtml#t0050) and our manual inspection, we notice that MSE generated the exact same GSETs as standard SE for 26 of the 32 FABP model versions with “modification” and “addition” changes and all the FABP model versions with “deletion” changes. However, for all other versions, MSE generated slightly different GSETs. Possible reasons for this are that: (1) the subsumption relation that may exist between the nodes of a SET (resp., GSET) is nonsymmetric and (2) modifying an existing SET (resp., GSET) may change the order of the nodes of the tree as well as the subsumption relation between the nodes. As a result, we may have two semantically equivalent SETs with different numbers of nodes for the same model if the order of generating the nodes of the tree is changed. In [Fig. 24](#S0065245817300487_3.xhtml#f0115) we show an example of two differently sized SETs of the same model resulting from changing the order in which the different branches of the tree have been created. It presents a typical scenario that occurs when running the MSE algorithms where manipulating an already existing SET (resp., GSET) takes place to modify some parts of the tree or to add new ones.

![Fig. 24 An example of two differently sized SETs of the same model, each of which has a different branch order. Note the reduction in the number of nodes in the SET in (B) compared to the one in (A) as a result of the subsumption relation (SR) that is detected in the SET in (B) between node “j” and the previously visited node “l” which cannot exist if the creation order of both nodes is reversed as it is the case in the SET in (A). (A) An example SET where the branch leading to node “c” is created before the branch leading to node “d”. (B) The SET resulting from modifying the SET in (A) such that the branch leading to node “c” is now created after the branch leading to node “d”.](images/S0065245817300487/f04-24-9780128151198.jpg)

Fig. 24 An example of two differently sized SETs of the same model, each of which has a different branch order. Note the reduction in the number of nodes in the SET in (B) compared to the one in (A) as a result of the subsumption relation (SR) that is detected in the SET in (B) between node “j” and the previously visited node “l” which cannot exist if the creation order of both nodes is reversed as it is the case in the SET in (A). (A) An example SET where the branch leading to node “c” is created before the branch leading to node “d”. (B) The SET resulting from modifying the SET in (A) such that the branch leading to node “c” is now created after the branch leading to node “d”.

Based on the results of this research question, we conclude that it is possible in some cases for MSE to generate a SET (resp., GSET) that does not exactly match the one generated from standard SE, yet they are both semantically equivalent.

RQ3. Which aspects influence the effectiveness of each technique?

We summarize the key findings related to the two aforementioned aspects as follows.

1.  (1) For the change impact metric:  
    *   – Change impact measure criterion (applicable only for individual Statecharts models AQS, LGS and ACCS): According to the correlation coefficients computed between the values of columns 5–6, 8, 10–12 and the values of column 4 of [Tables 4](#S0065245817300487_3.xhtml#t0025)–[6](#S0065245817300487_3.xhtml#t0035), we notice that there is high negative correlation between the savings gained from MSE and the CIM metric for the AQS and the LGS models, meaning that in these cases the percentage of maximal paths affected by the change is a good predictor for the effectiveness of MSE. However, it is much lower for the ACCS model and this is due to the discrepancy between the notions of maximal paths and execution paths. A maximal path in a model may correspond to zero, one, or multiple feasible execution paths in the SET of the model depending on the guard condition and the action code of the transitions in the path. This discrepancy grows with the numbers of parallel transitions in the model (i.e., transitions with the same source and target states and guards but different triggers). The ACCS model contains more of these parallel transitions than the AQS and LGS models. We also notice that there is almost no significant correlation between the savings gained from DSE and the CIM metric.
    *   – Type of change criterion (applicable only for communicating Statecharts model FABP): In [Table 11](#S0065245817300487_3.xhtml#t0060), we show a summary of the average and the standard deviation values of the data shown in columns 4–5, 7 (resp., 9–11) of [Tables 7](#S0065245817300487_3.xhtml#t0040)–[9](#S0065245817300487_3.xhtml#t0050) corresponding to the amount of savings in the execution times and in the numbers of symbolic states and execution paths gained from applying MSE (resp., DSE) on the different versions of the FABP model per change type. Based on the values presented in this table, we notice that MSE achieved higher average savings for the versions of the FABP model with deletion changes than for the versions the FABP model with modification and addition changes, while DSE achieved similar average savings for the versions of each change type. This indicates that DSE is less influenced by the type of the changes made to the subject model.
2.  (2) For the model characteristics metrics: By looking at the characteristics of the four models in [Table 2](#S0065245817300487_2.xhtml#t0015) and the summary of the average and the standard deviation values of the amount of savings in the numbers of symbolic states gained for the four models in [Table 10](#S0065245817300487_3.xhtml#t0055), we notice the following:  
    *   – The differences between the average of savings gained among the four used models are not as significant for MSE as they are for DSE. As a result we could not find a clear relationship between the two defined metrics and the savings gained from MSE.
    *   – DSE achieved the least average savings for the ACCS model. This is because ACCS has the least number of multipath transitions which decreases the opportunity for savings from the partial exploration implemented in DSE.
    *   – DSE achieved much higher average savings for both the AQS and LGS models compared with the FABP model. This is because both AQS and LGS have less dependency between their multipath transitions compared with the FABP model which has the highest number of multipath dependent transitions. As we mentioned earlier, a high dependency between multipath transitions in a model decreases the opportunity for savings from the partial exploration implemented in DSE.
    *   – The standard deviation of the savings gained from DSE for the FABP model is the highest among the other models and it is even higher than the average value of the savings. This is because: (1) 78 of the 96 of the FABP versions have changes in transitions that have dependencies with all the multipath transitions in the model and therefore result in 0% savings with DSE and (2) only 18 of the 96 of the FABP versions have changes in transitions that have no dependencies with any of the multipath transitions in the model and therefore result in 96% savings with DSE.

 

Table 11

 Summary of Statistical Measures of the Effectiveness of MSE and DSE for the FABP Model Per Change Type With Respect to the Savings in Time, in the Numbers of Symbolic States and in the Numbers of Execution Paths 

 
| (a) Average and Standard Deviation of Savings in Time  |
| --- |
|  || AVG || STDEV |
|  || FABP || FABP |
|  || Modification || Addition || Deletion || Modification || Addition || Deletion |
| MSE || 59.2% || 56.6% || 82.3% || 22.7% || 23.9% || 13.9% |
| --- | --- | --- | --- | --- | --- | --- |
| DSE || 18.2% || 18.2% || 18.0% || 38.5% || 38.4% || 38.0% |
| (b) Average and Standard Deviation of Savings in Numbers of Symbolic States |
|  || AVG || STDEV |
|  || FABP || FABP |
|  || Modification || Addition || Deletion || Modification || Addition || Deletion |
| MSE || 58.9% || 59.0% || 91.0% || 29.8% || 30.1% || 16.5% |
| DSE || 18.1% || 18.1% || 17.9% || 38.3% || 38.3% || 37.9% |
| (c) Average and Standard Deviation of Savings in Numbers of Execution Paths |
|  || AVG || STDEV |
|  || FABP || FABP |
|  || Modification || Addition || Deletion || Modification || Addition || Deletion |
| MSE || 58.6% || 58.3% || 91.1% || 29.8% || 30.2% || 16.6% |
| DSE || 18.0% || 18.0% || 17.8% || 38.1% || 38.1% || 37.7% |

![t0060](images/S0065245817300487/t0060.png)

Based on the key findings of this research question, we conclude that our optimization techniques are complementary in the sense that the effectiveness of MSE depends mostly on the impact and the type of the change, while the effectiveness of DSE depends more on the numbers of transitions with multipath guards or action code as well as the numbers of transitions with dependencies with each other.

### 7.5 Threats to Validity

Threats to external validity for our evaluation may include (1) the use of KLEE in the implementation of our proposed techniques, (2) the selection of artifacts used in the evaluation, and (3) the types of changes applied to create the modified versions of the used models. Replacing KLEE with any other symbolic execution engine could produce slightly different SETs, depending on the searching strategy employed to explore the different paths of the code been executed, but this should have no impact on the effectiveness of our proposed techniques and rerunning the same evaluation steps with the other symbolic execution engines would mitigate this threat. The artifacts selected for our study are typical behavioral models that can be systematically explored using symbolic execution. The types of changes we used to create the modified versions were selective and may not reflect actual changes; however, rerunning the evaluation on actual model versions would address this threat.

Threats to internal validity may include (1) the originality of the proposed techniques and (2) the correctness of the implementation of our transformation components and proposed algorithms. Although the work presented here is inspired by an already existing work for evolving programs, we are the first to apply it in the context of evolving state-based models. Regarding the correctness of our implementation, we have already tried to address this threat through extensive testing and inspection; more experimentation might allow us to reduce the risk of bugs further.

### 7.6 Summary

In this section we have provided the evaluation of the proposed optimization techniques. We have identified the research questions and the criteria that the evaluation should investigate and the artifacts that we use to perform the evaluation. Three models of hierarchical individual Statecharts as well as one model of three communicating Statecharts are used to evaluate the optimization techniques for each type. An analysis of the results shows a considerable amount of savings resulting from both optimization techniques. In certain versions the savings have reached up to 90+%. The results of MSE have shown its sensitivity to the location and the type of the change made in the models versions, while the results of DSE have shown its sensitivity to the characteristics of the subject models that are related to the existence of multipath transitions in these models that have few dependencies with other transitions.

 

## 8 Conclusion: Summary, Future Work, and Perspective

### 8.1 Summary and Future Work

In this chapter, we have presented two different techniques for optimizing the symbolic execution of evolving Rhapsody Statecharts. The first technique reuses the SET of a previous version of a model to improve the symbolic execution of the current version such that it avoids redundant exploration of common execution paths between the two versions, whereas the second technique uses a change impact analysis to reduce the scope of the exploration to mainly exercise the parts impacted by the change. A key contribution in this work is a proof-of-concept of the feasibility and the effectiveness of the two proposed optimization techniques such that they can be used to speed up the analysis process of such behavioral models as they evolve. The two techniques proposed in this work are applied on both individual and communicating Statecharts and are implemented and integrated in the IBM Rhapsody tool as a set of three external helpers. The first helper represents the transformation components which are built in the context of IBM Rhapsody RulesComposer Add-On and are responsible for (1) flattening a Rhapsody model into our Communicating Mealy-like machines (CMLM) internal representation, (2) compute the data and the communication dependencies in a CMLM and its MLMs, and (3) generate a Java representation of the CMLM representation. The second helper represents the component that is responsible for: (1) mapping a difference report that is generated from the Rhapsody DiffMerge tool to compare between two successive versions of a Rhapsody model into a difference report between the CMLM representation of each version and (2) identifying the impacted elements of each change found in the difference report. The last helper represents our KLEE-based symbolic execution components including standard SE and the two proposed optimizations: MSE and DSE. We performed an extensive evaluation of the two proposed techniques on a set of three individual hierarchical Statecharts and one model of three communicating Statecharts with a set of 160 different model versions and different types of atomic changes including modification, addition and deletion of the transitions in these models. The results from our experiments show a significant amount of savings up to 90+% in certain scenarios with respect to the size of the SETs generated from applying either technique and the time taken to generate them. The results also highlight the key factors that mostly influence the effectiveness of each technique. These are the change type and location for the MSE technique and the model characteristics concerning the number of multipath transitions in a model and the dependencies between its transitions for the DSE technique.

Some directions for future work include but not limited to the following:

1.  (1) The first direction is to extend the support for more advanced features of action code including more complex data types and user-defined method calls. Both features can be easily added to the current implementation by extending our interface component with the KLEE symbolic execution engine.
2.  (2) Another important direction is to extend the support for some user-defined or domain-specific semantics of specific Statechart features (e.g., priority schema for conflicting transitions and execution order of concurrent states) that is used in practice to override the default one of the tool. To the best of our knowledge, only practitioners who build these models can determine such refinements. In such cases, a modification to our current transformation components should be made.
3.  (3) The third direction is to extend the SET representation to include the test case values of the symbolic variables used to reach a feasible symbolic state such that a complete set of traces can be extracted for a generated SET to be used as a driver for model-based testing and run-time monitoring. This extension is feasible and is supported by the KLEE's “ktest-tool” utility that enables the reading of the contents of the “.ktest” binary files of the test cases generated by the tool.
4.  (4) The fourth direction is to extend the evaluation of the proposed work to consider more models with actual versions. This extension is limited by the accessibility to existing model repositories.
5.  (5) The fifth direction is to build a SET-based query engine to facilitate user queries and visualization of subparts of the tree. This feature is very important to provide us with a more precise and automated way to inspect some features in a given SET or to compare two SETs.
6.  (6) Finally, the proposed work in this research can be adapted to consider other state-based models used in other MDE tools, especially the open-source ones where the opportunity for extensibility is higher and is not limited by the use of some proprietary tools.

### 8.2 Perspective: The Road Ahead for MDE

The previous section contains suggestions how the work presented in this paper could be extended. But, the context of our work is MDE, and some more general words about MDE and its challenges and opportunities also seem appropriate.

According to Bran Selic, a key characteristic of traditional engineering disciplines is reliability, encompassing both, the “reliability of designs, that is, confidence that a proposed solution will fulfill its requirements and do so more or less within agreed-on cost, resource, and time constraints” and the “reliable transmission of design intent from specification to the implementation” \[

MDE thus goes beyond particular forms of notation (graphical versus textual), languages (such as UML), standards (such as OMG's MDA), processes, or tools. Instead, MDE shares with large parts of the computer science community an interest in abstraction \[

#### 8.2.1 Challenges

Several reports on the use of MDE in industry exist containing evidence that MDE can improve software quality and developer productivity \[

Selic explains this lack of adoption with cultural, social, and economic factors, and technical issues \[

The extent to which tools affect the success of industrial use of MDE has been studied in \[

Both papers highlight the need for MDE research on a broad set of topics that goes significantly beyond what is typically considered Computer Science.

#### 8.2.2 Opportunities

Despite these challenges, some recent technological and cultural developments also present significant opportunities to advance the state of the art of MDE in theory and practice \[

For instance, there has been significant progress in the specification and use of the formal semantics of highly complex artifacts including programming languages \[

Also, there has been significant industrial backing for the development of open-source modeling tools \[

As argued above, increasing levels of complexity in industrial software products and the way they are produced, together with novel uses of software will also create more opportunities for MDE. For instance, in its multiannual roadmap SPARC, the largest civilian-funded robotics research and innovation program in the world, has identified MDE as key technology for building robotic software and systems in a way that replaces the current lack of development processes and reliance on “craftmanship” by the adoption of “established engineering processes”:

“Model based methods are needed at the core of all complex robot systems and through the lifecycle. To address increasing complexity, a shift from human-oriented document-driven approaches to computer-assisted tools and a computer processable model-driven approach is needed in order to gain from design support processes. \[…\] Model-driven software development and domain-specific languages are core technologies required in order to achieve a separation of roles in the robotics domain while also improving composability, system integration, and also addressing nonfunctional properties” \[

Examples of other domains undergoing significant changes many of which involve new uses of software include automotive \[

Additional opportunities will be created by, e.g., tightening regulatory requirements for the certification of industrial software \[

Overall, we see significant potential for the continued successful use of MDE and increasing adoption, particularly if the challenges mentioned above can be addressed to a satisfactory extent.

## Appendix

### A.1 Ecore Meta-Model of CMLMs

In this [Appendix](#S0065245817300487_3.xhtml#s0320), we present the Ecore meta-model of our CMLMs. For clarity, we show it in two parts. The first part highlights the elements used to represent individual MLMs. The second part highlights the elements used to represent communicating MLMs.

![Fig. A.1 CMLMs Ecore meta-model—Part 1/2.](images/S0065245817300487/f04-25-9780128151198.jpg)

Fig. A.1 CMLMs Ecore meta-model—Part 1/2.

 ![Fig. A.2 CMLMs Ecore meta-model—Part 2/2.](images/S0065245817300487/f04-26-9780128151198.jpg)

Fig. A.2 CMLMs Ecore meta-model—Part 2/2.

 

## References

\[1\] King J.C. Symbolic execution and program testing. *Commun. ACM.* 1976;19(7):385–394.

\[2\] Gaston C., Le Gall P., Rapin N., Touil A. Symbolic execution techniques for test purpose definition. In: Uyar M.Ü., Duale A.Y., Fecko M.A., eds. Springer; 1–18. *Testing of Communicating Systems.* 2006;vol. 3964.

\[3\] Zurowska K., Dingel J. Symbolic execution of UML-RT state machines. In: ACM; 2012:1292–1299. *27th Annual ACM Symposium on Applied Computing (SAC’12).*.

\[4\] GRAMMATECH CodeSonar, GRAMMATECH CodeSonar, [http://www.grammatech.com/codesonar/](http://www.grammatech.com/codesonar/).

\[5\] IAR visualSTATE, IAR visualSTATE, [https://www.iar.com/iar-embedded-workbench/add-ons-and-integrations/visualstate/](https://www.iar.com/iar-embedded-workbench/add-ons-and-integrations/visualstate/).

\[6\] Person S., Yang G., Rungta N., Khurshid S. Directed incremental symbolic execution. *ACM SIGPLAN Notices.* 2011;46(6):504–515.

\[7\] Yang G., Păsăreanu C.S., Khurshid S. Memoized symbolic execution. In: ACM; 2012:144–154. *International Symposium on Software Testing and Analysis (ISSTA’12).*.

\[8\] Cadar C., Dunbar D., Engler D.R., et al. KLEE: unassisted and automatic generation of high-coverage tests for complex systems programs. 209–224. *8th USENIX Symposium on Operating Systems Design and Implementation (OSDI’08).* 2008;8.

\[9\] IBM Rational, Rational Rhapsody Developer, [http://www-03.ibm.com/software/products/en/ratirhap/](http://www-03.ibm.com/software/products/en/ratirhap/).

\[10\] Harel D. Statecharts: a visual formalism for complex systems. *Sci. Comput. Program.* 1987;8(3):231–274.

\[11\] Clarke L.A. A system to generate test data and symbolically execute programs. *IEEE Trans. Softw. Eng.* 1976;2(3):215–222.

\[12\] Cadar C., Sen K. Symbolic execution for software testing: three decades later. *Commun. ACM.* 2013;56(2):82–90.

\[13\] Khurshid S., Păsăreanu C.S., Visser W. Generalized symbolic execution for model checking and testing. In: Garavel H., Hatcliff J., eds. Springer; 2003:553–568. *Tools and Algorithms for the Construction and Analysis of Systems.*.

\[14\] Yang G., Person S., Rungta N., Khurshid S. Directed incremental symbolic execution. *ACM Trans. Softw. Eng. Methodol.* 2014;24(1):3.

\[15\] Cadar C., Engler D. Execution generated test cases: how to make systems code crash itself. In: Godefroid P., ed. Springer; 2005:2–23. *Model Checking Software.*.

\[16\] Godefroid P., Klarlund N., Sen K. DART: directed automated random testing. *ACM SIGPLAN Notices.* 2005;40(6):213–223.

\[17\] Thums A., Schellhorn G., Ortmeier F., Reif W. Interactive verification of statecharts. In: Ehrig H., Damm W., Desel J., Große-Rhode M., Reif W., Schnieder E., Westkämper E., eds. Springer; 2004:355–373. *Integration of Software Specification Techniques for Applications in Engineering.*.

\[18\] Balser M., Bäumler S., Knapp A., Reif W., Thums A. Interactive verification of UML state machines. In: Davies J., Schulte W., Barnett M., eds. Springer; 2004:434–448. *Formal Methods and Software Engineering.*.

\[19\] Androutsopoulos K., Clark D., Harman M., Li Z., Tratt L. Control dependence for extended finite state machines. In: Chechik M., Wirsing M., eds. Springer; 2009:216–230. *Fundamental Approaches to Software Engineering.*.

\[20\] Labbé S., Gallois J.-P. Slicing communicating automata specifications: polynomial algorithms for model reduction. *Form. Asp. Comput.* 2008;20(6):563–595.

\[21\] Ranganath V.P., Amtoft T., Banerjee A., Hatcliff J., Dwyer M.B. A new foundation for control dependence and slicing for modern program structures. *ACM Trans. Program. Lang. Syst.* 2007;29(5):27.

\[22\] Chimisliu V., Wotawa F. Improving test case generation from UML statecharts by using control, data and communication dependencies. In: IEEE; 2013:125–134. *13th International Conference on Quality Software (QSIC).*.

\[23\] Stephan M., Cordy J.R. A survey of model comparison approaches and applications. In: Hammoudi S., Pires L.F., Filipe J., das Neves R.C., eds. 2013:265–277. *Modelsward.*.

\[24\] Maoz S., Ringert J.O., Rumpe B. A manifesto for semantic model differencing. In: Dingel J., Solberg A., eds. Springer; 2011:194–203. *Models in Software Engineering.*.

\[25\] Dingel J. Complexity is the only constant: trends in computing and their relevance to model driven engineering. In: Echahed R., Minas M., eds. Springer; 2016:3–18. *International Conference on Graph Transformation.*.

\[26\] Kolawa A.K., Kucharski M. *System and Method for Detecting Defects in a Computer Program Using Data and Control Flow Analysis.* 2011 US Patent 7,900,193.

\[27\] Biswas S., Mall R., Satpathy M., Sukumaran S. Regression test selection techniques: a survey. *Informatica.* 2011;35(3).

\[28\] Bhaduri P., Ramesh S. *Model Checking of Statechart Models: Survey and Research Directions.* 2004 arXiv:cs/0407038.

\[29\] Păsăreanu C.S., Visser W. A survey of new trends in symbolic execution for software testing and analysis. *Int. J. Softw. Tools Technol. Transfer.* 2009;11(4):339–353.

\[30\] Maoz S. Using model-based traces as runtime models. *IEEE Comput.* 2009;42:28–36.

\[31\] Hearnden D., Lawley M., Raymond K. Incremental model transformation for the evolution of model-driven systems. In: Nierstrasz O., Whittle J., Harel D., Reggio G., eds. Springer; 2006:321–335. *Model Driven Engineering Languages and Systems.*.

\[32\] Henzinger T.A., Jhala R., Majumdar R., Sanvido M.A. Extreme model checking. In: Dershowitz N., ed. Springer; 2003:332–358. *Verification: Theory and Practice.*.

\[33\] Yang G., Dwyer M.B., Rothermel G. Regression model checking. In: IEEE; 2009:115–124. *IEEE International Conference on Software Maintenance (ICSM 2009).*.

\[34\] Backes J., Person S., Rungta N., Tkachuk O. Regression verification using impact summaries. In: Bartocci E., Ramakrishnan C.R., eds. Springer; 2013:99–116. *Model Checking Software.*.

\[35\] Felsing D., Grebing S., Klebanov V., Rümmer P., Ulbrich M. Automating regression verification. In: ACM; 2014:349–360. *29th ACM/IEEE International Conference on Automated Software Engineering (ASE’14).*.

\[36\] Godlin B., Strichman O. Regression verification. In: ACM; 2009:466–471. *46th Annual Design Automation Conference.*.

\[37\] Godlin B., Strichman O. Regression verification: proving the equivalence of similar programs. *Softw. Test. Verif. Reliab.* 2013;23(3):241–258.

\[38\] Person S., Dwyer M.B., Elbaum S., Pasareanu C.S. Differential symbolic execution. In: ACM; 2008:226–237. *16th ACM SIGSOFT International Symposium on Foundations of Software Engineering (FSE’08).*.

\[39\] Strichman O., Godlin B. Regression verification—a practical way to verify programs. In: Meyer B., Woodcock J., eds. Springer; 2005:496–501. *Verified Software: Theories, Tools, Experiments.*.

\[40\] Yang G., Khurshid S., Person S., Rungta N. Property differencing for incremental checking. In: ACM; 2014:1059–1070. *36th International Conference on Software Engineering.*.

\[41\] Mikk E., Lakhnech Y., Siegel M., Holzmann G.J. Implementing statecharts in PROMELA/SPIN. In: IEEE; 1998:90–101. *2nd IEEE Workshop on Industrial Strength Formal Specification Techniques.*.

\[42\] Clarke E., Heinle W. *Modular Translation of Statecharts to SMV.* Pittsburgh: Tech. Rep. CMU-CS-00-XXX, Carnegie Mellon University; 2000 PA.

\[43\] Mehlitz P. Trust your model-verifying aerospace system models with java pathfinder. In: IEEE; 2008. *Aerospace Conference.*.

\[44\] Madhukar K., Metta R., Singh P., Venkatesh R. Reachability verification of rhapsody statecharts. In: IEEE; 2013:96–101. *IEEE Sixth International Conference on Software Testing, Verification and Validation Workshops (ICSTW).*.

\[45\] Giese H., Tichy M., Burmester S., Schäfer W., Flake S. ACM, Towards the compositional verification of real-time UML designs. *ACM SIGSOFT Softw. Eng. Notes.* 2003;28(5):38–47.

\[46\] Schinz I., Toben T., Mrugalla C., Westphal B. The rhapsody UML verification environment. In: IEEE; 2004:174–183. *Second International Conference on Software Engineering and Formal Methods (SEFM’04).*.

\[47\] Lee N.H., Cha S.D. Generating test sequences using symbolic execution for event-driven real-time systems. *Microprocess. Microsyst.* 2003;27(10):523–531.

\[48\] Frantzen L., Tretmans J., Willemse T. Test generation based on symbolic specifications. In: Springer; 2005:1–15. *Formal Approaches to Software Testing.*.

\[49\] Jéron T. Symbolic model-based test selection. *Electron. Notes Theor. Comput. Sci.* 2009;240:167–184.

\[50\] Pasareanu C.S., Schumann J., Mehlitz P., Lowry M., Karsai G., Nine H., Neema S. Model based analysis and test generation for flight software. In: IEEE; 2009:83–90. *Third IEEE International Conference on Space Mission Challenges for Information Technology, 2009. SMC-IT 2009.*.

\[51\] Lauterburg S., Sobeih A., Marinov D., Viswanathan M. Incremental state-space exploration for programs with dynamically allocated data. In: ACM; 2008:291–300. *30th International Conference on Software Engineering (ICSE’08).*.

\[52\] Conway C.L., Namjoshi K.S., Dams D., Edwards S.A. Incremental algorithms for inter-procedural analysis of safety properties. In: Springer; 2005:449–461. *Computer Aided Verification.*.

\[53\] Law J., Rothermel G. Incremental dynamic impact analysis for evolving software systems. In: IEEE; 2003:430–441. *14th International Symposium on Software Reliability Engineering, 2003. ISSRE 2003.*.

\[54\] Visser W., Geldenhuys J., Dwyer M.B. Green: reducing, reusing and recycling constraints in program analysis. In: ACM; 2012. *ACM SIGSOFT 20th International Symposium on the Foundations of Software Engineering.*.

\[55\] Jia X., Ghezzi C., Ying S. Enhancing reuse of constraint solutions to improve symbolic execution. In: ACM; 2015:177–187. *International Symposium on Software Testing and Analysis (ISSTA’15).*.

\[56\] Aquino A., Bianchi F.A., Chen M., Denaro G., Pezzè M. Reusing constraint proofs in program analysis. In: ACM; 2015:305–315. *International Symposium on Software Testing and Analysis (ISSTA’15).*.

\[57\] Beyer D., Wendler P. Reuse of verification results. In: Bartocci E., Ramakrishnan C.R., eds. Springer; 2013:1–17. *Model Checking Software.*.

\[58\] Beyer D., Löwe S., Novikov E., Stahlbauer A., Wendler P. Precision reuse for efficient regression verification. In: ACM; 2013:389–399. *9th Joint Meeting on Foundations of Software Engineering (ESEC/FSE’13).*.

\[59\] Kurshan H., Hardin R.H., Kurshan R.P., Mcmillan K.L., Reeds J.A., Sloane N.J.A. Efficient regression verification. In: 1996:147–150. *IEE Proceedings of the International Workshop on Discrete Event Systems (WODES’96).*.

\[60\] Sery O., Fedyukovich G., Sharygina N. Incremental upgrade checking by means of interpolation-based function summaries. In: IEEE; 2012:114–121. *Formal Methods in Computer-Aided Design (FMCAD), 2012.*.

\[61\] Larus J.R. Whole program paths. *ACM SIGPLAN Notices.* 1999;34(5):259–269.

\[62\] Law J., Rothermel G. Whole program path-based dynamic impact analysis. In: IEEE; 2003:308–318. *25th International Conference on Software Engineering (ICSE’03).*.

\[63\] Rungta N., Person S., Branchaud J. A change impact analysis to characterize evolving program behaviors. In: IEEE; 2012:109–118. *28th IEEE International Conference on Software Maintenance (ICSM), 2012.*.

\[64\] Person S., Rungta N. Maintaining the health of software monitors. *Innov. Syst. Softw. Eng.* 2013;9(4):257–269.

\[65\] Böhme M.B.C. d. S. OliveiraRoychoudhury A. Partition-based regression verification. In: IEEE Press; 2013:302–311. *Proceedings of the 2013 International Conference on Software Engineering.*.

\[66\] Ghezzi C. Evolution, adaptation, and the quest for incrementality. In: Calinescu R., Garlan D., eds. Springer; 2012:369–379. *Large-Scale Complex IT Systems. Development, Operation and Management.*.

\[67\] Huang C.-M., Hsu J.-M. An incremental protocol verification method. *Comput. J.* 1994;37(8):698–710.

\[68\] Korel B., Tahat L.H., Vaysburg B. Model based regression test reduction using dependence analysis. In: IEEE; 2002:214–223. *International Conference on Software Maintenance (ICSM’02).*.

\[69\] EI-Fakih K., Yevtushenko N., Bochmann G. FSM-based incremental conformance testing methods. *IEEE Trans. Softw. Eng.* 2004;30(7):425–436.

\[70\] Chen Y., Probert R.L., Ural H. Model-based regression test suite generation using dependence analysis. In: ACM; 2007:54–62. *3rd International Workshop on Advances in Model-based Testing.*.

\[71\] Uzuncaova E., Khurshid S., Batory D. Incremental test generation for software product lines. *IEEE Trans. Softw. Eng.* 2010;36(3):309–322.

\[72\] Rapos E.J., Dingel J. Incremental test case generation for UML-RT models using symbolic execution. In: IEEE; 2012:962–963. *2012 IEEE Fifth International Conference on Software Testing, Verification and Validation (ICST).*.

\[73\] Lochau M., Schaefer I., Kamischke J., Lity S. Incremental model-based testing of delta-oriented software product lines. In: Brucker A.D., Julliand J., eds. Springer; 2012:67–82. *Tests and Proofs.*.

\[74\] Lity S., Baller H., Schaefer I. Towards incremental model slicing for delta-oriented software product lines. In: IEEE; 2015:530–534. *2015 IEEE 22nd International Conference on Software Analysis, Evolution and Reengineering (SANER).*.

\[75\] Clarke D., Helvensteijn M., Schaefer I. Abstract delta modeling. *ACM SIGPLAN Notices.* 2011;46(2):13–22.

\[76\] Egyed A. Automatically detecting and tracking inconsistencies in software design models. *IEEE Trans. Softw. Eng.* 2011;37(2):188–204.

\[77\] Blanc X., Mougenot A., Mounier I., Mens T. Incremental detection of model inconsistencies based on model operations. In: Springer; 2009:32–46. *International Conference on Advanced Information Systems Engineering.*.

\[78\] Zheng H., Zhang Z., Myers C.J., Rodriguez E., Zhang Y. Compositional model checking of concurrent systems. *IEEE Trans. Comput.* 2015;64(6):1607–1621.

\[79\] Burmester S., Giese H., Hirsch M., Schilling D. Incremental design and formal verification with UML/RT in the FUJABA real-time tool suite. In: Citeseer; 2004. *International Workshop on Specification and Validation of UML Models for Real Time and Embedded Systems, SVERTS2004, Satellite Event of the 7th International Conference on the Unified Modeling Language, UML.*.

\[80\] Cordy M., Schobbens P.-Y., Heymans P., Legay A. Towards an incremental automata-based approach for software product-line model checking. In: ACM; 74–81. *16th International Software Product Line Conference.* 2012;2.

\[81\] Johnson K., Calinescu R., Kikuchi S. An incremental verification framework for component-based software systems. In: ACM; 2013:33–42. *16th International ACM Sigsoft Symposium on Component-based Software Engineering (CBSE’13).*.

\[82\] Hartmann J., Imoberdorf C., Meisinger M. ACM, UML-based integration testing. *ACM SIGSOFT Softw. Eng. Notes.* 2000;25(5):60–70.

\[83\] Bourhfir C., Dssouli R., Aboulhamid E., Rico N. A guided incremental test case generation procedure for conformance testing for CEFSM specified protocols. In: Petrenko A., Yevtushenko N., eds. Springer; 1998:279–294. *Testing of Communicating Systems.*.

\[84\] D.E. Long, Model checking, abstraction, and compositional verification (Ph.D. thesis), Carnegie Mellon University 1993.

\[85\] Kang I., Lee I. State minimization for concurrent system analysis based on state space exploration. In: IEEE; 1994:123–134. *Ninth Annual Conference on Computer Assurance, 1994. COMPASS’94 Safety, Reliability, Fault Tolerance, Concurrency and Real Time, Security.*.

\[86\] Abdulla P.A., Annichini A., Bensalem S., Bouajjani A., Habermehl P., Lakhnech Y. Verification of infinite-state systems by combining abstraction and reachability analysis. In: Springer; 1999:146–159. *Computer Aided Verification.*.

\[87\] Boigelot B., Godefroid P. Symbolic verification of communication protocols with infinite state spaces using QDDs. *Form. Methods Syst. Des.* 1999;14(3):237–255.

\[88\] Cheung S.C., Kramer J. Context constraints for compositional reachability analysis. *ACM Trans. Softw. Eng. Methodol.* 1996;5(4):334–377.

\[89\] Cheung S.C., Giannakopoulou D., Kramer J. Verification of Liveness Properties Using Compositional Reachability Analysis. In: Springer; 1997:227–243. *6th European Software Engineering Conference Held Jointly with the 5th ACM SIGSOFT Symposium on the Foundations of Software Engineering (ESEC-FSE ’97), 1997.*.

\[90\] Zurowska K., Dingel J. Symbolic execution of communicating and hierarchically composed UML-RT state machines. In: Goodloe A.E., Person S., eds. Springer; 2012:39–53. *NASA Formal Methods.*.

\[91\] Jöbstl E., Weiglhofer M., Aichernig B.K., Wotawa F. When BDDs fail: conformance testing with symbolic execution and SMT solving. In: IEEE; 2010:479–488. *Third International Conference on Software Testing, Verification and Validation (ICST).*.

\[92\] Anand S., Păsăreanu C.S., Visser W. Symbolic Execution with Abstract Subsumption Checking. In: Springer; 2006:163–181. *International SPIN Workshop on Model Checking of Software.*.

\[93\] Luo G., Bochmann G.V., Petrenko A. Test selection based on communicating nondeterministic finite-state machines using a generalized wp-method. *IEEE Trans. Softw. Eng.* 1994;20(2):149–162.

\[94\] Khalil A., Dingel J. Incremental symbolic execution of evolving state machines. In: IEEE; 2015:14–23. *2015 ACM/IEEE 18th International Conference on Model Driven Engineering Languages and Systems (MODELS).*.

\[95\] Khalil A., Dingel J. *Incremental Symbolic Execution of Evolving State Machines Using Memoization and Dependence Analysis.* Queen's University; 2015.1–42 Tech. Rep. 2015–623.

\[96\] A.L.J. Dominguez, Detection of feature interactions in automotive active safety features (Ph.D. thesis), University of Waterloo, 2012.

\[97\] Lee D., Sabnani K.K., Kristol D.M., Paul S. Conformance testing of protocols specified as communicating finite state machines—a guided random walk based approach. *IEEE Trans. Commun.* 1996;44(5):631–640.

\[98\] Selic B. What will it take? A view on adoption of model-based methods. *Softw. Syst. Model.* 2012;11:513–526.

\[99\] Kramer J. Is abstraction the key to computing? *Commun. ACM.* 2007;50(4):36–42.

\[100\] Denning P. Virtual memory. *ACM Comput. Surv.* 1970;2(3):153–189.

\[101\] Parnas D. On the criteria to be used in decomposing systems into modules. *Commun. ACM.* 1972;15(12):1053–1058.

\[102\] Koopman P., Wagner M. Challenges in autonomous vehicle testing and validation. *SAE Int. J. Trans. Saf.* 2016;4(1):15–24.

\[103\] Lohr S. *G.E., the 124-Year-Old Software Start-Up.* 2016 The New York Times, August 27.

\[104\] Weigert T., Weil F. Practical experience in using model-driven engineering to develop trustworthy systems. In: IEEE; 2006:208–217. *IEEE International Conference on Sensor Networks, Ubiquitous, and Trustworthy Computing (SUTC’06).*.

\[105\] Kirstan S., Zimmermann J. Evaluating costs and benefits of model-based development of embedded software systems in the car industryresults of a qualitative case study. In: 2010. *Workshop “From Code Centric to Model Centric: Evaluating the Effectiveness of MDD (C2M: EEMDD)”.*.

\[106\] Bone M., Cloutier R.R. The current state of model based system engineering: results from the OMGTM SysML request for information 2009. In: 2010. *8th Conference on Systems Engineering Research (CSER).*.

\[107\] Hutchinson J., Whittle J., Rouncefield M., Kristofferson S. Empirical assessment of MDE in industry. In: ACM; 2011:471–480. *33rd International Conference on Software Engineering (ICSE11).*.

\[108\] Mohagheghi P., Gilani W., Stefanescu A., Fernandez M., Nordmoen B., Fritzsche M. Where does model-driven engineering help? Experiences from three industrial cases. *Softw. Syst. Model.* 2013;12(3):619–639.

\[109\] Liebel G., Marko N., Tichy M., Leitner A., Hansson J. Assessing the state-of-practice of model-based engineering in the embedded systems domain. In: 2014:166–182. *ACM/IEEE 17th International Conference on Model Driven Engineering Languages and Systems (MODELS’14).*.

\[110\] Petre M. “No shit” or “Oh, shit!”: responses to observations on the use of UML in professional practice. *Softw. Syst. Model.* 2014;13(4):1225–1235.

\[111\] Whittle J., Hutchinson J., Rouncefield M., Burden H., Heldal R. A taxonomy of tool-related issues affecting the adoption of model-driven engineering. *Softw. Syst. Model.* 2017;16(2):313–331.

\[112\] Bogdănaş D., Roşu G. K-Java: a complete semantics of Java. In: ACM; 2015:445–456. *ACM SIGPLAN/SIGACT Symposium on Principles of Programming Languages (POPL’15).*.

\[113\] Klein G., Elphinstone K., Heiser G., Andronick J., Cock D., Derrin P., Elkaduwe D., Engelhardt K., Kolanski R., Norrish M., Sewell T., Tuch H., Winwood S. Formal verification of an OS kernel. In: ACM; 2009:207–220. *ACM SIGOPS Symposium on Operating Systems Principles (SOSP’09).*.

\[114\] Leroy X. Formal verification of a realistic compiler. *Commun. ACM.* 2009;52(7).

\[115\] Vardi M. *The Automated-Reasoning Revolution: From Theory to Practice and Back.* 2017 ICSE’17 keynote presentation.

\[116\] *ExCAPE Annual Report of Activities, April 2014 to March 2015.* 2015. [https://excape.cis.upenn.edu/about.html](https://excape.cis.upenn.edu/about.html) Available from.

\[117\] *Syntax-Guided Synthesis Competition (SyGuS’17), July 22.* 2017 Heidelberg, Germany.

\[118\] PolarSys: Open Source Solutions for Embedded Systems, Eclipse Working Group, [https://www.polarsys.org](https://www.polarsys.org).

\[119\] Barrett R., Bordeleau F. 5 Years of ‘Papyrusing’—migrating industrial development from a proprietary commercial tool to Papyrus. In: 2015:3–12. *Workshop on Open Source Software for Model Driven Engineering (OSS4MDE’15).* (invited presentation).

\[120\] SPARC. *Multi-Annual Roadmap (MAR) for Horizon 2020 Call ICT-2017 (ICT-25, 27 & 28).* 2016. Available from [https://www.eu-robotics.net/sparc/newsroom/press/multi-annual-roadmap-mar-for-horizon-2020-call-ict-2017-ict-25-ict-27-ict-28-published.html](https://www.eu-robotics.net/sparc/newsroom/press/multi-annual-roadmap-mar-for-horizon-2020-call-ict-2017-ict-25-ict-27-ict-28-published.html).

\[121\] Radio Technical Commission for Aeronautics. *DO-178C: Software Considerations in Airborne Systems and Equipment Certification.* 2012.

\[122\] Kokaly S., Salay R., Sabetzadeh M., Chechik M., Maibaum T. Model Management for Regulatory Compliance: a position paper. In: 2016: *8th Workshop on Models in Software Engineering (MiSE’16).* Austin, USA.

\[123\] Monroe D. When data is not enough. *Commun. ACM.* 2015;58(12):12–14.

![u04-01-9780128151198](images/S0065245817300487/u04-01-9780128151198.jpg)

**Amal Khalil** received her Ph.D. degree in computer science from Queen's University (2016) in the areas of model-driven engineering and model-based verification of behavioral software models in the context of automotive embedded systems. She is a former researcher in the Modeling and Analysis in Software Engineering Group at Queen's University. Amal Khalil was awarded a Silver Medal in the ACM Student Research Competition that was held in conjunction with the 2015 ACM/IEEE 18th International Conference on Model Driven Engineering Languages and Systems (MODELS). Before moving to Canada, Amal Khalil received her Bachelor and M.Sc. degrees in Electrical Engineering.

![u04-02-9780128151198](images/S0065245817300487/u04-02-9780128151198.jpg)

**Juergen Dingel** received an M.Sc. from Berlin University of Technology in Germany and a Ph.D. in Computer Science from Carnegie Mellon University (2000). He is Professor in the School of Computing at Queen's University where he leads the Modeling and Analysis in Software Engineering group. His research interests include software modeling, model-driven engineering, analysis of software artifacts, formal specification and verification, and software quality assurance. Juergen was PC co-chair of the ACM/IEEE 17th International Conference on Model Driven Engineering Languages and Systems (MODELS'14) and of the IFIP International Conference on Formal Techniques for Distributed Systems (FMOODS-FORTE'11). He is on the editorial boards of the Springer journals Software and Systems Modeling (SoSyM), and Software Tools for Technology Transfer (STTT) and currently serves as chair of the MODELS Steering Committee.

* * *

^([a](#S0065245817300487_1.xhtml#xfn0010 "label")) The term “Statechart” is used exchangeably with the term “State Machine” in this document.

^([b](#S0065245817300487_1.xhtml#xfn0015 "label")) Please note that we sometimes use the terms “symbolic transition”, “symbolic path”, and “execution path” to mean the same thing, however, more generally, the term “execution path” refers to a sequence of one or more consecutive symbolic transitions in a given SET.

^([c](#S0065245817300487_1.xhtml#xfn0020 "label")) Depth-first-search would be another possible alternative.

^([d](#S0065245817300487_1.xhtml#xfn0025 "label")) We use the popular open-source symbolic execution engine KLEE \[

^([e](#S0065245817300487_2.xhtml#xfn0030 "label")) Note that we can also call it regression or partial symbolic execution.

^([f](#S0065245817300487_2.xhtml#xfn0035 "label")) Dead ends are states that have no feasible outgoing transitions and they are not end states.

Chapter Five 

# A Tutorial on Software Obfuscation

Sebastian Banescu; Alexander Pretschner    ^()Technische Universität München, München, Germany

## Abstract

Protecting a digital asset once it leaves the cyber trust boundary of its creator is a challenging security problem. The creator is an entity which can range from a single person to an entire organization. The trust boundary of an entity is represented by all the (virtual or physical) machines controlled by that entity. Digital assets range from media content to code and include items such as: music, movies, computer games, and premium software features. The business model of the creator implies sending digital assets to end-users—such that they can be consumed—in exchange for some form of compensation. A security threat in this context is represented by malicious end-users, who attack the confidentiality or integrity of digital assets, in detriment to digital asset creators and/or other end-users. Software obfuscation transformations have been proposed to protect digital assets against malicious end-users, also called Man-At-The-End (MATE) attackers. Obfuscation transforms a program into a functionally equivalent program which is harder for MATE to attack. However, obfuscation can be use both for benign and malicious purposes. Malware developers rely on obfuscation techniques to circumvent detection mechanisms and to prevent malware analysts from understanding the logic implemented by the malware. This chapter presents a tutorial of the most popular existing software obfuscation transformations and mentions published attacks against each transformation. We present a snapshot of the field of software obfuscation and indicate possible directions, which require more research.

### Keywords

Obfuscation; Software protection; Reverse engineering; Man-At-The-End; Code transformation; Tutorial

## 1 Introduction

A common business model for commercial media content and software creators is to distribute digital assets (e.g., music, movies, proprietary algorithms in software executables) to end-users, in exchange for some form of compensation. Even with ubiquitous cloud-based services, digital asset creators still need to ship media content and client applications to end-users. For both performance and scalability reasons, software developers often choose to develop thick client applications, which contain sensitive code and/or data. For example, games or media players are often thick clients offering premium features or content, which should only be accessible if the end-user pays a license fee. Sometimes, the license is temporary and therefore the client software should somehow restrict access to these features and content once the license expires. Moreover, some commercial software developers also want to protect secret algorithms used in their client software, which give them an advantage over their competitors.

One open challenge in IT security is protecting digital assets once they leave the cyber trust boundary of their creator. The creator of digital assets can range from a single person to an organization. The security threat in this context is represented by malicious end-users, who among other things, may want to:

*   • Use digital assets without paying the license fees required by the creators of that digital asset.
*   • Redistribute illegal copies of digital assets to other end-users, sometimes in order to make a profit.
*   • Make changes to the digital assets (e.g., by tampering with its code), in order to modify its behavior.

Such malicious end-users are also called Man-At-The-End (MATE) attackers \[

Researchers, practitioners, and law makers have sought several solutions for this challenge, all of which have their advantages and disadvantages. [Fig. 1](#S0065245817300499.xhtml#f0010) shows a classification of these solutions, proposed by Collberg et al. \[

![Fig. 1 Classification of protections against MATE attacks proposed in \[ ¶ An obfuscator is in essence a compiler that takes a program as input, and outputs a functionally equivalent program, which is harder to understand and analyze than the input program. The meaning of the phrases “functionally equivalent” and “harder to understand and analyze” will be discussed in this chapter. For instance, some classical compiler optimizations are also considered obfuscation transformations \[ ¶ This chapter presents a tutorial of several popular obfuscation transformations together with illustrative examples. It also mentions the MATE attacks published in the literature, which have been proposed for defeating each obfuscation transformation. The rest of the chapter is structured as follows. Section 2 presents classification dimensions for obfuscation transformations. Section 3 presents classification dimensions for MATE attacks. Section 4 presents a survey of obfuscation transformations and state-of-the-art MATE attacks that claim to break each obfuscation. Section 5 discusses the current state of software obfuscation vs MATE attacks. Section 6 presents related work, and Section 7 concludes the chapter. ¶  ¶ 2 Classification of Code Obfuscation Transformations ¶ Several surveys and taxonomies for software obfuscation have been proposed in literature \[ ¶ 2.1 Abstraction Level of Transformations ¶ One common dimension of code transformations is the level of abstraction at which these transformations have a noticeable effect, i.e., source code, intermediate representation, and binary machine code. Such a distinction is relevant for usability purposes, e.g., a JavaScript developer will mostly be interested in source code-level transformations and a C developer will mainly be interested in binary level. However, none of the previously mentioned taxonomies and surveys classifies transformations according to the abstraction level. This is due to the fact that some obfuscation transformations have an effect at multiple abstraction levels. Moreover, it is common for papers to focus only on a specific abstraction level, disregarding transformations at other levels. ¶ 2.2 Unit of Transformations ¶ Larsen et al. \[ ¶ • Instruction-level transformations are applied to individual instructions or sequences of instructions. This is due to the fact that at the source code level, a code statement can consist of one or more IR or Assembly instructions.• Basic block-level transformations affect the position of one or more basic blocks. Basic blocks are a list of sequential instructions that have a single entry point and end in a branch instruction.• Loop-level transformations alter the familiar loop constructs added by developers.• Function-level transformations affect several instructions and basic blocks of a particular subroutine. Moreover, they may also affect the stack and heap memory corresponding to the function.• Program-level transformations affect several functions inside an application. However, they also affect the data segments of the program and the memory allocated by that program.• System-level transformations target the operating system or the runtime environment and they affect how other programs interact with them. ¶ The unit of transformation is important in practice because developers can choose the appropriate level of granularity according to the asset they must protect. For example, loop-level transformations are not appropriate for hiding data, but they are appropriate for hiding algorithms. However, the same problem, as for the previous classification dimension, arises for the unit of transformation, namely, the same obfuscation transformation may be applicable to different units of transformation. ¶ 2.3 Dynamics of Transformations ¶ The dynamics of transformation—used by Schrittwieser et al. \[ ¶ 2.4 Target of Transformations ¶ The most common dimension for classifying obfuscation transformations is according to the target of transformations. This dimension was first proposed by Collberg et al. \[ ¶ • Data transformations, which change the representation and location of constant values (e.g., numbers, strings, keys) hard-coded in an application, as well as variable memory values used by the application.• Code transformations, which transform the high-level abstractions (e.g., data structures, variable names, indentation) as well as the algorithm and control-flow of the application. ¶ This dimension is important for practitioners, because it indicates the goal of the defender, i.e., whether the defender wants to protect data or code. Note that obfuscation transformations which target data may also affect the layout of the code and its control-flow, however, their target is hiding data, not code. In practice data transformations are often used in combination with code transformations, to improve the resilience of the program against MATE attacks. ¶ 2.4.1 Data Transformations ¶ Data transformations can be divided into two subcategories: ¶ 1. Constant data transformations, which affect static (hard-coded) values. Abstractly, such transformations are encoding functions which take one or more constant data items i (e.g., byte arrays, integer variables), and convert them into one or more data items i′ = f(i). This means that any value assigned to, compared to and based on i is also changed according to the new encoding. There will be a trade-off between resilience on one hand, and cost on the other, because all operations performed on i require computing f−1(i), unless f is homomorphic w.r.t. those operations.2. Variable data transformations, which modify the representation or structure of variable memory values. The goal of such transformations is to hamper the development of automated MATE attacks, which can assume that a certain variable memory value will always have a certain representation or a certain structure (e.g., an integer array of 100 contiguous elements). If such assumptions hold then automated attacks are easier to develop, because they mainly rely on pattern matching. Therefore, by employing the transformations presented in this section, one can raise the bar for these kinds of attacks. ¶ Note that variable transformations are not the transformations that affect the names or the order of variables, but the representation of the data stored in those variables. ¶  ¶ 2.4.2 Code Transformations ¶ Code transformations can also be divided into two subcategories, namely: ¶ 1. Code logic transformations, which affect the control-flow of the program, its ease of readability and maintainability. Such transformations are aimed at adding complexity to the code in order to prevent MATE attackers from understanding what the algorithm(s) implemented by the code are.2. Code abstraction transformations, which destroy programming abstractions, are generally the first hints that MATE attackers use to start reverse engineering a program. ¶ As opposed to constant data transformations, which in some cases perform one-way mappings of data to a completely different domain which requires no interpretation, code transformations must always perform a mapping to the same domain of executable code, because obfuscated code must be able to run on the underlying machine where it is installed. ¶ 2.5 Summary of Obfuscation Transformation Classification ¶ Table 1 provides a summary of the classification dimensions described above along with the possible discrete values that each dimension can take. In the next section we choose to present a survey of obfuscation transformations classified according to their target of transformation, because it entails a clear partition of transformations. ¶  ¶ Table 1 ¶ DimensionPossible Values Abstraction levelSource code Intermediate representation Binary machine code UnitInstruction Basic block Loop Function Program System DynamicsStatic Dynamic TargetConstant data Variable data Code logic Code abstraction ¶ 3 Classification of MATE Attacks ¶ In contrast to the classification of software protection techniques (see Section 2), the classification of MATE attacks has been the topic of relatively few publications \[ ¶ 3.1 Attack Type Dimension ¶ Basile et al. \[ ¶ • The original or a simplified version of the source code. This is always the case for MATE attackers who are interested in intellectual property theft, i.e., stealing a competitor's algorithm.• A statically embedded or dynamically generated data item. Common examples of such data items are decryption keys used by Digital Rights Management (DRM) technologies to play premium content only on authorized devices, for authorized users. However, data items may also include hard-coded passwords, IP addresses, etc.• The sequence of obfuscation transformations and/or tools used to obfuscate (protect) the program, also called metadata. This kind of information is often used by antivirus engines to detect suspicious binaries, based on the fact that several previously seen malware have used the same obfuscation transformations and/or tools.• The location (i.e., lines of code or bytes) of a particular function of the code. For instance, the attacker may be interested in the module which performs premium content decryption in order to copy it and reuse it in another program, without necessarily understanding how it works. ¶ We compare these four information types proposed by Collberg et al. \[ ¶ • Code understanding, which according to its description in the paper maps to the source code information type described above. However, the name of this category suggests a more general attack type than a full recovery of the entire source code, because it could be sufficient to have a partial code understanding. For example, a malware analysis engine can decide that a software is malicious using its observed behavior (e.g., unsolicited calls to premium telephone numbers), which does not require full understanding of the source code. Moreover, metadata recovery also falls inside of this category of code understanding. Therefore, in this chapter we will use this more general category, i.e., code understanding.• Finding the location of data, which maps perfectly onto the data item information type described above. However, the phrase location of data may be mistaken for the location information type. Therefore, this chapter will simply use data item recovery.• Finding the location of program functionality, which maps onto the location information type described above. However, Schrittwieser et al. \[• Extraction of code fragments, which does not directly map onto any of the information items described above. However, we believe that finding the location of program functionality is a prerequisite to this aim of the analyst, because extraction can only be done after the location of the code fragment has been recovered. Therefore, in this chapter we associate this aim of the analyst with the location information type. ¶ In sum, we use the following three categories of attack types with the meanings discussed above: (1) code understanding, (2) data item recovery, and (3) location recovery. ¶ 3.2 Dynamics Dimension ¶ Dynamics is one of the most commonly used classification criteria for automated MATE attacks and it refers to whether the attacked program is executed on a machine or not, i.e.: ¶ • Static analysis attacks do not execute the program on the underlying (physical or virtual) machine. The subject of the analysis is the static code of the program.• Dynamic analysis attacks run the program and record executed instructions, function calls and/or memory states during execution, which are the subject of analysis. ¶ Static attacks are commonly faster than dynamic attacks. However, static analysis attacks do not handle many code obfuscation transformations as well as dynamic analysis attacks. This does not mean that dynamic analysis attacks can handle any kind of obfuscation easily. For instance, it is challenging to dynamically analyze programs employing code transformation techniques that achieve temporal diversity, i.e., the program has significantly different execution traces and/or memory states on every execution. Moreover, dynamic analysis is in general incomplete, i.e., it cannot explore or reason about all possible executions of a program, as opposed to static analysis. ¶ 3.3 Interpretation Dimension ¶ Code interpretation refers to whether the program's code or the artifacts generated using it (e.g., static disassembly, dynamic traces) are treated as text or are interpreted according to a semantic meaning (e.g., operational semantics). Therefore the two types of code interpretation considered in this chapter are ¶  ¶  ¶ • Syntactic attacks which treat the program's code or any other artifacts generated by executing or processing it, as a string of bytes (e.g., characters). For example, pattern matching on static code \[ ¶  ¶ • Semantic attacks which interpret the code according to some semantics, e.g., denotational semantics, operational semantics, axiomatic semantics, and variations thereof \[ ¶ Syntactic attacks are generally faster than semantic attacks due to the missing layer of abstraction that interprets the code. Coincidentally, most syntactic attacks are performed via static analysis and most semantic attacks are performed via dynamic analysis. However, there are exceptions, e.g., the syntactic analysis of dynamically generated execution traces and semantic static analysis via abstract interpretation \[ ¶ 3.4 Alteration Dimension ¶ Alteration refers to whether the automated MATE attack changes (alters) the code or not. This type of classification is analogous to the message alteration classification of MITM attacks on communication channels. Hence there are two types of code alteration: ¶ • Passive attacks do not make any changes to the code or data of the program. For instance, extracting a secret key or password from a program does not require any code alterations.• Active attacks make changes to the code or data of a program. For example, removing data or code integrity checks (e.g., password checks) require modifying the code of the program. Also “disarming” malware may also involve tampering with its code. ¶ If an attacker's goal can be achieved via either passive or active attacks, then the type of attack used depends on the complexity of the program under attack and the types of protection the program has in place. For instance, if a program is protected via dynamically verified checksums of the program input, then active attacks require finding and disabling these checksumming instructions, which could be more costly than a passive attack. ¶ 3.5 Summary of MATE Attack Classification ¶ Table 2 provides a summary of the classification dimensions described above along with the possible discrete values that each dimension can take. In the remainder of this chapter we will refer to these dimensions when describing attack implementations. ¶  ¶ Table 2 ¶ DimensionPossible Values Attack typeCode understanding Data recovery Location recovery DynamicsStatic Dynamic Code interpretationSyntactic Semantic AlterationPassive Active ¶ 4 Survey of Obfuscation Transformations ¶ Obfuscation transformations can be implemented in different ways, i.e., the obfuscation transformation gives only a high-level description (e.g., pseudo-code) and it leaves it up to the obfuscation engine developer to take concrete implementation decisions. This section provides a description of the abstract idea behind common obfuscation transformations, it does not focus on any particular implementation of an obfuscation engine. This state-of-the-art survey groups obfuscation transformation techniques according to their target of transformation, namely, data and code. We also give examples using code snippets written in C, JavaScript, and Assembly language, to illustrate the transformations. ¶  ¶ 4.1 Constant Data Transformations ¶ 4.1.1 Opaque Predicates ¶  ¶ Collberg et al. \[ ¶ Opaque predicates can be created based on mathematical formulas which are hard to solve statically, but they can also be built using any other problem which is difficult to compute statically, e.g., aliasing. Aliasing is represented by a state of a program where a certain memory location is referenced by multiple symbols (e.g., variables) in the program. Several works in literature show that pointer alias analysis (i.e., deciding at any given point during execution, which symbols may alias a certain memory location) is undecidable \[ ¶ Fig. 2 Opaque expressions based on linked lists. ¶ One extension of opaque predicates was made by Palsberg et al. \[ ¶ Attacks: Due to their popularity, opaque predicates have been the target of several MATE attacks published in the literature. Dalla Preda et al. \[ ¶ 4.1.2 Convert Static Data to Procedural Data (a.k.a. Encode Literals) ¶ A simple way of obfuscating a hard-coded constant is to convert it into a function (program) that produces the constant at runtime \[ ¶ Listing 1 ¶ Code Before Encode Literals ¶   1 int main(int ac, char\* av \[\]) {  2      int a = 1;  3      // do stuff  4      return 0;  5  } ¶ Listing 2 ¶ Code After Encode Literals ¶   1 int main(int ac, char\* av \[\]) {  2      double s = sin(atof (av \[1\]));  3      double c = cos(atof (av \[1\]));  4      int a = (int) (s \* s + c \* c);  5      // do stuff  6      return 0;  7  } ¶ Attacks: This obfuscation transformation has been successfully attacked by the two semantic attacks of Banescu et al. \[ ¶ 4.1.3 Mixed Boolean-Arithmetic ¶ Zhou et al. \[ ¶ \\begin{array}{r}
{f(x) = 727318528x^{2} + 3506639707x + 6132886\\;(\\operatorname{mod}\\; 2^{32}).} \\\\
\\end{array} ¶ si2\_e ¶ The output of computing f(k) is 1704256593. This value can be inverted back to the value of k during runtime by using the following polynomial: ¶ \\begin{array}{r}
{f^{- 1}(x) = 1428291584x^{2} + 1257694419x + 4129091678\\;(\\operatorname{mod}\\; 2^{32}).} \\\\
\\end{array} ¶ si3\_e ¶ Zhou et al. \[ ¶ \\begin{array}{r}
{2y = - 2(x \\vee ( - y - 1)) - (( - 2x - 1) \\vee ( - 2y - 1)) - 3.} \\\\
\\end{array} ¶ si4\_e ¶ This identity makes the computation of a constant value (i.e., 2y, which is the value of f(k) in the running example), dependent on a program input value, i.e., x. Note that this relation can be applied multiple times for different program inputs. The resulting Boolean-arithmetic relation is further obfuscated by applying the following identity: ¶ \\begin{array}{r}
{x + y = (x \\oplus y) - (( - 2x - 1) \\vee ( - 2y - 1)) - 1.} \\\\
\\end{array} ¶ si5\_e ¶ Making the computation of f−1(k) dependent on three 32-bit integer input arguments of the program and applying the second Boolean-arithmetic relation multiple times gives the code in Listing 3, which dynamically computes the original value of k = 0x87654321. Note that in Listing 3, variables a, b, d, and e are input dependent, common subexpressions of the MBA expression of k. ¶ Listing 3 ¶ Hiding the Value of k = 0x876554321 Using Mixed Boolean-Arithmetic ¶   1 int main(int argc, char\* argv \[\]) { // compiled on a 32−bit architecture  2 int x = atoi (argv \[1\]);  3 int x1 = atoi (argv \[2\]);  4 int x2 = atoi (argv \[3\]);  5  6 int a = x\*(x1 | 3749240069);  7 int b = x\*((−2\*x1 − 1) | 3203512843);  8 int d = ((235810187\*x + 281909696− x2) ˆ (2424056794+x2));  9 int e = ((3823346922\*x + 3731147903+2\*x2) | (3741821003 + 4294967294\*x2));1011 int k = 135832444\*d + 4159134852\*e + 272908530\*a + 409362795\*x + 136454265\*b + 2284837645 + 415760384\*a\*b + 2816475136\*a\*d + 1478492160\*a\*e + 3325165568\*b\*b + 2771124224\*b\*x + 1247281152\*a\*x + 1408237568\*b\*d + 2886729728\*b\*e + 4156686336\*x\*x + 4224712704\*x\*d + 415760384\*a\*a + 70254592\*x\*e + 1428160512\*d\*d + 1438646272\*d\*e + 1428160512\*e\*e;12 // do stuff13 return 0;14 } ¶ Attacks: Guinet et al. \[ ¶ 4.1.4 White-Box Cryptography ¶ This transformation was pioneered by Chow et al. \[ ¶ The idea behind the white-box approach in \[ ¶ Listing 4 ¶ 8-Bit XOR With MSB of Secret Key ¶   1 char xor (char input) {  2      return input ˆ 0x53;  3 } ¶ Listing 5 ¶ LUT-Based 8-Bit XOR ¶   1 char lut \[256\] = {  2      0x53, 0x52, 0x51, . . ., 0x5C,  3      0x43, 0x42, 0x41, . . ., 0x4C,  4      0x73, 0x72, 0x71, . . ., 0x7C,  5           |                                                      |  6      0xA3, 0xA2, 0xA1, . . ., 0xAC  7 };  8      9 char xor (char input) {10      return lut \[input\];11 } ¶ LUTs can also be used to encode random invertible bijective functions, which are used to further obfuscate the LUTs representing internal AES functions. This is necessary because an attacker could extract the MSB of the secret key from the LUT in Listing 5. In order to hide the key, WBC proposes to generate a random permutation of 256 bytes and apply it to the LUT. To be able to use the resulting LUT, the inverse permutation would be composed with the next operation following the XOR during AES encryption. Since the attacker would not know the randomly generated permutation value, she/he would no longer be able to extract the key directly from the LUT. Converting several steps of an AES cipher to LUT-based implementations and then applying random permutations to these LUTs leads to an implementation which is much more compact than the huge LUT with 2128 entries of 128-bits. Typically, the size of a WB-AES cipher is around a few megabytes. The same idea can also be applied to other ciphers as well. ¶ Attacks: Several MATE attacks on WB-DES \[ ¶ 4.1.5 One-Way Transformations ¶ One-way transformations refer to mapping data values from one domain to another domain (e.g., f(i) = i′), without needing to perform the inverse mapping f−1(i′) during runtime. This means that f must be homomorphic w.r.t. the operations performed using i. For instance, a cryptographic hash function such a secure hash algorithm (SHA), e.g., SHA-256 (denoted H) may be used as a one-way transformation. H can map a hard-coded string password s to a 256-bit value, i.e., v = H(s). Generally, the only operation performed with a hard-coded password is an equality check with an external user input i. Hence, v does not need to be mapped back to s during runtime. Instead, the program can compute v′ = H(i) and verify the equality between the hard-coded value v and the dynamically computed v′. Since the implementation of H for cryptographic hash functions does not disclose the inverse mapping H−1, the MATE attacker is forced to either guess s or identify the equality comparison and modify it such that it always indicates equality regardless of i. The latter tampering attack can be hampered if the code of the equality check is highly obfuscated, which can be achieved by applying code obfuscation transformations (see Section 4.3). ¶ Attacks: More than a decade ago, Wang et al. \[ ¶ 4.2 Variable Data Transformations ¶ 4.2.1 Split Variables ¶ The idea behind this transformation is to substitute one variable by two or more variables \[ ¶ Listing 6 ¶ Split Variable ¶   1 char b1, b2, b3, b4; // i = b1, b2, b3, b4  2      3 int add(int a) {  4      return a + ((b1 << 8 + b2)  5                                          << 8 + b3)  6                                          << 8 + b4;  7 } ¶  ¶ Attacks: Slowinska et al. \[ ¶ 4.2.2 Merge Variables ¶ Two or more variables can be merged into a single variable, if the ranges of the combined variables fit within the precision of the compound variable \[ ¶ Listing 7 ¶ Merged Variables ¶   1 int i; // i = b1, b2, b3, b4  2 char add\_b1(char a) {  3      return a + (i >> 24);  4 }  5 // . . .  6 char add\_b4(char a) {  7      return a + (i & 0xff);  8 } ¶ Attacks: The previously mentioned MATE attack proposed by Slowinska et al. \[ ¶ 4.2.3 Restructure Arrays ¶ Similarly to variables, arrays can be split or merged \[ ¶ Listing 8 ¶ Folded Array ¶   1 int folded \[10\] \[10\] = {{1, 2, . . ., 10},  2                                                       {11, 12, . . ., 20},  3                                                      . . .  4                                                       {91, 92, . . ., 100}}; ¶ Listing 9 ¶ Flattened Array ¶   1 int flattened \[100\] = {1, 2, . . ., 100}; ¶ Attacks: Slowinska et al. \[ ¶ Listing 10 ¶ Original Basic Block ¶   1 mov eax, 0x10h  2 mul ebx, eax  3 cmp ebx, 0x10h  4 je 0x12345678 ¶ Listing 11 ¶ Basic Block After Reordering Variables ¶   1 mov edx, 0x10h  2 mul ebx, edx  3 cmp ebx, 0x10h  4 je 0x12345678 ¶ 4.2.4 Reorder Variables ¶ This transformation changes the location or the name of variables in the program code, by permuting or substituting them \[ ¶ Attacks: Griffin et al. \[ ¶ 4.2.5 Dataflow Flattening ¶ Dataflow flattening, proposed by Anckaert et al. \[ ¶ 1. The MMU allocates a new memory region on the heap, for a given variable.2. It copies the value of that variable to the new memory region.3. The MMU updates all pointers from the old to the new memory region of the variable.4. Finally, it deallocates the old memory region. ¶ In addition to reordering the data on the heap, dataflow flattening also proposes moving all local variables from the stack to the heap and scrambling pointers to hide the relation between the different pointers returned to the program. This transformation has a resilience against MATE attacks, nonetheless, its execution overhead is also high. ¶ Attacks: At the time of writing this chapter, we are not aware of reported attacks on this obfuscation technique in the literature. ¶ 4.2.6 Randomized Stack Frames ¶ This transformation assigns each newly allocated stack frame a random position on the stack \[ ¶ Listing 12 ¶ Original Function Prolog and Epilog ¶   1 push ebp             ; save previous stack frame  2 mov ebp, esp   ; base of this stack frame  3 . . .                      ; function body  4 mov esp, ebp    ; discard this stack frame  5 pop ebp               ; restore previous frame  6 ret ¶ Listing 13 ¶ Prologue and Epilogue After Stack Randomization ¶   1 sub esp, 0x43  2 push ebp  3 sub esp, 0x5f  4 mov ebp, esp  5 . . .  6 mov esp, ebp  7 add esp, 0x5f  8 pop ebp  9 add esp, 0x4310 ret ¶ Attacks: Strackx et al. \[ ¶  ¶ 4.2.7 Data Space Randomization ¶ Cadar et al. \[ ¶ Listing 14 shows a C-code snippet performing a simple summation operation. Listing 15 shows how the function from Listing 14, after it is obfuscated using DSR. Note that each value is XOR-ed with a random mask, which must be used for decryption when performing the addition operation on line 7 of Listing 15. Even though the actual values of the variables are now hidden by masking, the security issue is shifted to hiding the masks or the relation between values and masks from MATE attackers. This can be achieved by applying other obfuscation transformations on top of DSR. DSR is reported to introduce an average run-time overhead of 15% and it can protect against buffer- and heap-overflow attacks. ¶ Listing 14 ¶ Original Addition Function ¶   1 int a = 5;  2 int b = 10;  3 . . .  4 int sum = a + b; ¶ Listing 15 ¶ Addition Function Obfuscated With DSR ¶   1 int mask\_a = rand ();  2 int a = 5 ˆ mask\_a;  3 int mask\_b = rand ();  4 int b = 10 ˆ mask\_b;  5 . . .  6 int mask\_sum = rand ();  7 int sum = ((a ˆ mask\_a) + (b ˆ mask\_b)) ˆ mask\_sum; ¶ Attacks: The attack of Strackx et al. \[ ¶ 4.3 Code Logic Transformations ¶ 4.3.1 Instruction Reordering ¶ This technique targets sequences of instructions, which when permuted, do not alter the original program execution \[ ¶ Listing 16 ¶ Code Before Instruction Reordering ¶   1 mov eax, ebx  2 add ecx, edx  3 add eax, ecx  4 . . . ¶  ¶ Listing 17 ¶ Code After Instruction Reordering ¶   1 add ecx, edx  2 mov eax, ebx  3 add eax, ecx  4 . . . ¶ Attacks: Zhang et al. \[ ¶ 4.3.2 Instruction Substitution ¶ This technique (first mentioned in \[ ¶ Listing 18 ¶ Assembly Code#1 Performing Swap ¶   1 mov edx, eax  2 mov eax, ebx  3 mov ebx, edx ¶ Listing 19 ¶ Assembly Code#2 Performing Swap ¶   1 push eax  2 push ebx  3 pop eax  4 pop ebx ¶ Attacks: The code understanding and data recovery attack of Banescu et al. \[ ¶ 4.3.3 Encode Arithmetic ¶ This technique is proposed by Collberg \[ ¶ Listing 20 ¶ Code Before Encode Arithmetic ¶   1 int main(int ac, char\* av \[\]) {  2      int x = atoi (av \[1\]);  3      int y = atoi (av \[2\]);  4      int w = atoi (av \[3\]);  5      int z = x + y + w;  6      // do stuff  7      return 0;  8 } ¶ Listing 21 ¶ Code After Encode Arithmetic ¶   1 int main(int ac, char\* av \[\]) {  2      int x = atoi (av \[1\]);  3      int y = atoi (av \[2\]);  4      int w = atoi (av \[3\]);  5      int z = (((x ˆ y) + ((x & y) << 1)) | w) +  6                       (((x ˆ y) + ((x & y) << 1)) & w);  7      // do stuff  8      return 0;  9 } ¶ Attacks: The drawback of this approach is that there are a limited number of such Boolean-arithmetic identities available in the literature \[ ¶ Listing 22 ¶ Code Before Inserting Garbage Code ¶   1 int sum = 0;  2 for (i = 0; i < arr\_len; i++)  3      sum += arr \[i\];  4 int average = sum / arr\_len; ¶ 4.3.4 Garbage Insertion ¶ This technique implies inserting arbitrary sequences of instructions that are independent of the data flow of the original program and do not affect its input–output (IO) behavior (functionality) \[ ¶ Listing 23 ¶ Code After Inserting Garbage Code ¶   1 int sum = 0;  2 int prod = 1;  3 for (i = 0; i < arr\_len; i++) {  4      sum += arr \[i\];  5      prod \*= arr \[i\];  6 }  7 int average = sqrt (prod);  8 average = sum / arr\_len; ¶ Attacks: Performing the generic attack based on taint analysis, proposed by Yadegari et al. \[ ¶ 4.3.5 Insert Dead Code ¶ This transformation was first proposed by Collberg et al. \[ ¶ Listing 24 ¶ Code Before Inserting Dead Code ¶   1 int main(int ac, char\* av \[\]) {  2      int x = atoi (av \[1\]);  3      int y = sqrt (x);  4      // do stuff  5      return 0;  6 } ¶ Listing 25 ¶ Code After Inserting Dead Code ¶   1 int main(int ac, char\* av \[\]) {  2      int x = atoi (av \[1\]);  3      int y;  4      if (x\*x + x % 2 == 0)  5           y = sqrt(x);  6      else  7           y = x\*x;  8      // do stuff  9      return 0;10 } ¶ Attacks: Along with the previously presented attacks by Salem and Banescu \[ ¶ 4.3.6 Adding and Removing Function Calls ¶ These two techniques were first proposed by Cohen \[ ¶ (1) selecting an arbitrary sequence of instructions,(2) creating a subroutine using that sequence, and(3) finally, substituting the original sequence with a call to that subroutine. ¶ Removing a call to a subroutine implies ¶ (1) substitute all calls to a subroutine with the body of that subroutine and(2) delete the subroutine. ¶ Listing 26 shows a code snippet that contains a function, while Listing 27 shows a code snippet where this function has been removed. The reverse transformation from Listings 27 to 26 is adding function calls. These transformations cause changes in the structure of a program, which creates more complexity for MATE attacks. The cost of this technique grows or decreases with the number of inserted and removed subroutine calls, respectively. This method has been extended by Banescu et al. \[ ¶ Listing 26 ¶ Add Function Calls ¶   1 int foo (int a, int b) {  2      return a + b;  3 }  4 . . .  5 int c = foo (a, b + 1); ¶ Listing 27 ¶ Remove Function Calls ¶   1 int c = a + b + 1; ¶ Attacks: We have already mentioned the attack of Zhang et al. \[ ¶ 4.3.7 Loop Transformations ¶ Several loop transformations have been proposed as compiler optimization passes by Bacon et al. \[ ¶ Attacks: The dynamic code understanding attack by Slowinska et al. \[ ¶ 4.3.8 Adding and Removing Jumps ¶ These techniques change the control-flow of the program by adding spurious jumps or removing existing jumps \[ ¶ (1) a jump to a random position,(2) followed by I, and(3) a jump to the instruction immediately following I in the original version of the program. ¶ An example is illustrated in Listing 29, where the code from Listing 28 has been transformed by adding two unconditional jumps to labels L1 and L2. Removing jump instructions may also be done if it does not alter the original semantics of the program, e.g., unconditional jumps may be removed and the code from the address of the jump, merged with the code preceding the unconditional jump. An example is shown in Listing 28, where all jumps from the code in Listing 29 have been removed. However, in practice adding jumps is more frequently employed in order to increase the complexity of the MATE attack. The transformation space of this technique is bounded by the length of the program it is applied to. The cost of this method grows (decreases) with the number of inserted (removed) jump instructions. The resilience of adding jumps can be increased by further obfuscating the addresses of the jumps using data obfuscation techniques such as opaque expressions or converting static data to procedural data. ¶ Listing 28 ¶ Code With Jumps Removed ¶   1 mov edx, eax  2 mov eax, ebx  3 mov ebx, edx  4 . . . ¶ Listing 29 ¶ Code With Jumps Added ¶   1        mov edx, eax  2        jmp L1  3       . . .  4 L2:mov ebx, edx  5       . . .  6 L1:mov eax, ebx  7        jmp L2  8       . . . ¶ Attacks: If the target of the added jumps are not made dependent on input values using opaque expressions, then they are trivial to bypass using the already mentioned dynamic attack of Yadegari et al. \[ ¶ 4.3.9 Program Encoding ¶ This technique keeps one or more instructions encoded (i.e., encrypted \[ ¶ Attacks: Tang et al. \[ ¶ 4.3.10 Self-Modifying Code ¶ This technique has been discussed in several works \[ ¶ Fig. 3 Self-modifying code via function templates and edit scripts. ¶ Attacks: Self-modifying code can be effective against dynamic-analysis attack, which aim to break the integrity of the code (e.g., via dynamic code patching), if the executed instructions are different in different runs of the program with the same inputs. However, Nguyen et al. \[ ¶ 4.3.11 Virtualization Obfuscation ¶ This technique is related to the program encoding technique, because it also implies an encoding of instructions \[ ¶ Listing 30 ¶ Point Function Program ¶   1 int main(int argc, char\* argv \[\]) {       // Virtualization bytecode :  2      char branch\_cond = 1;                                 // a5 00 07  3      4      branch\_cond &= argv \[1\] \[0\] == ’1’;   // 87 00 00 02  5      branch\_cond &= argv \[1\] \[1\] == ’2’;   // 87 00 01 03  6      branch\_cond &= argv \[1\] \[2\] == ’3’;   // 87 00 02 04  7      branch\_cond &= argv \[1\] \[3\] == ’4’;   // 87 00 03 05  8      branch\_cond &= argv \[1\] \[4\] == ’5’;   // 87 00 04 06  9    10      if (branch\_cond)                                            // 1f 00 0211           printf ("You win !∖n");                         // 03 0012      return 0;                                                            // 42 0113 } ¶ 1. Map variables, function parameters, and constants to entries in a common data array, which represents the memory of the interpreter. This array is initialized on lines 3–4 in Listing 31. Its first position represents the branch\_cond variable from Listing 30 and the following entries represent constants such as the return value, the ASCII codes of the characters from “1” to “5” and logical true encoded as 1.2. Map all statements in a function to a new randomly chosen language, which represents the instruction set architecture (ISA) of the interpreter. In our example the ISA is defined by:  ¶ • Variable assignment is encoded using 3 bytes, namely, the opcode (0xa5) and the index of the left- and right-hand operands inside the data array.• Equality comparison, followed by applying the logical AND operation to between the result and another variable. Examples of such instructions are shown on lines 4–5 in Listing 30. Such an instruction is encoded using 4 bytes, namely, the opcode (0x87), the variable to which the Boolean value is assigned and the two other byte values which are compared for equality.• Conditional branch statements are encoded using 3 bytes, namely, the opcode (0x1f), the Boolean variable which is tested and the number of bytes to jump over if the variable is false.• Printing a string on standard output is encoded using 2 bytes, namely, the opcode (0x03) and the index of the string to be printed in the list of hard-coded strings of the function. In our example the list of hard-coded strings contains only one string and is defined on line 2 of Listing 31.• The return instruction is encoded using 2 bytes, namely, the opcode (0x42) and the value that should be returned by the program. ¶ Now we can write virtualization bytecode corresponding to the C program in Listing 30, which is shown in the comments of the code from the same listing.3. Store the encoded bytecode inside the code array, which is initialized on lines 5–9 in Listing 31.4. Create an interpreter for the previously generated ISA, which can execute the instructions in the code array using the data array as its memory. The input–output behavior of this execution must be the same as that of the original program. The interpreter can be seen on lines 11–32 of Listing 31. It consists of an infinite while loop, which has a switch statement inside. Each case section of the switch statement is an opcode handler, i.e., each possible opcode in the bytecode program is processed by a dedicated part of the interpreter. The current instruction to be processed by the interpreter is indicated by an integer variable of the interpreter called the virtual program counter (VPC). The VPC is used to index the instructions in the code array and it is initialized with the offset of the first instruction in that array (line 10). In every instruction handler the operands of the current instruction are used to perform the operation(s) corresponding to this instruction. Afterward, the VPC is set to the offset of the following bytecode instruction to be executed. This interpreter should be augmented with cases representing bogus opcodes for all possible byte values in order to increase the resilience against MATE attacks. ¶ Listing 31 ¶ Point Function Program Obfuscated With Virtualization ¶   1 int main(int argc, char\* argv \[\]) {  2      char const \*strings = "You win !∖0";  3      unsigned char data \[8\] = {0,     // branch\_cond var  4             0, 49, 50, 51, 52, 53, 1}; // constants  5      unsigned char code \[30\] = {0xa5, 0x00, 0x07, 0x87, 0x00,  6             0x00, 0x02, 0x87, 0x00, 0x01, 0x03, 0x87,  7             0x00, 0x02, 0x04, 0x87, 0x00, 0x03, 0x05,  8             0x87, 0x00, 0x04, 0x06, 0x1f, 0x00, 0x02,  9             0x03, 0x00, 0x42, 0x01};10      int vpc = 0;11      while (1)12      switch (code \[vpc\]) {13           case 0xa5 : // variable assignment14                data \[code \[vpc +1\]\] = data \[code \[vpc +2\]\];15                vpc += 3;16                break;17           case 0x87 : // equality comparison plus and18                data \[code \[vpc +1\]\] &=19                     (argv \[1\] \[code \[vpc +2\]\] == data \[code \[vpc +3\]\]);20                vpc += 4;21                break;22           case 0x1f : // i f statement23                vpc += (data \[code \[vpc +1\]\]) ? 0 : data \[code \[vpc +2\]\];24                vpc += 3;25                break;26           case 0x03 : // printf string27                printf ("% s∖n", strings + code \[vpc +1\]);28                vpc += 2;29                break;30           case 0x42 : // return31                return data \[code \[vpc +1\]\];32      }33 } ¶  ¶ Together with virtualization a wide range of additional data and code obfuscation transformations can be applied. Banescu et al. \[ ¶ Attacks: Kinder \[ ¶ 4.3.12 Control Flow Flattening ¶ Wang et al. \[ ¶ Listing 32 ¶ Code Before Control Flow Flattening (CFF) ¶   1 int gcd (int a, int b){  2      while (a != b)  3           if (a > b)  4               a = a − b;  5           else  6               b = b − a;  7      return a;  8 } ¶ Listing 33 ¶ Code After CFF ¶   1 int gcd (int a, int b){  2 int next = 0;  3 while (1) {  4      switch (next) {  5           case 0:  6                if (a != b) next = 1;  7                else next = 2;  8                break;  9           case 1:  10             if (a > b) next = 3;  11              else next = 4;  12              break;  13         case 2: return a;  14              break;  15         case 3: a = a − b; next = 0;  16              break;  17         case 4: b = b − a; next = 0;  18              break;  19         default :  20              break;  21 }}} ¶ Attacks: Udupa el al. \[ ¶ 4.3.13 Branch Functions ¶ Linn and Debray \[ ¶ Listing 34 ¶ Code Before Branch Functions ¶   1        mov edx, eax  2        jmp L1  3       . . .  4 L2:mov ebx, edx  5        jmp L3  6       . . .  7 L1:mov eax, ebx  8        jmp L2  9 L3:. . . ¶ Listing 35 ¶ Code After Branch Functions ¶   1        mov edx, eax  2        push 1  3        call f  4       . . .  5 L2:mov ebx, edx  6        push 3  7        call f  8       . . .  9 L1:mov eax, ebx10        push 211        call f12 L3:. . . ¶ Schrittwieser and Katzenbeisser \[ ¶ Attacks: Kruegel et al. \[ ¶ 4.4 Code Abstraction Transformations ¶ 4.4.1 Merging and Splitting Functions ¶ These two techniques are the code correspondents to the data obfuscation transformations of merging and splitting variables \[ ¶ Listing 36 ¶ Splitting Functions ¶   1 func1 (int a, int b) {  2      x = 4;  3      if (a < 3)  4           x = x + 6;  5      x \*= b;  6 }  7      8 func2 (int a, int c) {  9      y = a + 12;10      y = y/c;11 } ¶  ¶ Listing 37 ¶ Merging Functions ¶   1 func3 (int a, int b, int c) {  2      if (c % 2 == 0) {  3           x = 4;  4           if (a < 3)  5               x = x + 6;  6           x \*= b;  7      } else {  8           y = a + 12;  9           y = y/b;10      }11 } ¶ Attacks: Rugaber et al. \[ ¶ 4.4.2 Remove Comments and Change Formatting ¶ This transformation is only applicable to programs which are delivered as source code (e.g., JavaScript). Comments are removed if they exist and all space, tab, and newline characters are also removed, which results in a continuous string of code which is more potent against human attackers, than the original code. An example is shown in Listing 39, which is the result of removing comments and all formatting of the code from Listing 38. The original formatting and comments cannot be recovered \[ ¶ Listing 38 ¶ Original JavaScript Code ¶   1 function NewObject(prefix) {  2      var count = 0;  3      // This function generates a pop−up  4      this . SayHello = function (msg) {  5           count++;  6           alert (prefix+ msg);  7      }  8 }  9 var obj = new NewObject("Message : ");10 obj . SayHello ("You are welcome . "); ¶ Listing 39 ¶ JavaScript code after removing comments and formatting ¶   1 function NewObject(prefix){var count=0; this \["SayHello"\] = function (msg){count++; alert (prefix + msg)}} var obj = new NewObject("Message : "); obj . SayHello ("You are welcome. ") ¶ Attacks: Bichsel et al. \[ ¶ 4.4.3 Scrambling Identifier Names ¶ This transformation implies changing all symbol names (e.g., variables, constants, functions, classes) into random strings \[ ¶ Listing 40 ¶ Code Before Scrambling Identifiers ¶   1 sum = 0;  2 for (i = 0; i < arr\_len; i++)  3      sum += arr \[i\];  4 average /= arr\_len; ¶ Listing 41 ¶ Code After Scrambling Identifiers ¶   1 za82b547bcb = 0;  2 for (z1c0ab7cf0c = 0; z1c0ab7cf0c < za862d19cbc; z1c0ab7cf0c++)  3      za82b547bcb += zc1c28ca67f \[z1c0ab7cf0c\];  4 z8c8f7c7867 /= za862d19cbc ¶ Attacks: Ceccato et al. \[ ¶ 4.4.4 Removing Library Calls and Programming Idioms ¶ Most programs perform calls to external libraries providing useful data structures (e.g., lists, maps) and algorithms (e.g., sorting, searching). MATE attackers often start by inspecting calls made to external libraries to give a high-level indication of what the program is doing. This transformation implies replacing such dependencies on external libraries with own implementations where possible \[ ¶ Attacks: The machine learning based attack of Bichset et al. \[ ¶ 4.4.5 Modify Inheritance Relations ¶ Programs written in some object-oriented programming languages are distributed in some intermediate format to end-users (e.g., C#, Java). These intermediate formats are only compiled to native code on the client's machine and contain useful object-oriented programming abstractions. In such programs it is important to break the useful abstractions offered by classes, their structure and their relations (e.g., aggregation, inheritance). According to Collberg et al. \[ ¶ Attacks: At the time of writing this chapter there have been no reported attacks on this obfuscation technique in the literature. ¶ 4.4.6 Function Argument Randomization ¶ Randomizing the order of formal parameters of methods and inserting bogus arguments is a technique implemented by tools such as Tigress \[ ¶ Attacks: The static code understanding attack of Zhang et al. \[ ¶ 4.5 Summary of Survey ¶ In the survey presented above, we have enumerated several practical data and code obfuscation transformations. Practical obfuscation does not offer provable security guarantees like cryptographic obfuscation \[ ¶ Table 3 shows an overview and classification of all the obfuscation transformation presented in this section. We note that most of the presented transformations are applicable for all levels of abstraction (i.e., source code, IR, and binary). Most of the presented transformations are applicable at the function unit of transformation, followed closely by the program unit and then by instruction and basic block, both in third place. Only randomized stack frame have an effect on the system unit of transformation, because they change the layout of the stack. Two of the presented techniques are dynamic, meaning that they must allow code pages to be writable during program execution. The number of presented transformations are relatively balanced between the two different targets of transformation and their subcategories, however, code transformations are slightly more numerous. ¶  ¶ Table 3 ¶ Obfuscation TransformationAbstractionUnitDynamicsTarget Opaque predicatesAllFunctionStaticData constant Convert static data to procedural dataAllInstructionStaticData constant Mixed Boolean ArithmeticAllBasic blockStaticData constant White-box cryptographyAllFunctionStaticData constant One-way transformationsAllInstructionStaticData constant Split variablesAllFunctionStaticData variable Merge variablesAllFunctionStaticData variable Restructure arraysSourceProgramStaticData variable Reorder variablesAllBasic blockStaticData variable Dataflow flatteningBinaryProgramStaticData variable Randomized stack framesBinarySystemStaticData variable Data space randomizationAllProgramStaticData variable Instruction reorderingAllBasic blockStaticCode logic Instruction substitutionAllInstructionStaticCode logic Encode ArithmeticAllInstructionStaticCode logic Garbage insertionAllBasic blockStaticCode logic Insert dead codeAllFunctionStaticCode logic Adding and removing callsAllProgramStaticCode logic Loop transformationsSource, IRLoopStaticCode logic Adding and removing jumpsBinaryFunctionStaticCode logic Program encodingAllAll buy systemDynamicCode logic Self-modifying codeAllProgramDynamicCode logic Virtualization obfuscationAllFunctionStaticCode logic Control flow flatteningAllFunctionStaticCode logic Branch functionsBinaryInstructionStaticCode logic Merging and splitting functionsAllProgramStaticCode abstraction Remove comments and change formattingSourceProgramStaticCode abstraction Scrambling identifier namesSourceProgramStaticCode abstraction Removing library calls and programming idiomsAllFunctionStaticCode abstraction Modify inheritance relationsSource, IRProgramStaticCode abstraction Function argument randomizationAllFunctionStaticCode abstraction ¶ t0020 ¶ 5 Discussion ¶ In this section we present an overview of the previous survey and discuss the observations stemming from it. Based on this discussion we identify gaps in the field of software obfuscation which require further investigation/research. ¶ Table 4 provides an overview of the various MATE attacks (already mentioned in the previous section), which have been successfully applied in order to defeat the obfuscation transformations presented in Section 4, w.r.t. the attack dimensions presented in Section 3. These attacks are placed in the cells of Table 4 to indicate the obfuscation transformation(s) they claim to break and where they stand w.r.t. the attack dimensions presented in Section 3. The following observations stem from Table 4: ¶  ¶  ¶ • Some works present attacks which are applicable to multiple obfuscation transformations and multiple attack dimensions. For instance, the attacks by Salem and Banescu \[ ¶  ¶ • Except for comparing different MATE attacks w.r.t. the classification dimensions presented in Section 3, there is no set of standard benchmarks used in the field of software obfuscation, which would allow comparing different attacks to one another. This indicates that more research is necessary in order to be able to compare these attack techniques to each other. Such research is needed for evaluating the strength of different obfuscation transformations. Therefore, the development of: (1) standard obfuscation benchmarks for MATE attacks and (2) standard attack benchmarks for obfuscation transformations is still an open problem in the field of software protection. ¶  ¶  ¶ • It is not shown in Table 4 due to lack of horizontal space, however, there are fewer active attacks than passive attacks. This may be due to the fact that active attacks are often associated with malicious exploitation (e.g., cracking software), which is not ethical for most researchers. However, more research is required in the direction of active attacks in order to enable the development of stronger protection against such attacks. ¶  ¶  ¶ • Also there are fewer attacks which aim to recover the location of data and/or code, in comparison to attacks on code understanding or data recovery. Location attacks are often associated with active attacks; therefore the previous argument applies to this observation as well. ¶  ¶  ¶ • As expected, the majority of data recovery attacks target data obfuscation transformations and the majority of code understanding attacks target code obfuscation transformations. However, there are also some attacks which target both types of transformations, when they are used in combination with each other. Nevertheless, much more research is needed for investigating the strength of combinations of multiple software obfuscation transformations. ¶  ¶  ¶ • Most attacks on obfuscated code are dynamic, because the majority of the obfuscation transformations presented in this paper aim to break static analysis techniques. Similarly, most attacks are semantic because most dynamic attacks are also semantic. However, note that there are also exceptions. Nevertheless, there are relatively few works about static semantic and dynamic syntactic attacks, which indicates a topic that needs further exploration. ¶  ¶  ¶ • Obfuscation transformations which have few or no attacks against them are not an indication that they are more secure. For instance, in the case of dataflow flattening, the most probable reason why there are no attacks against it is because it is too expensive to implement this obfuscation transformation in most practical scenarios. One of the strongest obfuscation transformation categories against MATE attackers are dynamic transformations, however, these transformations generally require making executable code pages in process memory also writable, which opens the door to remote code injection attacks \[ ¶  ¶ • Most attacks published in literature are dynamic, because even if code is statically encrypted/encoded, it must be decrypted/decoded during execution. This is the “Achilles heel” of obfuscation, i.e., code must still be executable, no matter how intricate the code is obfuscated when inspected statically. To prevent dynamic MATE attacks in practice obfuscation is used in combination with antidynamic-analysis techniques such as antidebugging \[ ¶  ¶ • In some contexts, the MATE attacker is not forced to perform static analysis due to antidynamic-analysis techniques, but due to resource constraints. For instance, some malware analysis systems have to analyze millions of instances per day \[ ¶  ¶ Table 4 ¶  ¶  ¶ Overview of Obfuscation Resilience Against MATE Attacks ¶  ¶  ¶  ¶  ¶ Obfuscation Transformation](images/S0065245817300499/f05-01-9780128151198.jpg)

Fig. 1 Classification of protections against MATE attacks proposed in \[ ¶ An obfuscator is in essence a compiler that takes a program as input, and outputs a functionally equivalent program, which is harder to understand and analyze than the input program. The meaning of the phrases “functionally equivalent” and “harder to understand and analyze” will be discussed in this chapter. For instance, some classical compiler optimizations are also considered obfuscation transformations \[ ¶ This chapter presents a tutorial of several popular obfuscation transformations together with illustrative examples. It also mentions the MATE attacks published in the literature, which have been proposed for defeating each obfuscation transformation. The rest of the chapter is structured as follows. [Section 2](#S0065245817300499.xhtml#s0015) presents classification dimensions for obfuscation transformations. [Section 3](#S0065245817300499.xhtml#s0055) presents classification dimensions for MATE attacks. [Section 4](#S0065245817300499.xhtml#s0085) presents a survey of obfuscation transformations and state-of-the-art MATE attacks that claim to break each obfuscation. [Section 5](#S0065245817300499.xhtml#s0270) discusses the current state of software obfuscation vs MATE attacks. [Section 6](#S0065245817300499.xhtml#s0275) presents related work, and [Section 7](#S0065245817300499.xhtml#s0305) concludes the chapter. ¶ ¶ 2 Classification of Code Obfuscation Transformations ¶ Several surveys and taxonomies for software obfuscation have been proposed in literature \[ ¶ 2.1 Abstraction Level of Transformations ¶ One common dimension of code transformations is the level of abstraction at which these transformations have a noticeable effect, i.e., source code, intermediate representation, and binary machine code. Such a distinction is relevant for usability purposes, e.g., a JavaScript developer will mostly be interested in source code-level transformations and a C developer will mainly be interested in binary level. However, none of the previously mentioned taxonomies and surveys classifies transformations according to the abstraction level. This is due to the fact that some obfuscation transformations have an effect at multiple abstraction levels. Moreover, it is common for papers to focus only on a specific abstraction level, disregarding transformations at other levels. ¶ 2.2 Unit of Transformations ¶ Larsen et al. \[ ¶ • Instruction-level transformations are applied to individual instructions or sequences of instructions. This is due to the fact that at the source code level, a code statement can consist of one or more IR or Assembly instructions.• Basic block-level transformations affect the position of one or more basic blocks. Basic blocks are a list of sequential instructions that have a single entry point and end in a branch instruction.• Loop-level transformations alter the familiar loop constructs added by developers.• Function-level transformations affect several instructions and basic blocks of a particular subroutine. Moreover, they may also affect the stack and heap memory corresponding to the function.• Program-level transformations affect several functions inside an application. However, they also affect the data segments of the program and the memory allocated by that program.• System-level transformations target the operating system or the runtime environment and they affect how other programs interact with them. ¶ The unit of transformation is important in practice because developers can choose the appropriate level of granularity according to the asset they must protect. For example, loop-level transformations are not appropriate for hiding data, but they are appropriate for hiding algorithms. However, the same problem, as for the previous classification dimension, arises for the unit of transformation, namely, the same obfuscation transformation may be applicable to different units of transformation. ¶ 2.3 Dynamics of Transformations ¶ The dynamics of transformation—used by Schrittwieser et al. \[ ¶ 2.4 Target of Transformations ¶ The most common dimension for classifying obfuscation transformations is according to the target of transformations. This dimension was first proposed by Collberg et al. \[ ¶ • Data transformations, which change the representation and location of constant values (e.g., numbers, strings, keys) hard-coded in an application, as well as variable memory values used by the application.• Code transformations, which transform the high-level abstractions (e.g., data structures, variable names, indentation) as well as the algorithm and control-flow of the application. ¶ This dimension is important for practitioners, because it indicates the goal of the defender, i.e., whether the defender wants to protect data or code. Note that obfuscation transformations which target data may also affect the layout of the code and its control-flow, however, their target is hiding data, not code. In practice data transformations are often used in combination with code transformations, to improve the resilience of the program against MATE attacks. ¶ 2.4.1 Data Transformations ¶ Data transformations can be divided into two subcategories: ¶ 1. Constant data transformations, which affect static (hard-coded) values. Abstractly, such transformations are encoding functions which take one or more constant data items i (e.g., byte arrays, integer variables), and convert them into one or more data items i′ = f(i). This means that any value assigned to, compared to and based on i is also changed according to the new encoding. There will be a trade-off between resilience on one hand, and cost on the other, because all operations performed on i require computing f^(−1)(i), unless f is homomorphic w.r.t. those operations.2. Variable data transformations, which modify the representation or structure of variable memory values. The goal of such transformations is to hamper the development of automated MATE attacks, which can assume that a certain variable memory value will always have a certain representation or a certain structure (e.g., an integer array of 100 contiguous elements). If such assumptions hold then automated attacks are easier to develop, because they mainly rely on pattern matching. Therefore, by employing the transformations presented in this section, one can raise the bar for these kinds of attacks. ¶ Note that variable transformations are not the transformations that affect the names or the order of variables, but the representation of the data stored in those variables. ¶  ¶ 2.4.2 Code Transformations ¶ Code transformations can also be divided into two subcategories, namely: ¶ 1. Code logic transformations, which affect the control-flow of the program, its ease of readability and maintainability. Such transformations are aimed at adding complexity to the code in order to prevent MATE attackers from understanding what the algorithm(s) implemented by the code are.2. Code abstraction transformations, which destroy programming abstractions, are generally the first hints that MATE attackers use to start reverse engineering a program. ¶ As opposed to constant data transformations, which in some cases perform one-way mappings of data to a completely different domain which requires no interpretation, code transformations must always perform a mapping to the same domain of executable code, because obfuscated code must be able to run on the underlying machine where it is installed. ¶ 2.5 Summary of Obfuscation Transformation Classification ¶ [Table 1](#S0065245817300499.xhtml#t0010) provides a summary of the classification dimensions described above along with the possible discrete values that each dimension can take. In the next section we choose to present a survey of obfuscation transformations classified according to their target of transformation, because it entails a clear partition of transformations. ¶  ¶ Table 1 ¶ DimensionPossible Values  
Abstraction levelSource code  
Intermediate representation  
Binary machine code  
UnitInstruction  
Basic block  
Loop  
Function  
Program  
System  
DynamicsStatic  
Dynamic  
TargetConstant data  
Variable data  
Code logic  
Code abstraction ¶ 3 Classification of MATE Attacks ¶ In contrast to the classification of software protection techniques (see [Section 2](#S0065245817300499.xhtml#s0015)), the classification of MATE attacks has been the topic of relatively few publications \[ ¶ 3.1 Attack Type Dimension ¶ Basile et al. \[ ¶ • The original or a simplified version of the source code. This is always the case for MATE attackers who are interested in intellectual property theft, i.e., stealing a competitor's algorithm.• A statically embedded or dynamically generated data item. Common examples of such data items are decryption keys used by Digital Rights Management (DRM) technologies to play premium content only on authorized devices, for authorized users. However, data items may also include hard-coded passwords, IP addresses, etc.• The sequence of obfuscation transformations and/or tools used to obfuscate (protect) the program, also called metadata. This kind of information is often used by antivirus engines to detect suspicious binaries, based on the fact that several previously seen malware have used the same obfuscation transformations and/or tools.• The location (i.e., lines of code or bytes) of a particular function of the code. For instance, the attacker may be interested in the module which performs premium content decryption in order to copy it and reuse it in another program, without necessarily understanding how it works. ¶ We compare these four information types proposed by Collberg et al. \[ ¶ • Code understanding, which according to its description in the paper maps to the source code information type described above. However, the name of this category suggests a more general attack type than a full recovery of the entire source code, because it could be sufficient to have a partial code understanding. For example, a malware analysis engine can decide that a software is malicious using its observed behavior (e.g., unsolicited calls to premium telephone numbers), which does not require full understanding of the source code. Moreover, metadata recovery also falls inside of this category of code understanding. Therefore, in this chapter we will use this more general category, i.e., code understanding.• Finding the location of data, which maps perfectly onto the data item information type described above. However, the phrase location of data may be mistaken for the location information type. Therefore, this chapter will simply use data item recovery.• Finding the location of program functionality, which maps onto the location information type described above. However, Schrittwieser et al. \[• Extraction of code fragments, which does not directly map onto any of the information items described above. However, we believe that finding the location of program functionality is a prerequisite to this aim of the analyst, because extraction can only be done after the location of the code fragment has been recovered. Therefore, in this chapter we associate this aim of the analyst with the location information type. ¶ In sum, we use the following three categories of attack types with the meanings discussed above: (1) code understanding, (2) data item recovery, and (3) location recovery. ¶ 3.2 Dynamics Dimension ¶ Dynamics is one of the most commonly used classification criteria for automated MATE attacks and it refers to whether the attacked program is executed on a machine or not, i.e.: ¶ • Static analysis attacks do not execute the program on the underlying (physical or virtual) machine. The subject of the analysis is the static code of the program.• Dynamic analysis attacks run the program and record executed instructions, function calls and/or memory states during execution, which are the subject of analysis. ¶ Static attacks are commonly faster than dynamic attacks. However, static analysis attacks do not handle many code obfuscation transformations as well as dynamic analysis attacks. This does not mean that dynamic analysis attacks can handle any kind of obfuscation easily. For instance, it is challenging to dynamically analyze programs employing code transformation techniques that achieve temporal diversity, i.e., the program has significantly different execution traces and/or memory states on every execution. Moreover, dynamic analysis is in general incomplete, i.e., it cannot explore or reason about all possible executions of a program, as opposed to static analysis. ¶ 3.3 Interpretation Dimension ¶ Code interpretation refers to whether the program's code or the artifacts generated using it (e.g., static disassembly, dynamic traces) are treated as text or are interpreted according to a semantic meaning (e.g., operational semantics). Therefore the two types of code interpretation considered in this chapter are ¶ 

¶ *   ¶ • Syntactic attacks which treat the program's code or any other artifacts generated by executing or processing it, as a string of bytes (e.g., characters). For example, pattern matching on static code \[ ¶ 
*   ¶ • Semantic attacks which interpret the code according to some semantics, e.g., denotational semantics, operational semantics, axiomatic semantics, and variations thereof \[ ¶ Syntactic attacks are generally faster than semantic attacks due to the missing layer of abstraction that interprets the code. Coincidentally, most syntactic attacks are performed via static analysis and most semantic attacks are performed via dynamic analysis. However, there are exceptions, e.g., the syntactic analysis of dynamically generated execution traces and semantic static analysis via abstract interpretation \[ ¶ 3.4 Alteration Dimension ¶ Alteration refers to whether the automated MATE attack changes (alters) the code or not. This type of classification is analogous to the message alteration classification of MITM attacks on communication channels. Hence there are two types of code alteration: ¶ • Passive attacks do not make any changes to the code or data of the program. For instance, extracting a secret key or password from a program does not require any code alterations.• Active attacks make changes to the code or data of a program. For example, removing data or code integrity checks (e.g., password checks) require modifying the code of the program. Also “disarming” malware may also involve tampering with its code. ¶ If an attacker's goal can be achieved via either passive or active attacks, then the type of attack used depends on the complexity of the program under attack and the types of protection the program has in place. For instance, if a program is protected via dynamically verified checksums of the program input, then active attacks require finding and disabling these checksumming instructions, which could be more costly than a passive attack. ¶ 3.5 Summary of MATE Attack Classification ¶ [Table 2](#S0065245817300499.xhtml#t0015) provides a summary of the classification dimensions described above along with the possible discrete values that each dimension can take. In the remainder of this chapter we will refer to these dimensions when describing attack implementations. ¶  ¶ Table 2 ¶ DimensionPossible Values  
    Attack typeCode understanding  
    Data recovery  
    Location recovery  
    DynamicsStatic  
    Dynamic  
    Code interpretationSyntactic  
    Semantic  
    AlterationPassive  
    Active ¶ 4 Survey of Obfuscation Transformations ¶ Obfuscation transformations can be implemented in different ways, i.e., the obfuscation transformation gives only a high-level description (e.g., pseudo-code) and it leaves it up to the obfuscation engine developer to take concrete implementation decisions. This section provides a description of the abstract idea behind common obfuscation transformations, it does not focus on any particular implementation of an obfuscation engine. This state-of-the-art survey groups obfuscation transformation techniques according to their target of transformation, namely, data and code. We also give examples using code snippets written in C, JavaScript, and Assembly language, to illustrate the transformations. ¶ 
    
    ¶ 4.1 Constant Data Transformations ¶ 4.1.1 Opaque Predicates ¶ 
    
    ¶ Collberg et al. \[ ¶ Opaque predicates can be created based on mathematical formulas which are hard to solve statically, but they can also be built using any other problem which is difficult to compute statically, e.g., aliasing. Aliasing is represented by a state of a program where a certain memory location is referenced by multiple symbols (e.g., variables) in the program. Several works in literature show that pointer alias analysis (i.e., deciding at any given point during execution, which symbols may alias a certain memory location) is undecidable \[ ¶ ![Fig. 2 Opaque expressions based on linked lists.](images/S0065245817300499/f05-02-9780128151198.jpg "fig:")¶ One extension of opaque predicates was made by Palsberg et al. \[ ¶ Attacks: Due to their popularity, opaque predicates have been the target of several MATE attacks published in the literature. Dalla Preda et al. \[ ¶ 4.1.2 Convert Static Data to Procedural Data (a.k.a. Encode Literals) ¶ A simple way of obfuscating a hard-coded constant is to convert it into a function (program) that produces the constant at runtime \[ ¶ Listing 1 ¶ Code Before Encode Literals ¶   1 int main(int ac, char\* av \[\]) {  2      int a = 1;  3      // do stuff  4      return 0;  5  } ¶ Listing 2 ¶ Code After Encode Literals ¶   1 int main(int ac, char\* av \[\]) {  2      double s = sin(atof (av \[1\]));  3      double c = cos(atof (av \[1\]));  4      int a = (int) (s \* s + c \* c);  5      // do stuff  6      return 0;  7  } ¶ Attacks: This obfuscation transformation has been successfully attacked by the two semantic attacks of Banescu et al. \[ ¶ 4.1.3 Mixed Boolean-Arithmetic ¶ Zhou et al. \[ ¶ $\\begin{array}{r} {f(x) = 727318528x^{2} + 3506639707x + 6132886\\;(\\operatorname{mod}\\; 2^{32}).} \\\\ \\end{array}$ ¶ ![si2\_e](images/S0065245817300499/si2_e.png) ¶ The output of computing f(k) is 1704256593. This value can be inverted back to the value of k during runtime by using the following polynomial: ¶ $\\begin{array}{r} {f^{- 1}(x) = 1428291584x^{2} + 1257694419x + 4129091678\\;(\\operatorname{mod}\\; 2^{32}).} \\\\ \\end{array}$ ¶ ![si3\_e](images/S0065245817300499/si3_e.png) ¶ Zhou et al. \[ ¶ $\\begin{array}{r} {2y = - 2(x \\vee ( - y - 1)) - (( - 2x - 1) \\vee ( - 2y - 1)) - 3.} \\\\ \\end{array}$ ¶ ![si4\_e](images/S0065245817300499/si4_e.png) ¶ This identity makes the computation of a constant value (i.e., 2y, which is the value of f(k) in the running example), dependent on a program input value, i.e., x. Note that this relation can be applied multiple times for different program inputs. The resulting Boolean-arithmetic relation is further obfuscated by applying the following identity: ¶ $\\begin{array}{r} {x + y = (x \\oplus y) - (( - 2x - 1) \\vee ( - 2y - 1)) - 1.} \\\\ \\end{array}$ ¶ ![si5\_e](images/S0065245817300499/si5_e.png) ¶ Making the computation of f^(−1)(k) dependent on three 32-bit integer input arguments of the program and applying the second Boolean-arithmetic relation multiple times gives the code in [Listing 3](#S0065245817300499.xhtml#b0020), which dynamically computes the original value of k = 0x87654321\. Note that in [Listing 3](#S0065245817300499.xhtml#b0020), variables a, b, d, and e are input dependent, common subexpressions of the MBA expression of k. ¶ Listing 3 ¶ Hiding the Value of k = 0x876554321 Using Mixed Boolean-Arithmetic ¶   1 int main(int argc, char\* argv \[\]) { // compiled on a 32−bit architecture  2 int x = atoi (argv \[1\]);  3 int x1 = atoi (argv \[2\]);  4 int x2 = atoi (argv \[3\]);  5  6 int a = x\*(x1 | 3749240069);  7 int b = x\*((−2\*x1 − 1) | 3203512843);  8 int d = ((235810187\*x + 281909696− x2) ˆ (2424056794+x2));  9 int e = ((3823346922\*x + 3731147903+2\*x2) | (3741821003 + 4294967294\*x2));1011 int k = 135832444\*d + 4159134852\*e + 272908530\*a + 409362795\*x + 136454265\*b + 2284837645 + 415760384\*a\*b + 2816475136\*a\*d + 1478492160\*a\*e + 3325165568\*b\*b + 2771124224\*b\*x + 1247281152\*a\*x + 1408237568\*b\*d + 2886729728\*b\*e + 4156686336\*x\*x + 4224712704\*x\*d + 415760384\*a\*a + 70254592\*x\*e + 1428160512\*d\*d + 1438646272\*d\*e + 1428160512\*e\*e;12 // do stuff13 return 0;14 } ¶ Attacks: Guinet et al. \[ ¶ 4.1.4 White-Box Cryptography ¶ This transformation was pioneered by Chow et al. \[ ¶ The idea behind the white-box approach in \[ ¶ Listing 4 ¶ 8-Bit XOR With MSB of Secret Key ¶   1 char xor (char input) {  2      return input ˆ 0x53;  3 } ¶ Listing 5 ¶ LUT-Based 8-Bit XOR ¶   1 char lut \[256\] = {  2      0x53, 0x52, 0x51, . . ., 0x5C,  3      0x43, 0x42, 0x41, . . ., 0x4C,  4      0x73, 0x72, 0x71, . . ., 0x7C,  5           |                                                      |  6      0xA3, 0xA2, 0xA1, . . ., 0xAC  7 };  8      9 char xor (char input) {10      return lut \[input\];11 } ¶ LUTs can also be used to encode random invertible bijective functions, which are used to further obfuscate the LUTs representing internal AES functions. This is necessary because an attacker could extract the MSB of the secret key from the LUT in [Listing 5](#S0065245817300499.xhtml#b0030). In order to hide the key, WBC proposes to generate a random permutation of 256 bytes and apply it to the LUT. To be able to use the resulting LUT, the inverse permutation would be composed with the next operation following the XOR during AES encryption. Since the attacker would not know the randomly generated permutation value, she/he would no longer be able to extract the key directly from the LUT. Converting several steps of an AES cipher to LUT-based implementations and then applying random permutations to these LUTs leads to an implementation which is much more compact than the huge LUT with 2^(128) entries of 128-bits. Typically, the size of a WB-AES cipher is around a few megabytes. The same idea can also be applied to other ciphers as well. ¶ Attacks: Several MATE attacks on WB-DES \[ ¶ 4.1.5 One-Way Transformations ¶ One-way transformations refer to mapping data values from one domain to another domain (e.g., f(i) = i′), without needing to perform the inverse mapping f^(−1)(i′) during runtime. This means that f must be homomorphic w.r.t. the operations performed using i. For instance, a cryptographic hash function such a secure hash algorithm (SHA), e.g., SHA-256 (denoted H) may be used as a one-way transformation. H can map a hard-coded string password s to a 256-bit value, i.e., v = H(s). Generally, the only operation performed with a hard-coded password is an equality check with an external user input i. Hence, v does not need to be mapped back to s during runtime. Instead, the program can compute v′ = H(i) and verify the equality between the hard-coded value v and the dynamically computed v′. Since the implementation of H for cryptographic hash functions does not disclose the inverse mapping H^(−1), the MATE attacker is forced to either guess s or identify the equality comparison and modify it such that it always indicates equality regardless of i. The latter tampering attack can be hampered if the code of the equality check is highly obfuscated, which can be achieved by applying code obfuscation transformations (see [Section 4.3](#S0065245817300499.xhtml#s0160)). ¶ Attacks: More than a decade ago, Wang et al. \[ ¶ 4.2 Variable Data Transformations ¶ 4.2.1 Split Variables ¶ The idea behind this transformation is to substitute one variable by two or more variables \[ ¶ Listing 6 ¶ Split Variable ¶   1 char b1, b2, b3, b4; // i = b1, b2, b3, b4  2      3 int add(int a) {  4      return a + ((b1 << 8 + b2)  5                                          << 8 + b3)  6                                          << 8 + b4;  7 } ¶  ¶ Attacks: Slowinska et al. \[ ¶ 4.2.2 Merge Variables ¶ Two or more variables can be merged into a single variable, if the ranges of the combined variables fit within the precision of the compound variable \[ ¶ Listing 7 ¶ Merged Variables ¶   1 int i; // i = b1, b2, b3, b4  2 char add\_b1(char a) {  3      return a + (i >> 24);  4 }  5 // . . .  6 char add\_b4(char a) {  7      return a + (i & 0xff);  8 } ¶ Attacks: The previously mentioned MATE attack proposed by Slowinska et al. \[ ¶ 4.2.3 Restructure Arrays ¶ Similarly to variables, arrays can be split or merged \[ ¶ Listing 8 ¶ Folded Array ¶   1 int folded \[10\] \[10\] = {{1, 2, . . ., 10},  2                                                       {11, 12, . . ., 20},  3                                                      . . .  4                                                       {91, 92, . . ., 100}}; ¶ Listing 9 ¶ Flattened Array ¶   1 int flattened \[100\] = {1, 2, . . ., 100}; ¶ Attacks: Slowinska et al. \[ ¶ Listing 10 ¶ Original Basic Block ¶   1 mov eax, 0x10h  2 mul ebx, eax  3 cmp ebx, 0x10h  4 je 0x12345678 ¶ Listing 11 ¶ Basic Block After Reordering Variables ¶   1 mov edx, 0x10h  2 mul ebx, edx  3 cmp ebx, 0x10h  4 je 0x12345678 ¶ 4.2.4 Reorder Variables ¶ This transformation changes the location or the name of variables in the program code, by permuting or substituting them \[ ¶ Attacks: Griffin et al. \[ ¶ 4.2.5 Dataflow Flattening ¶ Dataflow flattening, proposed by Anckaert et al. \[ ¶ 1. The MMU allocates a new memory region on the heap, for a given variable.2. It copies the value of that variable to the new memory region.3. The MMU updates all pointers from the old to the new memory region of the variable.4. Finally, it deallocates the old memory region. ¶ In addition to reordering the data on the heap, dataflow flattening also proposes moving all local variables from the stack to the heap and scrambling pointers to hide the relation between the different pointers returned to the program. This transformation has a resilience against MATE attacks, nonetheless, its execution overhead is also high. ¶ Attacks: At the time of writing this chapter, we are not aware of reported attacks on this obfuscation technique in the literature. ¶ 4.2.6 Randomized Stack Frames ¶ This transformation assigns each newly allocated stack frame a random position on the stack \[ ¶ Listing 12 ¶ Original Function Prolog and Epilog ¶   1 push ebp             ; save previous stack frame  2 mov ebp, esp   ; base of this stack frame  3 . . .                      ; function body  4 mov esp, ebp    ; discard this stack frame  5 pop ebp               ; restore previous frame  6 ret ¶ Listing 13 ¶ Prologue and Epilogue After Stack Randomization ¶   1 sub esp, 0x43  2 push ebp  3 sub esp, 0x5f  4 mov ebp, esp  5 . . .  6 mov esp, ebp  7 add esp, 0x5f  8 pop ebp  9 add esp, 0x4310 ret ¶ Attacks: Strackx et al. \[ ¶  ¶ 4.2.7 Data Space Randomization ¶ Cadar et al. \[ ¶ [Listing 14](#S0065245817300499.xhtml#b0075) shows a C-code snippet performing a simple summation operation. [Listing 15](#S0065245817300499.xhtml#b0080) shows how the function from [Listing 14](#S0065245817300499.xhtml#b0075), after it is obfuscated using DSR. Note that each value is XOR-ed with a random mask, which must be used for decryption when performing the addition operation on line 7 of [Listing 15](#S0065245817300499.xhtml#b0080). Even though the actual values of the variables are now hidden by masking, the security issue is shifted to hiding the masks or the relation between values and masks from MATE attackers. This can be achieved by applying other obfuscation transformations on top of DSR. DSR is reported to introduce an average run-time overhead of 15% and it can protect against buffer- and heap-overflow attacks. ¶ Listing 14 ¶ Original Addition Function ¶   1 int a = 5;  2 int b = 10;  3 . . .  4 int sum = a + b; ¶ Listing 15 ¶ Addition Function Obfuscated With DSR ¶   1 int mask\_a = rand ();  2 int a = 5 ˆ mask\_a;  3 int mask\_b = rand ();  4 int b = 10 ˆ mask\_b;  5 . . .  6 int mask\_sum = rand ();  7 int sum = ((a ˆ mask\_a) + (b ˆ mask\_b)) ˆ mask\_sum; ¶ Attacks: The attack of Strackx et al. \[ ¶ 4.3 Code Logic Transformations ¶ 4.3.1 Instruction Reordering ¶ This technique targets sequences of instructions, which when permuted, do not alter the original program execution \[ ¶ Listing 16 ¶ Code Before Instruction Reordering ¶   1 mov eax, ebx  2 add ecx, edx  3 add eax, ecx  4 . . . ¶  ¶ Listing 17 ¶ Code After Instruction Reordering ¶   1 add ecx, edx  2 mov eax, ebx  3 add eax, ecx  4 . . . ¶ Attacks: Zhang et al. \[ ¶ 4.3.2 Instruction Substitution ¶ This technique (first mentioned in \[ ¶ Listing 18 ¶ Assembly Code#1 Performing Swap ¶   1 mov edx, eax  2 mov eax, ebx  3 mov ebx, edx ¶ Listing 19 ¶ Assembly Code#2 Performing Swap ¶   1 push eax  2 push ebx  3 pop eax  4 pop ebx ¶ Attacks: The code understanding and data recovery attack of Banescu et al. \[ ¶ 4.3.3 Encode Arithmetic ¶ This technique is proposed by Collberg \[ ¶ Listing 20 ¶ Code Before Encode Arithmetic ¶   1 int main(int ac, char\* av \[\]) {  2      int x = atoi (av \[1\]);  3      int y = atoi (av \[2\]);  4      int w = atoi (av \[3\]);  5      int z = x + y + w;  6      // do stuff  7      return 0;  8 } ¶ Listing 21 ¶ Code After Encode Arithmetic ¶   1 int main(int ac, char\* av \[\]) {  2      int x = atoi (av \[1\]);  3      int y = atoi (av \[2\]);  4      int w = atoi (av \[3\]);  5      int z = (((x ˆ y) + ((x & y) << 1)) | w) +  6                       (((x ˆ y) + ((x & y) << 1)) & w);  7      // do stuff  8      return 0;  9 } ¶ Attacks: The drawback of this approach is that there are a limited number of such Boolean-arithmetic identities available in the literature \[ ¶ Listing 22 ¶ Code Before Inserting Garbage Code ¶   1 int sum = 0;  2 for (i = 0; i < arr\_len; i++)  3      sum += arr \[i\];  4 int average = sum / arr\_len; ¶ 4.3.4 Garbage Insertion ¶ This technique implies inserting arbitrary sequences of instructions that are independent of the data flow of the original program and do not affect its input–output (IO) behavior (functionality) \[ ¶ Listing 23 ¶ Code After Inserting Garbage Code ¶   1 int sum = 0;  2 int prod = 1;  3 for (i = 0; i < arr\_len; i++) {  4      sum += arr \[i\];  5      prod \*= arr \[i\];  6 }  7 int average = sqrt (prod);  8 average = sum / arr\_len; ¶ Attacks: Performing the generic attack based on taint analysis, proposed by Yadegari et al. \[ ¶ 4.3.5 Insert Dead Code ¶ This transformation was first proposed by Collberg et al. \[ ¶ Listing 24 ¶ Code Before Inserting Dead Code ¶   1 int main(int ac, char\* av \[\]) {  2      int x = atoi (av \[1\]);  3      int y = sqrt (x);  4      // do stuff  5      return 0;  6 } ¶ Listing 25 ¶ Code After Inserting Dead Code ¶   1 int main(int ac, char\* av \[\]) {  2      int x = atoi (av \[1\]);  3      int y;  4      if (x\*x + x % 2 == 0)  5           y = sqrt(x);  6      else  7           y = x\*x;  8      // do stuff  9      return 0;10 } ¶ Attacks: Along with the previously presented attacks by Salem and Banescu \[ ¶ 4.3.6 Adding and Removing Function Calls ¶ These two techniques were first proposed by Cohen \[ ¶ (1) selecting an arbitrary sequence of instructions,(2) creating a subroutine using that sequence, and(3) finally, substituting the original sequence with a call to that subroutine. ¶ Removing a call to a subroutine implies ¶ (1) substitute all calls to a subroutine with the body of that subroutine and(2) delete the subroutine. ¶ [Listing 26](#S0065245817300499.xhtml#b0135) shows a code snippet that contains a function, while [Listing 27](#S0065245817300499.xhtml#b0140) shows a code snippet where this function has been removed. The reverse transformation from Listings 27 to 26 is adding function calls. These transformations cause changes in the structure of a program, which creates more complexity for MATE attacks. The cost of this technique grows or decreases with the number of inserted and removed subroutine calls, respectively. This method has been extended by Banescu et al. \[ ¶ Listing 26 ¶ Add Function Calls ¶   1 int foo (int a, int b) {  2      return a + b;  3 }  4 . . .  5 int c = foo (a, b + 1); ¶ Listing 27 ¶ Remove Function Calls ¶   1 int c = a + b + 1; ¶ Attacks: We have already mentioned the attack of Zhang et al. \[ ¶ 4.3.7 Loop Transformations ¶ Several loop transformations have been proposed as compiler optimization passes by Bacon et al. \[ ¶ Attacks: The dynamic code understanding attack by Slowinska et al. \[ ¶ 4.3.8 Adding and Removing Jumps ¶ These techniques change the control-flow of the program by adding spurious jumps or removing existing jumps \[ ¶ (1) a jump to a random position,(2) followed by I, and(3) a jump to the instruction immediately following I in the original version of the program. ¶ An example is illustrated in [Listing 29](#S0065245817300499.xhtml#b0150), where the code from [Listing 28](#S0065245817300499.xhtml#b0145) has been transformed by adding two unconditional jumps to labels L1 and L2. Removing jump instructions may also be done if it does not alter the original semantics of the program, e.g., unconditional jumps may be removed and the code from the address of the jump, merged with the code preceding the unconditional jump. An example is shown in [Listing 28](#S0065245817300499.xhtml#b0145), where all jumps from the code in [Listing 29](#S0065245817300499.xhtml#b0150) have been removed. However, in practice adding jumps is more frequently employed in order to increase the complexity of the MATE attack. The transformation space of this technique is bounded by the length of the program it is applied to. The cost of this method grows (decreases) with the number of inserted (removed) jump instructions. The resilience of adding jumps can be increased by further obfuscating the addresses of the jumps using data obfuscation techniques such as opaque expressions or converting static data to procedural data. ¶ Listing 28 ¶ Code With Jumps Removed ¶   1 mov edx, eax  2 mov eax, ebx  3 mov ebx, edx  4 . . . ¶ Listing 29 ¶ Code With Jumps Added ¶   1        mov edx, eax  2        jmp L1  3       . . .  4 L2:mov ebx, edx  5       . . .  6 L1:mov eax, ebx  7        jmp L2  8       . . . ¶ Attacks: If the target of the added jumps are not made dependent on input values using opaque expressions, then they are trivial to bypass using the already mentioned dynamic attack of Yadegari et al. \[ ¶ 4.3.9 Program Encoding ¶ This technique keeps one or more instructions encoded (i.e., encrypted \[ ¶ Attacks: Tang et al. \[ ¶ 4.3.10 Self-Modifying Code ¶ This technique has been discussed in several works \[ ¶ ![Fig. 3 Self-modifying code via function templates and edit scripts.](images/S0065245817300499/f05-03-9780128151198.jpg "fig:")¶ Attacks: Self-modifying code can be effective against dynamic-analysis attack, which aim to break the integrity of the code (e.g., via dynamic code patching), if the executed instructions are different in different runs of the program with the same inputs. However, Nguyen et al. \[ ¶ 4.3.11 Virtualization Obfuscation ¶ This technique is related to the program encoding technique, because it also implies an encoding of instructions \[ ¶ Listing 30 ¶ Point Function Program ¶   1 int main(int argc, char\* argv \[\]) {       // Virtualization bytecode :  2      char branch\_cond = 1;                                 // a5 00 07  3      4      branch\_cond &= argv \[1\] \[0\] == ’1’;   // 87 00 00 02  5      branch\_cond &= argv \[1\] \[1\] == ’2’;   // 87 00 01 03  6      branch\_cond &= argv \[1\] \[2\] == ’3’;   // 87 00 02 04  7      branch\_cond &= argv \[1\] \[3\] == ’4’;   // 87 00 03 05  8      branch\_cond &= argv \[1\] \[4\] == ’5’;   // 87 00 04 06  9    10      if (branch\_cond)                                            // 1f 00 0211           printf ("You win !∖n");                         // 03 0012      return 0;                                                            // 42 0113 } ¶ 1. Map variables, function parameters, and constants to entries in a common data array, which represents the memory of the interpreter. This array is initialized on lines 3–4 in Listing 31. Its first position represents the branch\_cond variable from [Listing 30](#S0065245817300499.xhtml#b0155) and the following entries represent constants such as the return value, the ASCII codes of the characters from “1” to “5” and logical true encoded as 1.2. Map all statements in a function to a new randomly chosen language, which represents the instruction set architecture (ISA) of the interpreter. In our example the ISA is defined by:  ¶ • Variable assignment is encoded using 3 bytes, namely, the opcode (0xa5) and the index of the left- and right-hand operands inside the data array.• Equality comparison, followed by applying the logical AND operation to between the result and another variable. Examples of such instructions are shown on lines 4–5 in [Listing 30](#S0065245817300499.xhtml#b0155). Such an instruction is encoded using 4 bytes, namely, the opcode (0x87), the variable to which the Boolean value is assigned and the two other byte values which are compared for equality.• Conditional branch statements are encoded using 3 bytes, namely, the opcode (0x1f), the Boolean variable which is tested and the number of bytes to jump over if the variable is false.• Printing a string on standard output is encoded using 2 bytes, namely, the opcode (0x03) and the index of the string to be printed in the list of hard-coded strings of the function. In our example the list of hard-coded strings contains only one string and is defined on line 2 of Listing 31.• The return instruction is encoded using 2 bytes, namely, the opcode (0x42) and the value that should be returned by the program. ¶  
    Now we can write virtualization bytecode corresponding to the C program in [Listing 30](#S0065245817300499.xhtml#b0155), which is shown in the comments of the code from the same listing.3. Store the encoded bytecode inside the code array, which is initialized on lines 5–9 in Listing 31.4. Create an interpreter for the previously generated ISA, which can execute the instructions in the code array using the data array as its memory. The input–output behavior of this execution must be the same as that of the original program. The interpreter can be seen on lines 11–32 of Listing 31. It consists of an infinite while loop, which has a switch statement inside. Each case section of the switch statement is an opcode handler, i.e., each possible opcode in the bytecode program is processed by a dedicated part of the interpreter. The current instruction to be processed by the interpreter is indicated by an integer variable of the interpreter called the virtual program counter (VPC). The VPC is used to index the instructions in the code array and it is initialized with the offset of the first instruction in that array (line 10). In every instruction handler the operands of the current instruction are used to perform the operation(s) corresponding to this instruction. Afterward, the VPC is set to the offset of the following bytecode instruction to be executed. This interpreter should be augmented with cases representing bogus opcodes for all possible byte values in order to increase the resilience against MATE attacks. ¶ Listing 31 ¶ Point Function Program Obfuscated With Virtualization ¶   1 int main(int argc, char\* argv \[\]) {  2      char const \*strings = "You win !∖0";  3      unsigned char data \[8\] = {0,     // branch\_cond var  4             0, 49, 50, 51, 52, 53, 1}; // constants  5      unsigned char code \[30\] = {0xa5, 0x00, 0x07, 0x87, 0x00,  6             0x00, 0x02, 0x87, 0x00, 0x01, 0x03, 0x87,  7             0x00, 0x02, 0x04, 0x87, 0x00, 0x03, 0x05,  8             0x87, 0x00, 0x04, 0x06, 0x1f, 0x00, 0x02,  9             0x03, 0x00, 0x42, 0x01};10      int vpc = 0;11      while (1)12      switch (code \[vpc\]) {13           case 0xa5 : // variable assignment14                data \[code \[vpc +1\]\] = data \[code \[vpc +2\]\];15                vpc += 3;16                break;17           case 0x87 : // equality comparison plus and18                data \[code \[vpc +1\]\] &=19                     (argv \[1\] \[code \[vpc +2\]\] == data \[code \[vpc +3\]\]);20                vpc += 4;21                break;22           case 0x1f : // i f statement23                vpc += (data \[code \[vpc +1\]\]) ? 0 : data \[code \[vpc +2\]\];24                vpc += 3;25                break;26           case 0x03 : // printf string27                printf ("% s∖n", strings + code \[vpc +1\]);28                vpc += 2;29                break;30           case 0x42 : // return31                return data \[code \[vpc +1\]\];32      }33 } ¶  ¶ Together with virtualization a wide range of additional data and code obfuscation transformations can be applied. Banescu et al. \[ ¶ Attacks: Kinder \[ ¶ 4.3.12 Control Flow Flattening ¶ Wang et al. \[ ¶ Listing 32 ¶ Code Before Control Flow Flattening (CFF) ¶   1 int gcd (int a, int b){  2      while (a != b)  3           if (a > b)  4               a = a − b;  5           else  6               b = b − a;  7      return a;  8 } ¶ Listing 33 ¶ Code After CFF ¶   1 int gcd (int a, int b){  2 int next = 0;  3 while (1) {  4      switch (next) {  5           case 0:  6                if (a != b) next = 1;  7                else next = 2;  8                break;  9           case 1:  10             if (a > b) next = 3;  11              else next = 4;  12              break;  13         case 2: return a;  14              break;  15         case 3: a = a − b; next = 0;  16              break;  17         case 4: b = b − a; next = 0;  18              break;  19         default :  20              break;  21 }}} ¶ Attacks: Udupa el al. \[ ¶ 4.3.13 Branch Functions ¶ Linn and Debray \[ ¶ Listing 34 ¶ Code Before Branch Functions ¶   1        mov edx, eax  2        jmp L1  3       . . .  4 L2:mov ebx, edx  5        jmp L3  6       . . .  7 L1:mov eax, ebx  8        jmp L2  9 L3:. . . ¶ Listing 35 ¶ Code After Branch Functions ¶   1        mov edx, eax  2        push 1  3        call f  4       . . .  5 L2:mov ebx, edx  6        push 3  7        call f  8       . . .  9 L1:mov eax, ebx10        push 211        call f12 L3:. . . ¶ Schrittwieser and Katzenbeisser \[ ¶ Attacks: Kruegel et al. \[ ¶ 4.4 Code Abstraction Transformations ¶ 4.4.1 Merging and Splitting Functions ¶ These two techniques are the code correspondents to the data obfuscation transformations of merging and splitting variables \[ ¶ Listing 36 ¶ Splitting Functions ¶   1 func1 (int a, int b) {  2      x = 4;  3      if (a < 3)  4           x = x + 6;  5      x \*= b;  6 }  7      8 func2 (int a, int c) {  9      y = a + 12;10      y = y/c;11 } ¶  ¶ Listing 37 ¶ Merging Functions ¶   1 func3 (int a, int b, int c) {  2      if (c % 2 == 0) {  3           x = 4;  4           if (a < 3)  5               x = x + 6;  6           x \*= b;  7      } else {  8           y = a + 12;  9           y = y/b;10      }11 } ¶ Attacks: Rugaber et al. \[ ¶ 4.4.2 Remove Comments and Change Formatting ¶ This transformation is only applicable to programs which are delivered as source code (e.g., JavaScript). Comments are removed if they exist and all space, tab, and newline characters are also removed, which results in a continuous string of code which is more potent against human attackers, than the original code. An example is shown in [Listing 39](#S0065245817300499.xhtml#b0200), which is the result of removing comments and all formatting of the code from [Listing 38](#S0065245817300499.xhtml#b0195). The original formatting and comments cannot be recovered \[ ¶ Listing 38 ¶ Original JavaScript Code ¶   1 function NewObject(prefix) {  2      var count = 0;  3      // This function generates a pop−up  4      this . SayHello = function (msg) {  5           count++;  6           alert (prefix+ msg);  7      }  8 }  9 var obj = new NewObject("Message : ");10 obj . SayHello ("You are welcome . "); ¶ Listing 39 ¶ JavaScript code after removing comments and formatting ¶   1 function NewObject(prefix){var count=0; this \["SayHello"\] = function (msg){count++; alert (prefix + msg)}} var obj = new NewObject("Message : "); obj . SayHello ("You are welcome. ") ¶ Attacks: Bichsel et al. \[ ¶ 4.4.3 Scrambling Identifier Names ¶ This transformation implies changing all symbol names (e.g., variables, constants, functions, classes) into random strings \[ ¶ Listing 40 ¶ Code Before Scrambling Identifiers ¶   1 sum = 0;  2 for (i = 0; i < arr\_len; i++)  3      sum += arr \[i\];  4 average /= arr\_len; ¶ Listing 41 ¶ Code After Scrambling Identifiers ¶   1 za82b547bcb = 0;  2 for (z1c0ab7cf0c = 0; z1c0ab7cf0c < za862d19cbc; z1c0ab7cf0c++)  3      za82b547bcb += zc1c28ca67f \[z1c0ab7cf0c\];  4 z8c8f7c7867 /= za862d19cbc ¶ Attacks: Ceccato et al. \[ ¶ 4.4.4 Removing Library Calls and Programming Idioms ¶ Most programs perform calls to external libraries providing useful data structures (e.g., lists, maps) and algorithms (e.g., sorting, searching). MATE attackers often start by inspecting calls made to external libraries to give a high-level indication of what the program is doing. This transformation implies replacing such dependencies on external libraries with own implementations where possible \[ ¶ Attacks: The machine learning based attack of Bichset et al. \[ ¶ 4.4.5 Modify Inheritance Relations ¶ Programs written in some object-oriented programming languages are distributed in some intermediate format to end-users (e.g., C#, Java). These intermediate formats are only compiled to native code on the client's machine and contain useful object-oriented programming abstractions. In such programs it is important to break the useful abstractions offered by classes, their structure and their relations (e.g., aggregation, inheritance). According to Collberg et al. \[ ¶ Attacks: At the time of writing this chapter there have been no reported attacks on this obfuscation technique in the literature. ¶ 4.4.6 Function Argument Randomization ¶ Randomizing the order of formal parameters of methods and inserting bogus arguments is a technique implemented by tools such as Tigress \[ ¶ Attacks: The static code understanding attack of Zhang et al. \[ ¶ 4.5 Summary of Survey ¶ In the survey presented above, we have enumerated several practical data and code obfuscation transformations. Practical obfuscation does not offer provable security guarantees like cryptographic obfuscation \[ ¶ [Table 3](#S0065245817300499.xhtml#t0020) shows an overview and classification of all the obfuscation transformation presented in this section. We note that most of the presented transformations are applicable for all levels of abstraction (i.e., source code, IR, and binary). Most of the presented transformations are applicable at the function unit of transformation, followed closely by the program unit and then by instruction and basic block, both in third place. Only randomized stack frame have an effect on the system unit of transformation, because they change the layout of the stack. Two of the presented techniques are dynamic, meaning that they must allow code pages to be writable during program execution. The number of presented transformations are relatively balanced between the two different targets of transformation and their subcategories, however, code transformations are slightly more numerous. ¶  ¶ Table 3 ¶ Obfuscation TransformationAbstractionUnitDynamicsTarget  
    Opaque predicatesAllFunctionStaticData constant  
    Convert static data to procedural dataAllInstructionStaticData constant  
    Mixed Boolean ArithmeticAllBasic blockStaticData constant  
    White-box cryptographyAllFunctionStaticData constant  
    One-way transformationsAllInstructionStaticData constant  
    Split variablesAllFunctionStaticData variable  
    Merge variablesAllFunctionStaticData variable  
    Restructure arraysSourceProgramStaticData variable  
    Reorder variablesAllBasic blockStaticData variable  
    Dataflow flatteningBinaryProgramStaticData variable  
    Randomized stack framesBinarySystemStaticData variable  
    Data space randomizationAllProgramStaticData variable  
    Instruction reorderingAllBasic blockStaticCode logic  
    Instruction substitutionAllInstructionStaticCode logic  
    Encode ArithmeticAllInstructionStaticCode logic  
    Garbage insertionAllBasic blockStaticCode logic  
    Insert dead codeAllFunctionStaticCode logic  
    Adding and removing callsAllProgramStaticCode logic  
    Loop transformationsSource, IRLoopStaticCode logic  
    Adding and removing jumpsBinaryFunctionStaticCode logic  
    Program encodingAllAll buy systemDynamicCode logic  
    Self-modifying codeAllProgramDynamicCode logic  
    Virtualization obfuscationAllFunctionStaticCode logic  
    Control flow flatteningAllFunctionStaticCode logic  
    Branch functionsBinaryInstructionStaticCode logic  
    Merging and splitting functionsAllProgramStaticCode abstraction  
    Remove comments and change formattingSourceProgramStaticCode abstraction  
    Scrambling identifier namesSourceProgramStaticCode abstraction  
    Removing library calls and programming idiomsAllFunctionStaticCode abstraction  
    Modify inheritance relationsSource, IRProgramStaticCode abstraction  
    Function argument randomizationAllFunctionStaticCode abstraction ¶ ![t0020](images/S0065245817300499/t0020.png)¶ 5 Discussion ¶ In this section we present an overview of the previous survey and discuss the observations stemming from it. Based on this discussion we identify gaps in the field of software obfuscation which require further investigation/research. ¶ [Table 4](#S0065245817300499.xhtml#t0025) provides an overview of the various MATE attacks (already mentioned in the previous section), which have been successfully applied in order to defeat the obfuscation transformations presented in [Section 4](#S0065245817300499.xhtml#s0085), w.r.t. the attack dimensions presented in [Section 3](#S0065245817300499.xhtml#s0055). These attacks are placed in the cells of [Table 4](#S0065245817300499.xhtml#t0025) to indicate the obfuscation transformation(s) they claim to break and where they stand w.r.t. the attack dimensions presented in [Section 3](#S0065245817300499.xhtml#s0055). The following observations stem from [Table 4](#S0065245817300499.xhtml#t0025): ¶ 
    ¶ *   ¶ • Some works present attacks which are applicable to multiple obfuscation transformations and multiple attack dimensions. For instance, the attacks by Salem and Banescu \[ ¶ 
    *   ¶ • Except for comparing different MATE attacks w.r.t. the classification dimensions presented in [Section 3](#S0065245817300499.xhtml#s0055), there is no set of standard benchmarks used in the field of software obfuscation, which would allow comparing different attacks to one another. This indicates that more research is necessary in order to be able to compare these attack techniques to each other. Such research is needed for evaluating the strength of different obfuscation transformations. Therefore, the development of: (1) standard obfuscation benchmarks for MATE attacks and (2) standard attack benchmarks for obfuscation transformations is still an open problem in the field of software protection. ¶ 
    ¶ *   ¶ • It is not shown in [Table 4](#S0065245817300499.xhtml#t0025) due to lack of horizontal space, however, there are fewer active attacks than passive attacks. This may be due to the fact that active attacks are often associated with malicious exploitation (e.g., cracking software), which is not ethical for most researchers. However, more research is required in the direction of active attacks in order to enable the development of stronger protection against such attacks. ¶ 
    ¶ *   ¶ • Also there are fewer attacks which aim to recover the location of data and/or code, in comparison to attacks on code understanding or data recovery. Location attacks are often associated with active attacks; therefore the previous argument applies to this observation as well. ¶ 
    ¶ *   ¶ • As expected, the majority of data recovery attacks target data obfuscation transformations and the majority of code understanding attacks target code obfuscation transformations. However, there are also some attacks which target both types of transformations, when they are used in combination with each other. Nevertheless, much more research is needed for investigating the strength of combinations of multiple software obfuscation transformations. ¶ 
    ¶ *   ¶ • Most attacks on obfuscated code are dynamic, because the majority of the obfuscation transformations presented in this paper aim to break static analysis techniques. Similarly, most attacks are semantic because most dynamic attacks are also semantic. However, note that there are also exceptions. Nevertheless, there are relatively few works about static semantic and dynamic syntactic attacks, which indicates a topic that needs further exploration. ¶ 
    ¶ *   ¶ • Obfuscation transformations which have few or no attacks against them are not an indication that they are more secure. For instance, in the case of dataflow flattening, the most probable reason why there are no attacks against it is because it is too expensive to implement this obfuscation transformation in most practical scenarios. One of the strongest obfuscation transformation categories against MATE attackers are dynamic transformations, however, these transformations generally require making executable code pages in process memory also writable, which opens the door to remote code injection attacks \[ ¶ 
    *   ¶ • Most attacks published in literature are dynamic, because even if code is statically encrypted/encoded, it must be decrypted/decoded during execution. This is the “Achilles heel” of obfuscation, i.e., code must still be executable, no matter how intricate the code is obfuscated when inspected statically. To prevent dynamic MATE attacks in practice obfuscation is used in combination with antidynamic-analysis techniques such as antidebugging \[ ¶ 
    *   ¶ • In some contexts, the MATE attacker is not forced to perform static analysis due to antidynamic-analysis techniques, but due to resource constraints. For instance, some malware analysis systems have to analyze millions of instances per day \[ ¶  ¶ Table 4 ¶ 
        
        ¶ 
        
         ¶ Overview of Obfuscation Resilience Against MATE Attacks ¶ 
        
         ¶ ¶ 
        ¶ | ¶ Obfuscation Transformation Given this observation, one may jump to the conclusion that it may be beneficial for benign software developers and antimalware developers, if less research in this field was published, because then malicious MATE attackers and malware developers would not have as many techniques and tools at their disposal. This would not stop malicious parties from developing their own techniques, but it would keep many benign parties “in the dark” about advances in this field. This was the case in the 1980s, before this research community was born and malicious parties were already using software obfuscation to protect malware and MATE attacks to break licenses. Therefore, having such a two camp research community, where each side challenges the weaknesses of the other side leads to continuous improvements, which accelerate progress and practical applicability of such research. 
        
        ## 6 Related Work
        
        As indicated in [Fig. 1](#S0065245817300499.xhtml#f0010), there are several ways in which one could protect against MATE attacks. Since in this chapter we focus on technical protection via obfuscation, in this section we present the other types of protections. This is followed by related work from the field of cryptographic obfuscation and by other surveys of software obfuscation.
        
        ### 6.1 Encryption via Trusted Hardware
        
        Software protection via encryption is usually enabled by trusted hardware, also called trusted computing. Intel has released a hardware based technology \[
        
        ### 6.2 Server-Side Execution
        
        Tamper protection via communication with trusted servers is employed in massive multiplayer online games (MMOGs) to detect cheating. Anticheat software such as PunkBuster \[
        
        Martignoni et al. \[
        
        Jakobsson and Johansson \[
        
        ### 6.3 Code Tamper-detection and Tamper-proofing
        
        Code tamper-detection and tamper-proofing are complementary techniques to software diversity and obfuscation and they aim to detect, respectively, prevent unauthorized modifications of a program's code. However, these techniques are not generally stealthy, and hence they should be combined with diverse obfuscation in order to hamper MATE attackers from disabling such mechanisms.
        
        Chang and Atallah \[
        
        Chen et al. \[
        
        Jacob et al. \[
        
        Cappaert et al. \[
        
        ### 6.4 Cryptographic Obfuscation
        
        In addition to the practical software protection techniques presented so far, there is also an entire subfield of cryptography dedicated to obfuscation. The first formal study of obfuscation was published in 2001 by Barak et al. \[
        
        Over a decade later, Garg et al. \[
        
        ### 6.5 Other Surveys of Software Obfuscation
        
        The seminal work of Collberg et al. \[
        
        Larsen et al. \[
        
        Schrittwiesser et al. \[
        
        ## 7 Conclusion
        
        This paper presents a tutorial on software obfuscation. This tutorial includes a state-of-the-art survey of obfuscation transformations and their classifications. Each obfuscation transformation is accompanied by an illustrative example (often in the form of code snippets), as well as an enumeration of existing associated attacks published in the literature. We discuss how the current landscape of software obfuscation research is split into two complementary camps, namely, software protection and malware analysis, and why this division is important for accelerating progress. An interesting observation is that malicious entities may have higher benefits from techniques proposed in the field of research, due to the fact that they do not have high performance constraints as benign entities (e.g., commercial software vendors) have. However, the only way to defend against malicious entities is to push these areas of research forward. One way to increase the performance constraints of malicious MATE attackers is by employing frequent software updates, which shrinks the window of opportunity of such attackers. Therefore, future research in the field of software obfuscation should also investigate obfuscation techniques which allow incremental updates.
        
        Our outlook on the field of obfuscation is positive. We believe that even with advances in hardware-based software protection techniques such as Intel SGX \[
        
        The main challenge in the field of software obfuscation is that there is no standard methodology or benchmarks for evaluating the strength of different obfuscation transformations or combinations thereof. The first steps in the direction of obfuscation evaluation have been made by Banescu et al. \[
        
        We envision that side-channel attacks against obfuscation will become increasingly popular. This premonition is due to the recent differential computation analysis (DCA) presented by Bos et al. \[
        
        ## References
        
        \[1\] Collberg C., Davidson J., Giacobazzi R., Gu Y.X., Herzberg A., Wang F. Toward digital asset protection. *IEEE Intell. Syst.* 2011;26(6):8–13.
        
        \[2\] Dolev D., Yao A.C. On the security of public key protocols. In: Washington, DC, USA: IEEE Computer Society; 1981:350–357. doi:10.1109/SFCS.1981.32. *Proceedings of the 22nd Annual Symposium on Foundations of Computer Science.*.
        
        \[3\] Main A.P.C. van Oorschot. *Software Protection and Application Security: Understanding the Battleground.* 2003. [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.216.3498&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.216.3498&rep=rep1&type=pdf) International Course on State of the Art and Evolution of Computer Security and Industrial Cryptography.
        
        \[4\] Shamir A., Van Someren N. Playing ‘hide and seek’ with stored keys. In: *Financial Cryptography.* London, UK: Springer-Verlag; 1999:118–124. [https://dl.acm.org/citation.cfm?id=728464](https://dl.acm.org/citation.cfm?id=728464).
        
        \[5\] B. Wyseur, White-box cryptography (Ph.D. thesis), Katholieke Universiteit Leuven, Leuven-Heverlee, 2009, [https://repository.libis.kuleuven.be/dspace/handle/1979/2098](https://repository.libis.kuleuven.be/dspace/handle/1979/2098).
        
        \[6\] Cohen F.B. Operating system protection through program evolution. *Comput. Secur.* 0167-40481993. ;12(6):565–584. doi:10.1016/0167-4048(93)90054-9. [http://www.sciencedirect.com/science/article/pii/0167404893900549](http://www.sciencedirect.com/science/article/pii/0167404893900549).
        
        \[7\] Collberg C., Thomborson C., Low D. *A Taxonomy of Obfuscating Transformations.* New Zealand: Department of Computer Science, The University of Auckland; 1997. [https://researchspace.auckland.ac.nz/handle/2292/3491](https://researchspace.auckland.ac.nz/handle/2292/3491).
        
        \[8\] Congress U. Digital Millennium Copyright Act. *Public Law.* 1998;105(304):112.
        
        \[9\] Kur A., Planck M., Dreier T. *European intellectual property law: text, cases and materials.* Cheltenham: Edward Elgar Publishing; 2013.
        
        \[10\] Badger L., D’Anna L., Kilpatrick D., Matt B., Reisse A., Van Vleck T. *Self-Protecting Mobile Agents Obfuscation Techniques Evaluation.* 2002 Network Associates Laboratories, Report 01036.
        
        \[11\] Mavrogiannopoulos N., Kisserli N., Preneel B. A taxonomy of self-modifying code for obfuscation. *Comput. Secur.* 016740482011. ;30(8):679–691. doi:10.1016/j.cose.2011.08.007. [http://linkinghub.elsevier.com/retrieve/pii/S0167404811001076](http://linkinghub.elsevier.com/retrieve/pii/S0167404811001076).
        
        \[12\] Larsen P., Homescu A., Brunthaler S., Franz M. SoK: automated software diversity. In: IEEE; 2014:276–291. *IEEE Symposium on Security and Privacy.*.
        
        \[13\] Schrittwieser S., Katzenbeisser S., Kinder J., Merzdovnik G., Weippl E. Protecting software through obfuscation: can it keep pace with progress in code analysis? *ACM Comput. Surv.* 2016;49(1):4.
        
        \[14\] Team P. *PaX Non-Executable Pages Design & Implementation.* 2003. [http://pax.grsecurity.net](http://pax.grsecurity.net) Available from.
        
        \[15\] Collberg C., Nagra J. *Surreptitious Software.* Upper Saddle River, NJ: Addision-Wesley Professional; 2010.
        
        \[16\] Akhunzada A., Sookhak M., Anuar N.B., Gani A., Ahmed E., Shiraz M., Furnell S., Hayat A., Khan M.K. Man-at-the-end attacks: analysis, taxonomy, human aspects, motivation and future directions. *J. Netw. Comput. Appl.* 2015;48:44–57.
        
        \[17\] C. Basile, S. Di Carlo, T. Herlea, V. Business, J. Nagra, B. Wyseur, Towards a formal model for software tamper resistance, in: Second International Workshop on Remote Entrusting (ReTtust 2009), vol. 16.
        
        \[18\] C. Collberg, The Tigress C Diversifier/Obfuscator. [http://tigress.cs.arizona.edu/](http://tigress.cs.arizona.edu/), n.d. (accessed 29.11.16).
        
        \[19\] Skochinsky I. *IDA F.L.I.R.T. technology: in-depth.* 2013. [https://www.hex-rays.com/products/ida/tech/flirt/in\_depth.shtml](https://www.hex-rays.com/products/ida/tech/flirt/in_depth.shtml) (accessed: 03.03.17).
        
        \[20\] Banescu S., Wuchner T., Salem A., Guggenmos M., Pretschner A., et al. A framework for empirical evaluation of malware detection resilience against behavior obfuscation. In: IEEE; 2015:40–47. *2015 10th International Conference on Malicious and Unwanted Software (MALWARE).*.
        
        \[21\] Floyd R.W. Assigning meanings to programs. 19–32. *Mathematical Aspects of Computer Science.* 1967;vol. 19.
        
        \[22\] Cousot P., Cousot R. Abstract interpretation: a unified lattice model for static analysis of programs by construction or approximation of fixpoints. In: ACM; 1977:238–252. *Proceedings of the 4th ACM SIGACT-SIGPLAN Symposium on Principles of Programming Languages.*.
        
        \[23\] Sutton M., Greene A., Amini P. *Fuzzing: Brute Force Vulnerability Discovery.* Crowfordsville, IN, USA: Pearson Education; 2007.
        
        \[24\] Landi W. Undecidability of static analysis. *ACM Lett. Program. Lang. Syst.* 1992;1(4):323–337.
        
        \[25\] Ramalingam G. The undecidability of aliasing. *ACM Trans. Program. Lang. Syst.* 1994;16(5):1467–1471.
        
        \[26\] Horwitz S. Precise flow-insensitive may-alias analysis is NP-hard. *ACM Trans. Program. Lang. Syst.* 1997;19(1):1–6.
        
        \[27\] Wang C., Davidson J., Hill J., Knight J. Protection of software-based survivability mechanisms. In: 2001:193–202. doi:10.1109/DSN.2001.941405. *International Conference on Dependable Systems and Networks (DSN 2001).*.
        
        \[28\] Palsberg J., Krishnaswamy S., Kwon M., Ma D., Shao Q., Zhang Y. Experience with software watermarking. In: IEEE; 2000:308–316. *Computer Security Applications, 2000. ACSAC’00. 16th Annual Conference.*.
        
        \[29\] Majumdar A., Thomborson C. Manufacturing opaque predicates in distributed systems for code obfuscation. In: Australian Computer Society, Inc.; 187–196. *Proceedings of the 29th Australasian Computer Science Conference.* 2006;vol. 48.
        
        \[30\] Dalla Preda M., Madou M., De Bosschere K., Giacobazzi R. Opaque predicates detection by abstract interpretation. In: Johnson M., Vene V., eds. *Algebraic Methodology and Software Technology.* Berlin, Heidelberg: Springer; 81–95. doi:10.1007/11784180\_9. *Lecture Notes in Computer Science.* 2006;vol. 4019 ISBN 978-3-540-35633-2.
        
        \[31\] Banescu S., Collberg C., Ganesh V., Newsham Z., Pretschner A. Code obfuscation against symbolic execution attacks. In: ACM; 2016. *Proc. of 2016 Annual Computer Security Applications Conference.*.
        
        \[32\] Banescu S., Ochoa M., Pretschner A. A framework for measuring software obfuscation resilience against automated attacks. In: IEEE; 2015:45–51. *2015 IEEE/ACM 1st International Workshop on Software Protection (SPRO).*.
        
        \[33\] Salem A., Banescu S. Metadata recovery from obfuscated programs using machine learning. In: ACM; 2016:8. *Proceedings of the 6th Software Security, Protection and Reverse Engineering Workshop.*.
        
        \[34\] Bacon D.F., Graham S.L., Sharp O.J. Compiler transformations for high-performance computing. *ACM Comput. Surv.* 1994;26(4):345–420.
        
        \[35\] Zhou Y., Main A., Gu Y.X., Johnson H. Information hiding in software with mixed Boolean-arithmetic transforms. In: Springer; 2007:61–75. *International Workshop on Information Security Applications.*.
        
        \[36\] Guinet A., Eyrolles N., Videau M. *Arybo: Manipulation, canonicalization and identification of mixed boolean-arithmetic symbolic expressions.* Grenoble, France: Proceedings of GreHack 2016; . 2016.
        
        \[37\] Chow S., Eisen P., Johnson H., van Oorschot P.C. A white-box DES implementation for DRM applications. In: Feigenbaum J., ed. *Digital Rights Management. DRM 2002.* Berlin, Heidelberg: Springer; . *Lecture Notes in Computer Science.* 2003;vol. 2696.
        
        \[38\] Chow S., Eisen P., Johnson H., Oorschot P.C.V. White-box cryptography and an AES implementation. no. 2595 In: *Selected Areas in Cryptography.* Berlin, Heidelberg: Springer; 2003:250–270. *in LNCS.* ISBN 978-3-540-00622-0, 978-3-540-36492-4.
        
        \[39\] FIPS P.U.B.S. *197: Advanced Encryption Standard (AES).* 2001 National Institute of Standards and Technology.
        
        \[40\] Xiao Y., Lai X. A secure implementation of white-box AES. In: 2009:1–6. doi:10.1109/CSA.2009.5404239. *2nd International Conference on Computer Science and its Applications, 2009. CSA ’09.*.
        
        \[41\] Bringer J., Chabanne H., Dottax E. *White box cryptography: another attempt.* 2006. [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.99.661&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.99.661&rep=rep1&type=pdf) Available from (accessed 22.06.11).
        
        \[42\] Karroumi M. Protecting White-Box AES with Dual Ciphers. no. 6829 In: Rhee K.-H., Nyang D., eds. *Information Security and Cryptology—ICISC 2010.* Berlin, Heidelberg: Springer; 2011:278–291. *Lecture Notes in Computer Science.*. [http://link.springer.com/chapter/10.1007/978-3-642-24209-0\_19](http://link.springer.com/chapter/10.1007/978-3-642-24209-0_19) ISBN 978-3-642-24208-3, 978-3-642-24209-0.
        
        \[43\] Wyseur B., Michiels W., Gorissen P., Preneel B. Cryptanalysis of white-box DES implementations with arbitrary external encodings. no. 4876 In: *Selected Areas in Cryptography.* Berlin, Heidelberg: Springer; 2007:264–277. *LNCS.*. [http://link.springer.com/chapter/10.1007/978-3-540-77360-3\_17](http://link.springer.com/chapter/10.1007/978-3-540-77360-3_17) ISBN 978-3-540-77359-7, 978-3-540-77360-3.
        
        \[44\] Billet O., Gilbert H., Chatbi C.E. *Cryptanalysis of a White Box AES Implementation.* Waterloo, Canada: Springer-Verlag; 2005.227–240 ISBN 3-540-24327-5, 978-3-540-24327-4.
        
        \[45\] De Mulder Y., Roelse P., Preneel B. Cryptanalysis of the Xiao-Lai white-box AES implementation. In: Knudsen L.R., Wu H., eds. Berlin, Heidelberg: Springer; 2013:34–49. *Selected Areas in Cryptography.*. [http://link.springer.com/chapter/10.1007/978-3-642-35999-6\_3](http://link.springer.com/chapter/10.1007/978-3-642-35999-6_3).
        
        \[46\] Courtois N.T., Pieprzyk J. Cryptanalysis of block ciphers with overdefined systems of equations. In: Zheng Y., ed. Berlin, Heidelberg: Springer; 2002:267–287. *International Conference on the Theory and Application of Cryptology and Information Security.*.
        
        \[47\] Banescu S., Pretschner A., Battré D., Cazzulani S., Shield R., Thompson G. Software-based protection against changeware. In: 2015:231–242. *Proceedings of the Conference on Data and Application Security and Privacy.* CODASPY '15.
        
        \[48\] Wang X., Feng D., Lai X., Yu H. Collisions for hash functions MD4, MD5, HAVAL-128 and RIPEMD. In: 2004. *IACR Cryptology ePrint Archive.* Report 2004:199.
        
        \[49\] Stevens M., Bursztein E., Karpman P., Albertini A., Markov Y. *The First Collision for Full SHA-1.* 2017. [https://shattered.it/static/shattered.pdf](https://shattered.it/static/shattered.pdf).
        
        \[50\] Slowinska A., Haller I., Bacs A., Baranga S., Bos H. Data structure archaeology: scrape away the dirt and glue back the pieces!. In: Cham: Springer; 2014:1–20. *International Conference on Detection of Intrusions and Malware, and Vulnerability Assessment.*.
        
        \[51\] Viticchié A., Regano L., Torchiano M., Basile C., Ceccato M., Tonella P., Tiella R. *Assessment of source code obfuscation techniques.* In: 2016 IEEE 16th International Working Conference on Source Code Analysis and Manipulation (SCAM); 2016:11–20. doi:10.1109/SCAM.2016.17 Raleigh, NC.
        
        \[52\] Slowinska A., Stancescu T., Bos H. Howard: a dynamic excavator for reverse engineering data structures. In: 2011. *NDSS.*.
        
        \[53\] Pappas V., Polychronakis M., Keromytis A.D. Smashing the gadgets: hindering return-oriented programming using in-place code randomization. In: IEEE; 2012:601–615. doi:10.1109/SP.2012.41. *IEEE Symposium on Security and Privacy (SP).*. [http://ieeexplore.ieee.org/lpdocs/epic03/wrapper.htm?arnumber=6234439](http://ieeexplore.ieee.org/lpdocs/epic03/wrapper.htm?arnumber=6234439) ISBN 978-1-4673-1244-8, 978-0-7695-4681-0.
        
        \[54\] Griffin K., Schneider S., Hu X., Chiueh T.-C. Automatic generation of string signatures for malware detection. In: Springer; 2009:101–120. *International Workshop on Recent Advances in Intrusion Detection.*.
        
        \[55\] Anckaert B., Jakubowski M.H., Venkatesan R., Saw C.W. Runtime protection via dataflow flattening. In: IEEE; 2009:242–248. *2009 Third International Conference on Emerging Security Information, Systems and Technologies.*.
        
        \[56\] Goldreich O., Ostrovsky R. Software protection and simulation on oblivious RAMs. *J. ACM.* 1996;43(3):431–473.
        
        \[57\] Forrest S., Somayaji A., Ackley D.H. Building diverse computer systems. In: IEEE; 1997:67–72. *The Sixth Workshop on Hot Topics in Operating Systems.*.
        
        \[58\] Fedler R., Banescu S., Pretschner A. ISA2R: improving software attack and analysis resilience via compiler-level software diversity. In: Springer; 2015:362–371. *International Conference on Computer Safety, Reliability, and Security.*.
        
        \[59\] Strackx R., Younan Y., Philippaerts P., Piessens F., Lachmund S., Walter T. Breaking the memory secrecy assumption. In: ACM; 2009:1–8. *Proceedings of the Second European Workshop on System Security.*.
        
        \[60\] Cadar C., Akritidis P., Costa M., Martin J.-P., Castro M. *Data Randomization.* Tech. rep. TR-2008-120 Microsoft Research; 2008.
        
        \[61\] Bhatkar S., Sekar R. Data space randomization. In: Zamboni D., ed. *Detection of Intrusions and Malware, and Vulnerability Assessment.* Berlin, Heidelberg: Springer; 2008:1–22. *Lecture Notes in Computer Science.* no. 5137 in.
        
        \[62\] Cowan C., Beattie S., Johansen J., Wagle P. Pointguard TM: protecting pointers from buffer overflow vulnerabilities. 91–104. *Proceedings of the 12th Conference on USENIX Security Symposium.* 2003;vol. 12.
        
        \[63\] L.O. Andersen, Program analysis and specialization for the C programming language (Ph.D. thesis), University of Copenhagen, 1994.
        
        \[64\] Zhang F., Huang H., Zhu S., Wu D., Liu P. ViewDroid: towards obfuscation-resilient mobile application repackaging detection. In: ACM; 2014:25–36. *Proceedings of the 2014 ACM Conference on Security and Privacy in Wireless & Mobile Networks.*.
        
        \[65\] Jacob M., Jakubowski M.H., Naldurg P., Saw C.W., Venkatesan R. The superdiversifier: peephole individualization for software protection. In: Matsuura K., Fujisaki E., eds. *Advances in Information and Computer Security. IWSEC 2008.* Berlin, Heidelberg: Springer; . *Lecture Notes in Computer Science.* 2008;vol. 5312.
        
        \[66\] El-Khalil R., Keromytis A.D. Hydan: hiding information in program binaries. In: Springer; 2004:187–199. *International Conference on Information and Communications Security.*.
        
        \[67\] De Sutter B., Anckaert B., Geiregat J., Chanet D., De Bosschere K. Instruction set limitation in support of software diversity. In: Springer; 2008:152–165. *International Conference on Information Security and Cryptology.*.
        
        \[68\] Mason J., Small S., Monrose F., MacManus G. English shellcode. In: ACM; 2009:524–533. *Proceedings of the 16th ACM Conference on Computer and Communications Security.*.
        
        \[69\] Warren H.S. *Hacker's Delight.* Boston, MA: Addison-Wesley Longman Publishing Co., Inc.; 2002 ISBN 0201914654.
        
        \[70\] Eyrolles N., Goubin L., Videau M. Defeating MBA-based Obfuscation. In: ACM; 2016:27–38. *Proceedings of the 2016 ACM Workshop on Software PROtection.*.
        
        \[71\] Yadegari B., Johannesmeyer B., Whitely B., Debray S. A generic approach to automatic deobfuscation of executable code. In: IEEE; 2015:674–691. *2015 IEEE Symposium on Security and Privacy (SP).*.
        
        \[72\] Knoop J., Rüthing O., Steffen B. Partial dead code elimination. *ACM SIGPLAN Notices.* 1994;29(6):147–158.
        
        \[73\] Gupta R., Benson D., Fang J.Z. Path profile guided partial dead code elimination using predication. In: IEEE; 1997:102–113. *Proceedings International Conference on Parallel Architectures and Compilation Techniques.*.
        
        \[74\] Wüchner T., Ochoa M., Pretschner A. Robust and effective malware detection through quantitative data flow graph metrics. In: Springer; 2015:98–118. *International Conference on Detection of Intrusions and Malware, and Vulnerability Assessment.*.
        
        \[75\] Yadegari B., Stephens J., Debray S. Analysis of exception-based control transfers. In: ACM; 2017:205–216. *Proceedings of the Seventh ACM on Conference on Data and Application Security and Privacy.*.
        
        \[76\] Vrba, Z. cryptexec: Next-generation runtime binary encryption using on-demand function extraction. Phrak 0x0b (0x3f). #0x0d of 0x14.\[online\] (2003), [http://www.phrack.org/archives/issues/63/13.txt](http://www.phrack.org/archives/issues/63/13.txt).
        
        \[77\] Cappaert J., Preneel B., Anckaert B., Madou M., De Bosschere K. Towards tamper resistant code encryption: practice and experience. In: Springer; 2008:86–100. *Information Security Practice and Experience.*.
        
        \[78\] M. Oberhumer, L. Molnár J.F. Reiser, UPX: The Ultimate Packer for eXecutables, 2004, Published online at [http://upx.sourceforge.net/](http://upx.sourceforge.net/)
        
        \[79\] Tang Y., Chen S. An automated signature-based approach against polymorphic internet worms. *IEEE Trans. Parallel Distrib. Syst.* 2007;18(7).
        
        \[80\] Qiu J., Yadegari B., Johannesmeyer B., Debray S., Su X. Identifying and understanding self-checksumming defenses in software. In: ACM; 2015:207–218. *Proceedings of the 5th ACM Conference on Data and Application Security and Privacy.*.
        
        \[81\] Madou M., Anckaert B., Moseley P., Debray S., De Sutter B., De Bosschere K. Software protection through dynamic code mutation. In: Berlin, Heidelberg: Springer; 2006:194–206. *Information Security Applications.*.
        
        \[82\] Kanzaki Y., Monden A., Nakamura M., Matsumoto K.-I. Exploiting self-modification mechanism for program protection. In: 2003:170–179. *Proceedings. 27th Annual International Computer Software and Applications Conference. COMPSAC.*.
        
        \[83\] Nguyen-Tuong A., Wang A., Hiser J.D., Knight J.C., Davidson J.W. On the effectiveness of the metamorphic shield. In: ACM; 2010:170–174. *Proceedings of the Fourth European Conference on Software Architecture: Companion Volume.*.
        
        \[84\] Barrantes E.G., Ackley D.H., Palmer T.S., Stefanovic D., Zovi D.D. Randomized instruction set emulation to disrupt binary code injection attacks. In: ACM; 2003:281–289. *Proceedings of the 10th ACM Conference on Computer and Communications Security.*.
        
        \[85\] Mason J., Watkins K., Eisner J., Stubblefield A. A natural language approach to automated cryptanalysis of two-time pads. In: ACM; 2006:235–244. *Proceedings of the 13th ACM Conference on Computer and Communications Security.*.
        
        \[86\] Dalla Preda M., Giacobazzi R., Debray S., Coogan K., Townsend G.M. Modelling metamorphism by abstract interpretation. In: Springer; 2010:218–235. *International Static Analysis Symposium.*.
        
        \[87\] Banescu S., Lucaci C., Krämer B., Pretschner A. VOT4CS: a virtualization obfuscation tool for C. In: ACM; 2016:39–49. *Proceedings of the 2016 ACM Workshop on Software PROtection.*.
        
        \[88\] Kinder J. Towards static analysis of virtualization-obfuscated binaries. In: 2012:61–70. doi:10.1109/WCRE.2012.16. *19th Working Conference on Reverse Engineering (WCRE).* 1095-1350.
        
        \[89\] Rolles R. Unpacking Virtualization Obfuscators. In: Berkeley, CA, USA: USENIX Association; 2009:1. *Proceedings of the 3rd USENIX Conference on Offensive Technologies, Montreal, Canada.*. [http://dl.acm.org/citation.cfm?id=1855876.1855877](http://dl.acm.org/citation.cfm?id=1855876.1855877) WOOT'09.
        
        \[90\] Chow S., Gu Y., Johnson H., Zakharov V.A. An approach to the obfuscation of control-flow of sequential computer programs. In: Springer; 2001:144–155. *International Conference on Information Security.*.
        
        \[91\] Udupa S., Debray S., Madou M. Deobfuscation: reverse engineering obfuscated code. In: 2005:doi:10.1109/WCRE.2005.13. *12th Working Conference on Reverse Engineering.* 1095-1350.
        
        \[92\] Linn C., Debray S. Obfuscation of executable code to improve resistance to static disassembly. In: ACM; 2003:290–299. *Proceedings of the 10th ACM Conference on Computer and Communications Security.*.
        
        \[93\] Schrittwieser S., Katzenbeisser S. Code obfuscation against static and dynamic reverse engineering. In: Filler T., Pevný T., Craver S., Ker A., eds. *Information Hiding. IH 2011.* Berlin, Heidelberg: Springer; . *Lecture Notes in Computer Science.* 2011;vol. 6958.
        
        \[94\] Shacham H. The geometry of innocent flesh on the bone: return-into-libc without function calls (on the x86). In: 2007:552–561. *Proceedings of the 14th ACM Conference on Computer and Communications Security.*. [http://dl.acm.org/citation.cfm?id=1315313](http://dl.acm.org/citation.cfm?id=1315313).
        
        \[95\] Kruegel C., Robertson W., Valeur F., Vigna G. Static disassembly of obfuscated binaries. 18. *USENIX Security Symposium.* 2004;13.
        
        \[96\] Rugaber S., Stirewalt K., Wills L.M. The interleaving problem in program understanding. In: IEEE; 1995:166–175. *Proceedings of 2nd Working Conference on Reverse Engineering, 1995.*.
        
        \[97\] Stunnix, C/C++ Obfuscator. [http://stunnix.com/prod/cxxo/](http://stunnix.com/prod/cxxo/) (accessed 03.03.17).
        
        \[98\] PreEmptiveSolutions, DashO: Java & Android Obfuscator & Runtime Protection. [https://www.preemptive.com/products/dasho](https://www.preemptive.com/products/dasho) (accessed 03.03.17).
        
        \[99\] PreEmptiveSolutions, Dotfuscator: .NET App Self Protection and Obfuscation. [https://www.preemptive.com/products/dotfuscator](https://www.preemptive.com/products/dotfuscator) (accessed 03.03.17).
        
        \[100\] SemanticDesigns, Thicket Family of Source Code Obfuscators. [http://www.semanticdesigns.com/Products/Obfuscators/](http://www.semanticdesigns.com/Products/Obfuscators/) (accessed 03.03.17).
        
        \[101\] GuardSquare, ProGuard: The Open Source Optimizer for Java Bytecode. [https://www.guardsquare.com/en/proguard](https://www.guardsquare.com/en/proguard) (accessed 03.03.17).
        
        \[102\] yWorks, yGuard Java Bytecode Obfuscator and Shrinker. [https://www.yworks.com/products/yguard](https://www.yworks.com/products/yguard) (accessed 03.03.17).
        
        \[103\] Bichsel B., Raychev V., Tsankov P., Vechev M. Statistical deobfuscation of android applications. In: ACM; 2016:343–355. *Proceedings of the 2016 ACM SIGSAC Conference on Computer and Communications Security.*.
        
        \[104\] Ceccato M., Penta M.D., Falcarin P., Ricca F., Torchiano M., Tonella P. A family of experiments to assess the effectiveness and efficiency of source code obfuscation techniques. *Empir. Softw. Eng.* 1382-3256, 1573-76162013;19(4):1040–1074. doi:10.1007/s10664-013-9248-x.
        
        \[105\] Wills L.M. Automated program recognition: a feasibility demonstration. *Artif. Intell.* 0004-37021990;45(1–2):113–171. doi:10.1016/0004-3702(90)90039-3.
        
        \[106\] Foket C., De Sutter B., Coppens B., De Bosschere K. A novel obfuscation: class hierarchy flattening. In: Garcia-Alfaro J., Cuppens F., Cuppens-Boulahia N., Miri A., Tawbi N., eds. *Foundations and Practice of Security. FPS 2012.* Berlin, Heidelberg: Springer; . *Lecture Notes in Computer Science.* 2013;vol. 7743.
        
        \[107\] Collberg C., Martin S., Myers J., Nagra J. Distributed application tamper detection via continuous software updates. ACSAC '12 In: New York, NY, USA: ACM; 2012:319–328. doi:10.1145/2420950.2420997. *Proceedings of the 28th Annual Computer Security Applications Conference, Orlando, Florida, USA.*. [http://doi.acm.org/10.1145/2420950.2420997](http://doi.acm.org/10.1145/2420950.2420997) ISBN 978-1-4503-1312-4.
        
        \[108\] Barak B., Goldreich O., Impagliazzo R., Rudich S., Sahai A., Vadhan S., Yang K. On the (im) possibility of obfuscating programs. In: Springer; 2001:1–18. *Advances in Cryptology CRYPTO 2001.*.
        
        \[109\] Garg S., Gentry C., Halevi S., Raykova M., Sahai A., Waters B. Candidate indistinguishability obfuscation and functional encryption for all circuits. In: 2013:40–49. doi:10.1109/FOCS.2013.13. *Proc. of the 54th Annual Symp. on Foundations of Computer Science.* 0272-5428.
        
        \[110\] Molnar, I., Method and Apparatus for Creating an Execution Shield. U.S. Patent Application No. 10/420,253.
        
        \[111\] Abrath B., Coppens B., Volckaert S., Wijnant J., De Sutter B. Tightly-coupled self-debugging software protection. In: ACM; 2016:7. *Proceedings of the 6th Workshop on Software Security, Protection, and Reverse Engineering.*.
        
        \[112\] Ferrie P. Attacks on more virtual machine emulators. *Symantec Technology Exchange.* 2007;55.
        
        \[113\] McAfee. *McAfee Labs Threats Report.* 2016. [http://www.mcafee.com/us/resources/reports/rp-quarterly-threats-mar-2016.pdf](http://www.mcafee.com/us/resources/reports/rp-quarterly-threats-mar-2016.pdf) tech. rep.
        
        \[114\] Anati I., Gueron S., Johnson S., Scarlata V. Innovative technology for CPU based attestation and sealing. *Proceedings of the 2nd International Workshop on Hardware and Architectural Support for Security and Privacy.* 2013;vol. 13.
        
        \[115\] Dewan P., Durham D., Khosravi H., Long M., Nagabhushan G. A hypervisor-based system for protecting software runtime memory and persistent storage. In: Society for Computer Simulation International; 2008:828–835. *Proceedings of the 2008 Spring Simulation Multiconference.*.
        
        \[116\] Feng W.-C., Kaiser E., Schluessler T. Stealth measurements for cheat detection in on-line games. In: 2008:15–20. *Proceedings of the 7th ACM SIGCOMM Workshop on Network and System Support for Games.*.
        
        \[117\] Intel. *Intel Active Management Technology—Query, Restore, Upgrade, and Protect Devices Remotely (Online).* 2016. [http://www.intel.com/content/www/us/en/architecture-and-technology/intel-active-management-technology.html](http://www.intel.com/content/www/us/en/architecture-and-technology/intel-active-management-technology.html) (accessed 20.09.16).
        
        \[118\] Evenbalance. *PunkBuster—Online Countermeasures (Online).* 2015. [http://www.evenbalance.com/pbsetup.php](http://www.evenbalance.com/pbsetup.php) (accessed 20.09.16).
        
        \[119\] Valve. *Valve Anti-Cheat System (VAC) (Online).* 2015. [https://support.steampowered.com/kb\_article.php?p\_faqid=370](https://support.steampowered.com/kb_article.php?p_faqid=370) (accessed 20.09.16).
        
        \[120\] Kaiser E., Feng W.-C., Schluessler T. Fides: remote anomaly-based cheat detection using client emulation. In: New York, NY, USA: ACM; 2009:269–279. *Proceedings of the 16th ACM Conference on Computer and Communications Security.* ISBN 978-1-60558-894-0.
        
        \[121\] Hoglund G. *Hacking World of Warcraft: An Exercise in Advanced Rootkit Design.* 2006 Black Hat.
        
        \[122\] Martignoni L., Paleari R., Bruschi D. Conqueror: tamper-proof code execution on legacy systems. In: Springer; 2010:21–40. *International Conference on Detection of Intrusions and Malware, and Vulnerability Assessment.*.
        
        \[123\] Seshadri A., Luk M., Shi E., Perrig A., van Doorn L., Khosla P. Pioneer: verifying code integrity and enforcing untampered code execution on legacy systems. *ACM SIGOPS Operating Systems Review.* 2005;39(5):1–16.
        
        \[124\] Jakobsson M., Johansson K.-A. Retroactive detection of malware with applications to mobile platforms. In: Washinton, DC: USENIX Association; 2010:1–13. *Proceedings of the 5th USENIX Conference on Hot Topics in Security.*.
        
        \[125\] Chang H., Atallah M.J. Protecting software code by guards. In: Springer; 2001:160–175. *Security and Privacy in Digital Rights Management.*.
        
        \[126\] Horne B., Matheson L., Sheehan C., Tarjan R.E. Dynamic self-checking techniques for improved tamper resistance. In: Sander T., ed. *Security and Privacy in Digital Rights Management. DRM 2001.* Berlin, Heidelberg: Springer; . *Lecture Notes in Computer Science.* 2002;vol. 2320.
        
        \[127\] Chen Y., Venkatesan R., Cary M., Pang R., Sinha S., Jakubowski M.H. Oblivious hashing: a stealthy software integrity verification primitive. In: Springer; 2002:400–414. *International Workshop on Information Hiding.*.
        
        \[128\] Ibrahim A., Banescu S. StIns4CS: a state inspection tool for C. In: ACM; 2016:61–71. *Proceedings of the 2016 ACM Workshop on Software PROtection.*.
        
        \[129\] Jacob M., Jakubowski M.H., Venkatesan R. Towards integral binary execution: implementing oblivious hashing using overlapped instruction encodings. In: ACM; 2007:129–140. *Proceedings of the 9th Workshop on Multimedia & Security.*.
        
        \[130\] Goldwasser S., Rothblum G.N. On best-possible obfuscation. In: Vadhan S.P., ed. *Theory of Cryptography. TCC 2007.* Berlin, Heidelberg: Springer; . *Lecture Notes in Computer Science.* 2007;vol. 4392.
        
        \[131\] Banescu S., Ochoa M., Pretschner A., Kunze N. Benchmarking indistinguishability obfuscation—a candidate implementation. In: LNCS; 2015. *Proc. of 7th International Symposium on ESSoS.* 8978.
        
        \[132\] D. Apon, Y. Huang, J. Katz, A.J. Malozemoff, Implementing cryptographic program obfuscation. IACR Cryptology ePrint Archive, Report 2014/779, 2014.
        
        \[133\] Barak B. Hopes, fears, and software obfuscation. *Commun. ACM.* 2016;59(3):88–96.
        
        \[134\] V. Costan, S. Devadas, Intel SGX Explained. IACR Cryptology ePrint Archive, Report 2016/86, 2016.
        
        \[135\] Brasser F., Müller U., Dmitrienko A., Kostiainen K., Capkun S., Sadeghi A.-R. *Software Grand Exposure: SGX Cache Attacks are Practical.* 2017 arXiv preprint arXiv:1702.07521.
        
        \[136\] Nohl K., Evans D., Starbug S., Plötz H. Reverse-engineering a cryptographic RFID tag. *USENIX Security Symposium.* 2008;vol. 28.
        
        \[137\] Becker G.T., Fyrbiak M., Kison C. Hardware obfuscation: techniques and open challenges. In: Springer; 2017:105–123. *Foundations of Hardware IP Protection.*.
        
        \[138\] Banescu S., Collberg C., Pretschner A. Predicting the resilience of obfuscated code against symbolic execution attacks via machine learning. In: Vancouver, BC: USENIX Association; 2017. *26th USENIX Security Symposium (USENIX Security 17).*. [https://www.usenix.org/conference/usenixsecurity17/technical-sessions/presentation/banescu](https://www.usenix.org/conference/usenixsecurity17/technical-sessions/presentation/banescu).
        
        \[139\] Bos J.W., Hubain C., Michiels W., Teuwen P. Differential computation analysis: hiding your white-box designs is not enough. In: Springer; 2016:215–236. *International Conference on Cryptographic Hardware and Embedded Systems.*.
        
        \[140\] Kocher P., Jaffe J., Jun B. Differential power analysis. In: Wiener M., ed. *Advances in Cryptology—CRYPTO’ 99. CRYPTO 1999.* Berlin, Heidelberg: Springer; . *Lecture Notes in Computer Science.* 1999;vol. 1666.
        
         
        
        ![u05-01-9780128151198](images/S0065245817300499/u05-01-9780128151198.jpg)
        
        **Sebastian Banescu** is an IT Security Specialist at BMW AG in Munich, where he is involved in various projects regarding the security of the connected car against remote attackers, tuning garages, and malicious car owners. In July 2017, he received his PhD, with distinction, at the Technical University of Munich under the supervision of Prof. Alexander Pretschner. The topic of his PhD thesis was to characterize the strength of software obfuscation against automated man-at-the-end attackers. Before that, he received a MSc in Computer Science and Engineering, from Eindhoven University of Technology in the Netherlands, and a BSc in Computer Science and Engineering, from the Technical University of Cluj-Napoca in Romania.
        
        ![u05-02-9780128151198](images/S0065245817300499/u05-02-9780128151198.jpg)
        
        **Alexander Pretschner** is full professor of software and systems engineering at the Technical University of Munich, scientific director at the Fortiss Research and Technology Transfer Institute in Munich, and speaker of the board of the Munich Center for Internet Research. Research focus on all aspects of systems quality, specifically testing and security. Diploma and MS degrees in computer science from RWTH Aachen University and the University of Kansas; PhD from Technical University of Munich. Prior positions include those of a senior researcher at ETH Zurich; of a group manager at the Fraunhofer Institute for Experimental Software Engineering and of an adjunct associate professor at the Technical University of Kaiserslautern; and of a full professor at Karlsruhe Institute of Technology. Program or general (co) chair of ICST, MODELS, ESSOS, and CODASPY; associate editor of the Journal of Software Testing, Verification, and Reliability (Wiley); the Journal of Computer and System Sciences (Elsevier); and the Journal of Software Systems Modeling (Springer); former associate editor of the IEEE Transactions on Dependable and Secure Computing.
        
        * * *
        
        1.  ^([a](#S0065245817300517.xhtml#xfn0010 "label")) [https://www.w3.org/XML/](https://www.w3.org/XML/).[↩](#fnref1)
        2.  ^([a](#S0065245817300529.xhtml#xfn0010 "label")) WSBPEL available at: [https://www.oasis-open.org/committees/tc\_home.php?wgabbrev=wsbpel](https://www.oasis-open.org/committees/tc_home.php?wgabbrev=wsbpel).[↩](#fnref2)
        3.  ^([b](#S0065245817300529.xhtml#xfn0015 "label")) XML Schema description: [https://www.w3.org/XML/Schema#dev](https://www.w3.org/XML/Schema#dev).[↩](#fnref3)
        4.  ^([d](#S0065245817300529.xhtml#xfn0025 "label")) [https://www.oasis-open.org/committees/tc\_home.php?wg\_abbrev=wss](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=wss).[↩](#fnref4)
        5.  ^([e](#S0065245817300529.xhtml#xfn0030 "label")) [http://docs.oasis-open.org/xacml/3.0/xacml-3.0-core-spec-os-en.html](http://docs.oasis-open.org/xacml/3.0/xacml-3.0-core-spec-os-en.html).[↩](#fnref5)
        6.  ^([f](#S0065245817300529.xhtml#xfn0035 "label")) [http://samate.nist.gov](http://samate.nist.gov).[↩](#fnref6)
        7.  ^([g](#S0065245817300487_3.xhtml#xfn0040 "label")) A compound value of the model name and the ID of the transition in Rhapsody where the change is made prefixed with the change type (M for a modification change, A for an addition change, or D for a deletion change).[↩](#fnref7)
        
         |
        | --- |